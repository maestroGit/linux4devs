# Permisos en GNU/Linux

## Introducció als permisos

Els permisos a GNU/Linux són un mecanisme fonamental de seguretat que controla com els usuaris i grups poden interactuar amb arxius i directoris. Aquest sistema és essencial per mantenir la privacitat i la integritat del sistema operatiu.

## Tipus de permisos bàsics

A GNU/Linux existeixen tres tipus de permisos bàsics:

- **r (read/lectura)**: Permet llegir el contingut d'un arxiu o veure el contingut d'un directori.
- **w (write/escriptura)**: Permet modificar el contingut d'un arxiu o crear, eliminar i reanomenar arxius dins d'un directori.
- **x (execute/execució)**: Permet executar un arxiu com a programa o accedir al contingut d'un directori.

## Nivells d'usuari

Els permisos s'apliquen a tres nivells diferents:

- **Propietari (user/usuari)**: L'usuari que ha creat l'arxiu o directori.
- **Grup (group/grup)**: El grup al qual pertany l'arxiu o directori.
- **Altres (others/altres)**: Tots els altres usuaris del sistema.

## Visualització dels permisos

Per veure els permisos d'un arxiu o directori, podem utilitzar la comanda `ls -l`:

```bash
ls -l procesos.md
```

La sortida serà similar a aquesta:

```
-rw-r--r-- 1 Juanki usuaris 0 mai 15 18:30 procesos.md
```

El primer camp mostra els permisos:

- El primer caràcter indica el tipus d'arxiu (`-` per arxius regulars, `d` per directoris).
- Els següents tres caràcters són els permisos del propietari (`rw-`).
- Els següents tres caràcters són els permisos del grup (`r--`).
- Els últims tres caràcters són els permisos per als altres usuaris (`r--`).

## Modificació de permisos

### Ús de la comanda chmod amb notació numèrica

La comanda `chmod` permet canviar els permisos utilitzant un sistema octal:

- 4 = read (r)
- 2 = write (w)
- 1 = execute (x)

Sumem els valors per obtenir el permís desitjat:

- 7 (4+2+1) = rwx
- 6 (4+2) = rw-
- 5 (4+1) = r-x
- 4 (4) = r--
- 3 (2+1) = -wx
- 2 (2) = -w-
- 1 (1) = --x
- 0 (0) = ---

Exemple:

```bash
chmod 644 procesos.md  # Estableix rw-r--r--
```

### Ús de la comanda chmod amb notació simbòlica

També podem utilitzar notació simbòlica:

- `u` (usuari/propietari)
- `g` (grup)
- `o` (altres)
- `a` (tots)

Exemple:

```bash
chmod u+x procesos.md  # Afegeix permís d'execució al propietari
chmod g-w procesos.md  # Treu permís d'escriptura al grup
chmod o=r procesos.md  # Estableix només permís de lectura per als altres
```

## Permisos especials

A més dels permisos bàsics, existeixen permisos especials:

- **SUID (Set User ID)**: Quan s'aplica a un executable, aquest s'executa amb els permisos del propietari de l'arxiu.
- **SGID (Set Group ID)**: Quan s'aplica a un executable, aquest s'executa amb els permisos del grup de l'arxiu.
- **Sticky Bit**: Utilitzat principalment en directoris compartits, impedeix que els usuaris eliminin arxius d'altres usuaris.

Exemple:

```bash
chmod 2755 directori  # Estableix SGID en un directori
```

## Canvi de propietari i grup

Per canviar el propietari d'un arxiu o directori:

```bash
chown Juanki procesos.md
```

Per canviar el grup:

```bash
chgrp usuaris procesos.md
```

Per canviar ambdós alhora:

```bash
chown Juanki:usuaris procesos.md
```

## Permisos per defecte

El sistema utilitza la màscara `umask` per determinar els permisos per defecte dels nous arxius i directoris. Es pot modificar amb la comanda `umask`.

## Recomanacions de seguretat

- No assigneu més permisos dels necessaris (principi del mínim privilegi).
- Reviseu regularment els permisos dels arxius sensibles.
- Utilitzeu grups per gestionar els permisos de forma eficient.
- Tingueu especial cura amb els permisos d'escriptura per a "altres".

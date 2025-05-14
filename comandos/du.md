<<<<<<< HEAD
# Comandament `du`

## Introducció

El comandament `du` (Disk Usage) és una eina que permet visualitzar l'espai de disc utilitzat pels fitxers i directoris en un sistema Linux. És extremadament útil per identificar quins fitxers o directoris ocupen més espai al disc dur.

## Sintaxi bàsica

```
du [opcions] [fitxer/directori...]
```

Si no s'especifica cap fitxer o directori, `du` analitzarà el directori actual.

## Opcions principals

- `-h, --human-readable`: Mostra les mides en format llegible per humans (KB, MB, GB).
- `-s, --summarize`: Mostra només el total per a cada argument.
- `-a, --all`: Mostra la mida de tots els fitxers, no només dels directoris.
- `-c, --total`: Produeix un gran total al final de la sortida.
- `--max-depth=N`: Especifica la profunditat màxima de directoris a analitzar.
- `-x, --one-file-system`: No travessa diferents sistemes de fitxers.

## Exemples d'ús

### Visualitzar l'espai que ocupa un directori en format llegible

```bash
du -h /home/usuari/Documents
```

### Mostrar només el resum total d'un directori

```bash
du -sh /home/usuari/Documents
```

### Mostrar els 5 directoris més grans dins d'una carpeta

```bash
du -h /home/usuari | sort -rh | head -5
```

### Mostrar l'espai total utilitzat pel directori actual i els subdirectoris

```bash
du -ch .
```

### Visualitzar només el primer nivell de directoris

```bash
du -h --max-depth=1 /home/usuari
```

## Casos pràctics

- **Trobar fitxers grans**: Combinant `du` amb `sort` podem identificar ràpidament quins fitxers o directoris consumeixen més espai.
- **Neteja del sistema**: És ideal per detectar espai que es pot alliberar eliminant arxius innecessaris.
- **Monitoratge de l'espai**: Permet controlar el creixement de directoris específics.

## Notes importants

- El comando `du` calcula l'ús de disc, no la mida aparent dels fitxers. Per tant, pot mostrar valors diferents dels de l'explorador d'arxius.
- L'execució de `du` en directoris molt grans pot trigar un temps considerable.
- Cal tenir permisos suficients per llegir els fitxers i directoris que s'analitzen.
=======

La comanda `du` (de l'anglès _disk usage_) s'utilitza per estimar i mostrar l'espai de disc utilitzat per fitxers i directoris. Forma part del paquet `coreutils`.

## Sintaxi Bàsica

```bash
du [OPCIONS]... [FITXER/DIRECTORI]...
```

Si no s'especifica cap fitxer o directori, `du` mostra l'ús del disc del directori actual.

## Opcions (Flags) Comunes

- **`-h` (`--human-readable`)**: Mostra les mides en un format llegible per humans (per exemple, K per Kilobytes, M per Megabytes, G per Gigabytes).

  ```bash
  du -h /ruta/al/directori
  ```

- **`-s` (`--summarize`)**: Mostra només el total per a cada argument (directori o fitxer especificat), sense mostrar l'ús de cada subdirectori individualment.

  ```bash
  du -s /ruta/al/directori1 /ruta/al/directori2
  ```

  Combinat amb `-h`:

  ```bash
  du -sh /ruta/al/directori
  ```

- **`-c` (`--total`)**: Afegeix una línia al final amb el total general de tots els arguments processats. És especialment útil quan es llisten diversos directoris o s'utilitza amb `-s`.

  ```bash
  du -csh /ruta/directori1 /home/usuari/documents
  ```

- **`-a` (`--all`)**: Mostra l'ús del disc per a cada fitxer, a més dels directoris. Per defecte, `du` només mostra l'ús dels directoris.

  ```bash
  du -ah /ruta/al/directori
  ```

- **`--max-depth=N`**: Limita la visualització de l'ús del disc fins a una profunditat `N` de subdirectoris. `du -h --max-depth=1` és similar a `du -sh *` però gestiona millor els fitxers ocults.

  ```bash
  # Mostra l'ús del directori actual i els seus subdirectoris de primer nivell
  du -h --max-depth=1 .
  ```

- **`--exclude=PATRÓ`**: Exclou fitxers o directoris que coincideixin amb el `PATRÓ`.
  ```bash
  # Calcula l'ús del directori actual excloent el directori node_modules
  du -h --exclude="node_modules" .
  ```

## Exemples Combinats

- **Mostrar l'ús total del directori actual en format llegible:**

  ```bash
  du -sh .
  ```

- **Mostrar l'ús dels directoris del primer nivell dins del directori actual, en format llegible:**

  ```bash
  du -h --max-depth=1 .
  ```

- **Mostrar els 10 directoris que més espai ocupen dins de `/var`:**
  ```bash
  du -h --max-depth=1 /var | sort -hr | head -n 10
  ```
  _(Nota: `sort -hr` ordena numèricament en format llegible i de forma inversa)_
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

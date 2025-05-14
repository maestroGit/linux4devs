<<<<<<< HEAD
# Comanda `tail`

`tail` és una comanda en GNU/Linux que mostra les últimes línies d'un arxiu o entrada. És molt útil per visualitzar el final d'un fitxer sense necessitat de mostrar-lo sencer.

## Sintaxi bàsica

```bash
tail [OPCIONS] [ARXIU]
```

Si no s'especifica cap arxiu, `tail` llegeix de l'entrada estàndard.

## Opcions principals

- `-n N` o `--lines=N`: Mostra les últimes N línies. Per defecte són 10 línies.
- `-f` o `--follow`: Mostra les últimes línies i continua llegint l'arxiu, mostrant noves línies a mesura que s'afegeixen. Molt útil per monitoritzar logs en temps real.
- `-c N` o `--bytes=N`: Mostra els últims N bytes.
- `-q` o `--quiet`: No mostra els noms dels arxius quan se n'especifiquen diversos.
- `--retry`: Segueix intentant obrir un arxiu si no és accessible.

## Exemples

### Veure les últimes 10 línies d'un arxiu

```bash
tail /clases/linux4devs/comandos/tail.md
```

### Veure les últimes 5 línies d'un arxiu

```bash
tail -n 5 /clases/linux4devs/comandos/tail.md
```

### Monitoritzar un arxiu en temps real

```bash
tail -f /clases/linux4devs/comandos/tail.md
```

### Veure els últims 100 bytes d'un arxiu

```bash
tail -c 100 /clases/linux4devs/comandos/tail.md
```

### Veure les últimes línies de múltiples arxius

```bash
tail -n 3 /clases/linux4devs/comandos/*.md
```

## Usos comuns

- Monitoritzar arxius de registre (logs) en temps real
- Veure les últimes entrades en un arxiu de dades
- Comprovar els últims canvis en un fitxer de configuració
- Verificar els resultats més recents d'un procés que escriu a un arxiu

## Combinació amb altres comandes

La comanda `tail` es pot combinar amb altres utilitzant pipes:

```bash
cat /clases/linux4devs/comandos/tail.md | grep "exemple" | tail -n 5
```

Aquest exemple mostra les últimes 5 línies que contenen la paraula "exemple" en l'arxiu.

## Diferències amb `head`

Mentre que `head` mostra el principi (les primeres línies) d'un arxiu, `tail` mostra el final (les últimes línies). Sovint s'utilitzen juntes per inspeccionar diferents parts d'un arxiu.
=======

La comanda `tail` s'utilitza en sistemes Unix i Linux per mostrar la part final (la "cua") d'un o més fitxers. Per defecte, mostra les últimes 10 línies.

## Sintaxi Bàsica

```bash
tail [OPCIONS]... [FITXER]...
```

## Opcions Comunes

- `-n <nombre>`: Mostra les últimes `<nombre>` línies en lloc de les 10 per defecte. També es pot escriure com `-<nombre>`.
  - Exemple: `tail -n 20 fitxer.log` o `tail -20 fitxer.log` mostra les últimes 20 línies.
- `-f`: Segueix el fitxer. Mostra les últimes línies i després espera, mostrant les noves línies a mesura que s'afegeixen al fitxer. Això és molt útil per monitorar fitxers de registre (logs) en temps real. Per aturar el seguiment, prem `Ctrl+C`.
- `-c <bytes>`: Mostra els últims `<bytes>` bytes del fitxer.
- `-q`: Mode silenciós (quiet). No mostra les capçaleres amb el nom del fitxer quan es processen múltiples fitxers.
- `-v`: Mode verbós (verbose). Sempre mostra les capçaleres amb el nom del fitxer.

## Exemples

1.  **Mostrar les últimes 10 línies d'un fitxer:**

    ```bash
    tail /var/log/syslog
    ```

2.  **Mostrar les últimes 50 línies d'un fitxer:**

    ```bash
    tail -n 50 /var/log/nginx/access.log
    ```

    o

    ```bash
    tail -50 /var/log/nginx/access.log
    ```

3.  **Monitorar un fitxer de registre en temps real:**

    ```bash
    tail -f /var/log/apache2/error.log
    ```

4.  **Mostrar les últimes 10 línies de múltiples fitxers:**

    ```bash
    tail fitxer1.txt fitxer2.txt
    ```

    (Mostrarà una capçalera indicant a quin fitxer pertany cada bloc de línies).

5.  **Mostrar els últims 100 bytes d'un fitxer:**
    ```bash
    tail -c 100 dades.bin
    ```

`tail` és una eina essencial per a administradors de sistemes i desenvolupadors per revisar ràpidament el contingut final de fitxers, especialment logs.
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

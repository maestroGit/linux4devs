# tail

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

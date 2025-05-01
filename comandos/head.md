# head

## Descripció

La comanda `head` s'utilitza en sistemes operatius Unix-like per mostrar les primeres línies d'un o més fitxers de text. Per defecte, mostra les primeres 10 línies.

## Sintaxi

```bash
head [OPCIÓ]... [FITXER]...
```

Si no s'especifica cap `FITXER`, o si `FITXER` és `-`, llegeix de l'entrada estàndard.

## Opcions comunes

- `-n <num>`, `--lines=<num>`: Mostra les primeres `<num>` línies en lloc de les 10 per defecte. Si `<num>` és negatiu (`-n -<num>`), mostra totes les línies excepte les últimes `<num>`.
- `-c <num>`, `--bytes=<num>`: Mostra els primers `<num>` bytes del fitxer. Es poden utilitzar sufixos multiplicadors com `b` (512), `kB` (1000), `K` (1024), `MB` (1000*1000), `M` (1024*1024), etc.
- `-q`, `--quiet`, `--silent`: No mostra les capçaleres que indiquen el nom del fitxer quan es processen múltiples fitxers.
- `-v`, `--verbose`: Mostra sempre les capçaleres amb el nom del fitxer.

## Exemples

1.  **Mostrar les primeres 10 línies (comportament per defecte):**

    ```bash
    head nom_del_fitxer.txt
    ```

2.  **Mostrar les primeres 5 línies:**

    ```bash
    head -n 5 nom_del_fitxer.txt
    ```

    o

    ```bash
    head -5 nom_del_fitxer.txt # Forma antiga, encara suportada
    ```

3.  **Mostrar els primers 100 bytes:**

    ```bash
    head -c 100 nom_del_fitxer.txt
    ```

4.  **Mostrar les primeres 3 línies de múltiples fitxers:**

    ```bash
    head -n 3 fitxer1.txt fitxer2.txt
    ```

    (Sortida inclourà capçaleres com `==> fitxer1.txt <==`)

5.  **Utilitzar amb pipes:** Mostrar les primeres 5 entrades del directori actual.
    ```bash
    ls -l | head -n 5
    ```

`head` és útil per obtenir una vista ràpida del contingut inicial d'un fitxer sense haver d'obrir-lo completament, especialment útil amb fitxers grans.

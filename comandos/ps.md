# ps (process status)

La comanda `ps` (process status) s'utilitza per mostrar informació sobre els processos que s'estan executant actualment al sistema.

## Sintaxi bàsica

```bash
ps [opcions]
```

## Opcions comunes

Hi ha diferents estils d'opcions per a `ps` (UNIX, BSD, GNU). Les més comunes, sovint utilitzades en l'estil BSD (sense guionet), són:

- **`a`**: Mostra els processos de tots els usuaris associats a un terminal. No mostra els líders de sessió ni els processos no associats a un terminal.
- **`u`**: Mostra un format orientat a l'usuari, que inclou: `USER`, `PID`, `%CPU`, `%MEM`, `VSZ`, `RSS`, `TTY`, `STAT`, `START`, `TIME`, `COMMAND`.
- **`x`**: Mostra els processos que no estan associats a cap terminal (processos dimoni o _daemons_). Combinat amb `a`, mostra tots els processos de l'usuari.
- **`e`** (estil UNIX, amb guionet `-e`): Mostra tots els processos del sistema. Equivalent a `A` (estil BSD).
- **`f`** (estil UNIX, amb guionet `-f`): Mostra un format "complet" (`UID`, `PID`, `PPID`, `C`, `STIME`, `TTY`, `TIME`, `CMD`), sovint mostrant la jerarquia de processos.
- **`l`** (estil UNIX, amb guionet `-l`): Mostra un format llarg amb més detalls tècnics.

## Combinacions freqüents

- **`ps aux`**: Una de les combinacions més utilitzades. Mostra tots els processos (`a`+`x`) en format detallat per usuari (`u`).
  ```bash
  ps aux
  ```
- **`ps ef`**: Mostra tots els processos del sistema (`e`) en format complet (`f`), incloent la jerarquia.
  ```bash
  ps ef
  ```
- **`ps -ef`**: Equivalent a l'anterior, utilitzant la sintaxi d'opcions UNIX.

## Exemples

1.  **Veure els teus propis processos:**

    ```bash
    ps
    ```

    o amb més detall:

    ```bash
    ps u
    ```

2.  **Veure tots els processos del sistema en format detallat:**

    ```bash
    ps aux
    ```

3.  **Veure tots els processos amb la seva jerarquia:**

    ```bash
    ps -ef
    ```

    o

    ```bash
    ps axf # Estil BSD amb arbre
    ```

4.  **Filtrar processos (per exemple, buscar processos de `nginx`):**
    ```bash
    ps aux | grep nginx
    ```
    _(Nota: `grep nginx` també apareixerà com un procés en el resultat)_. Una millor manera d'evitar això:
    ```bash
    ps aux | grep '[n]ginx'
    ```
    o utilitzar `pgrep`:
    ```bash
    pgrep nginx
    ps u -p $(pgrep nginx) # Mostra info detallada dels PIDs trobats per pgrep
    ```

La comanda `ps` és molt potent i té moltes més opcions per personalitzar la sortida (seleccionar columnes, ordenar, etc.). Consulta `man ps` per a una documentació completa.

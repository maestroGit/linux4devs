<<<<<<< HEAD
# Comando PS

El comando `ps` (Process Status) s'utilitza per veure els processos que s'estan executant al sistema.

## Sintaxi
=======

La comanda `ps` (process status) s'utilitza per mostrar informació sobre els processos que s'estan executant actualment al sistema.

## Sintaxi bàsica
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

```bash
ps [opcions]
```

<<<<<<< HEAD
## Descripció

`ps` és una eina de monitoratge de processos que proporciona una instantània dels processos actuals en el sistema. Sense opcions, mostra només els processos que pertanyen a l'usuari actual i que s'han iniciat en la terminal actual.

## Opcions comunes

- `ps`: Mostra els processos de l'usuari actual a la terminal actual.
- `ps -e` o `ps -A`: Mostra tots els processos del sistema.
- `ps -f`: Mostra informació en format complet (més detallat).
- `ps -l`: Format llarg amb més informació.
- `ps aux`: Format molt detallat que mostra tots els processos de tots els usuaris.
- `ps -u usuari`: Mostra els processos d'un usuari específic.
- `ps -p PID`: Mostra informació del procés amb l'identificador PID especificat.

## Columnes de sortida

Quan s'executa `ps`, pot mostrar diverses columnes amb informació:

- `PID`: Identificador del procés.
- `TTY`: Terminal associada al procés.
- `TIME`: Temps de CPU utilitzat pel procés.
- `CMD`: Ordre que va iniciar el procés.

Amb opcions com `aux`, es mostren més columnes:

- `USER`: Usuari propietari del procés.
- `%CPU`: Percentatge d'ús de CPU.
- `%MEM`: Percentatge d'ús de memòria.
- `VSZ`: Mida de la memòria virtual.
- `RSS`: Memòria física utilitzada.
- `STAT`: Estat del procés (R=running, S=sleeping, Z=zombie, etc.).
- `START`: Hora d'inici del procés.

## Exemples

### Mostrar els processos de l'usuari actual

```bash
ps
```

### Mostrar tots els processos del sistema

```bash
ps -e
```

### Mostrar tots els processos amb informació detallada

```bash
ps aux
```

### Mostrar processos ordenats per ús de CPU

```bash
ps aux --sort=-%cpu
```

### Mostrar processos ordenats per ús de memòria

```bash
ps aux --sort=-%mem
```

### Mostrar processos d'un usuari específic

```bash
ps -u username
```

### Mostrar procés amb un PID específic

```bash
ps -p 1234
```

### Mostrar la jerarquia de processos en forma d'arbre

```bash
ps -ejH
# o
ps axjf
```

## Combinació amb altres comandes

És comú combinar `ps` amb `grep` per filtrar processos:

```bash
ps aux | grep firefox
```

També es pot utilitzar amb `less` per veure els resultats paginats:

```bash
ps aux | less
```

## Notes

- A diferència d'altres comandes Unix, `ps` accepta opcions sense el guió inicial (`-`), amb un guió (`-`) o amb dos guions (`--`), depenent del tipus d'estil que s'utilitzi (estil Unix, BSD o GNU).
- El comando `top` ofereix una alternativa a `ps` si necessites veure informació de processos que s'actualitza en temps real.
- Per matar processos identificats amb `ps`, pots utilitzar la comanda `kill` amb el PID corresponent.
=======
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
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

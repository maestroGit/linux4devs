
La comanda `sort` s'utilitza en sistemes Unix/Linux per ordenar les línies d'un fitxer de text o de l'entrada estàndard. Per defecte, ordena alfabèticament.

## Sintaxi Bàsica

```bash
sort [OPCIONS] [FITXER...]
```

- Si no es proporciona cap `FITXER`, `sort` llegeix de l'entrada estàndard.
- El resultat s'escriu a la sortida estàndard.

## Opcions Comunes

- `-n`, `--numeric-sort`: Ordena numèricament. Considera els valors numèrics de les línies.
- `-r`, `--reverse`: Inverteix l'ordre de la classificació (descendent).
- `-u`, `--unique`: Mostra només les línies úniques. Després d'ordenar, si hi ha línies idèntiques consecutives, només se'n mostra una.
- `-f`, `--ignore-case`: Ignora la diferència entre majúscules i minúscules durant l'ordenació.
- `-k POS1[,POS2]`, `--key=POS1[,POS2]`: Ordena basant-se en una clau (camp o columna) específica.
  - `POS1` indica la posició inicial de la clau (el primer camp és `1`).
  - `POS2` (opcional) indica la posició final de la clau. Si s'omet, la clau va des de `POS1` fins al final de la línia.
  - Es poden afegir modificadors a la posició, com `n` (numèric) o `r` (invers), per exemple: `-k2,2n` (ordena numèricament pel segon camp).
- `-t CHAR`, `--field-separator=CHAR`: Utilitza `CHAR` com a separador de camps per a l'opció `-k`. Per defecte, el separador és la transició entre un caràcter no blanc i un caràcter blanc.
- `-o FITXER_SORTIDA`, `--output=FITXER_SORTIDA`: Escriu el resultat a `FITXER_SORTIDA` en lloc de la sortida estàndard. És més segur que redirigir (`>`) si el fitxer de sortida és el mateix que un dels d'entrada.
- `--check` o `-c`: Comprova si el fitxer ja està ordenat. No genera sortida si ho està; altrament, informa del primer desordre i retorna un codi d'error.

## Exemples

Suposem que tenim un fitxer `dades.txt`:

```
poma
Banana
taronja
Poma
raïm
banana
10 fruites
2 fruites
```

1.  **Ordenació alfabètica simple:**

    ```bash
    sort dades.txt
    ```

    Sortida (l'ordre pot variar lleugerament segons la configuració regional, però generalment números van abans, majúscules abans que minúscules):

    ```
    10 fruites
    2 fruites
    Banana
    Poma
    banana
    poma
    raïm
    taronja
    ```

2.  **Ordenació ignorant majúscules/minúscules:**

    ```bash
    sort -f dades.txt
    ```

    Sortida:

    ```
    10 fruites
    2 fruites
    Banana
    banana
    Poma
    poma
    raïm
    taronja
    ```

3.  **Ordenació numèrica (només considera el número inicial):**

    ```bash
    sort -n dades.txt
    ```

    Sortida:

    ```
    2 fruites
    10 fruites
    Banana
    Poma
    banana
    poma
    raïm
    taronja
    ```

4.  **Ordenació inversa:**

    ```bash
    sort -r dades.txt
    ```

    Sortida:

    ```
    taronja
    raïm
    poma
    banana
    Poma
    Banana
    2 fruites
    10 fruites
    ```

5.  **Eliminar duplicats (ignorant majúscules/minúscules):**

    ```bash
    sort -fu dades.txt
    ```

    Sortida (només mostra una instància de cada línia, ignorant majúscules/minúscules):

    ```
    10 fruites
    2 fruites
    Banana
    Poma
    raïm
    taronja
    ```

6.  **Ordenar per la segona columna (separador ':') (fitxer `usuaris.txt`):**

    ```
    user1:100:Admin
    user3:50:Editor
    user2:200:Viewer
    user4:50:Guest
    ```

    Comanda (ordenar numèricament pel segon camp):

    ```bash
    sort -t: -k2,2n usuaris.txt
    ```

    Sortida:

    ```
    user3:50:Editor
    user4:50:Guest
    user1:100:Admin
    user2:200:Viewer
    ```

7.  **Ordenar primer pel segon camp (numèric) i després pel primer (alfabètic):**
    ```bash
    sort -t: -k2,2n -k1,1 usuaris.txt
    ```
    Sortida (user3 va abans que user4 perquè '3' < '4'):
    ```
    user3:50:Editor
    user4:50:Guest
    user1:100:Admin
    user2:200:Viewer
    ```

## Notes Addicionals

- `sort` pot necessitar espai temporal en disc (`/tmp` per defecte) per a fitxers molt grans que no caben a la memòria.
- L'ordre exacte pot dependre de la configuració regional (`locale`) del sistema (variable d'entorn `LC_COLLATE`). Per una ordenació consistent basada en valors de bytes, es pot establir `LC_ALL=C`.

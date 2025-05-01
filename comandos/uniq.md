# uniq

El comandament `uniq` s'utilitza per filtrar o informar sobre línies adjacents repetides en un fitxer. Normalment, rep una entrada ordenada (sovint la sortida del comandament `sort`) i, per defecte, escriu la versió filtrada a la sortida estàndard, on cada línia apareix només una vegada.

## Sintaxi

```bash
uniq [OPCIÓ]... [FITXER_ENTRADA [FITXER_SORTIDA]]
```

Si no es proporciona `FITXER_ENTRADA`, o si és `-`, llegeix de l'entrada estàndard. Si no es proporciona `FITXER_SORTIDA`, escriu a la sortida estàndard.

## Important

`uniq` només detecta línies repetides **adjacents**. Per tant, és crucial que l'entrada estigui prèviament ordenada si vols eliminar _totes_ les línies duplicades, no només les consecutives.

```bash
sort fitxer.txt | uniq
```

## Opcions Comunes

- `-c`, `--count`: Afegeix un prefix a cada línia indicant quantes vegades ha aparegut consecutivament.
- `-d`, `--repeated`: Mostra només les línies que apareixen més d'una vegada (duplicades adjacents). Es mostra una única instància per cada grup de duplicats.
- `-u`, `--unique`: Mostra només les línies que no es repeteixen (que no tenen cap línia adjacent idèntica).
- `-i`, `--ignore-case`: Ignora les diferències entre majúscules i minúscules en fer les comparacions.
- `-f N`, `--skip-fields=N`: Omet la comparació dels primers `N` camps. Un camp és una seqüència de caràcters separada per espais en blanc o tabuladors, seguida per espais en blanc.
- `-s N`, `--skip-chars=N`: Omet la comparació dels primers `N` caràcters. Si s'utilitza amb `-f`, els caràcters s'ometen _després_ dels camps omesos.
- `-w N`, `--check-chars=N`: Compara només els primers `N` caràcters de cada línia. Si s'utilitza amb `-s` o `-f`, la comparació es fa _després_ d'ometre els camps/caràcters especificats.

## Exemples

Suposem que tenim un fitxer `llista.txt` ordenat:

```
 poma
 poma
 plàtan
 taronja
 taronja
 taronja
```

1.  **Eliminar duplicats adjacents (ús bàsic):**

    ```bash
    uniq llista.txt
    ```

    Sortida:

    ```
    poma
    plàtan
    taronja
    ```

2.  **Comptar ocurrències:**

    ```bash
    uniq -c llista.txt
    ```

    Sortida:

    ```
       2 poma
       1 plàtan
       3 taronja
    ```

3.  **Mostrar només les línies duplicades:**

    ```bash
    uniq -d llista.txt
    ```

    Sortida:

    ```
    poma
    taronja
    ```

4.  **Mostrar només les línies úniques:**

    ```bash
    uniq -u llista.txt
    ```

    Sortida:

    ```
    plàtan
    ```

5.  **Combinat amb `sort` per a un fitxer no ordenat (`llista_desordenada.txt`):**
    ```
    taronja
    poma
    plàtan
    poma
    taronja
    taronja
    ```
    ```bash
    sort llista_desordenada.txt | uniq -c
    ```
    Sortida:
    ```
       1 plàtan
       2 poma
       3 taronja
    ```

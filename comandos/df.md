<<<<<<< HEAD
# df - Mostra l'espai disponible al disc

## Descripció

El comandament `df` (disk free) ens permet veure quant espai lliure i ocupat hi ha als discs i sistemes d'arxius del nostre ordinador.

## Sintaxi bàsica

```bash
df [opcions] [sistema_arxius]
```

## Exemples d'ús

### Veure l'espai en format llegible
=======

La comanda `df` (disk free) s'utilitza per mostrar l'espai de disc utilitzat i disponible als sistemes de fitxers del sistema operatiu Linux.

## Ús bàsic

```bash
df
```

Aquesta comanda mostrarà l'ús de l'espai per a tots els sistemes de fitxers muntats, normalment en blocs d'1K per defecte.

## Opcions (Flags) comunes

- `-h` (`--human-readable`): Mostra les mides en un format llegible per humans (per exemple, 1K, 234M, 2G). Utilitza potències de 1024.
- `-H` (`--si`): Similar a `-h`, però utilitza potències de 1000 (SI). Per exemple, 1.1K, 245M, 2.2G.
- `-T` (`--print-type`): Mostra el tipus de sistema de fitxers per a cada entrada (per exemple, ext4, tmpfs, nfs).
- `-i` (`--inodes`): Mostra informació sobre l'ús dels inodes en lloc de l'ús dels blocs. Això és útil per diagnosticar problemes on s'han esgotat els inodes abans que l'espai en disc.
- `-a` (`--all`): Inclou sistemes de fitxers pseudo, duplicats o inaccessibles a la sortida. Per defecte, aquests s'ometen.
- `--total`: Mostra una fila addicional al final amb el total de totes les mètriques (mida, utilitzat, disponible).
- `[FITXER]`: Si s'especifica un fitxer o directori, `df` mostrarà la informació del sistema de fitxers on resideix aquest fitxer o directori.

## Exemples

**Mostrar l'ús del disc en format llegible:**
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

```bash
df -h
```

<<<<<<< HEAD
Aquest és l'ús més comú. L'opció `-h` mostra les mides en format llegible (GB, MB, etc.)

### Veure només un disc específic
=======
**Mostrar l'ús del disc incloent el tipus de sistema de fitxers:**

```bash
df -hT
```

**Mostrar l'ús dels inodes:**

```bash
df -i
```

**Mostrar l'ús del disc per al sistema de fitxers que conté el directori `/home`:**
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

```bash
df -h /home
```

<<<<<<< HEAD
Mostra l'espai només pel directori /home

## Opcions principals

- `-h`: Mostra les mides en format humà (GB, MB, KB)
- `-T`: Mostra el tipus de sistema d'arxius
- `-i`: Mostra informació sobre els inodes
- `-a`: Mostra tots els sistemes d'arxius

## Sortida explicada

Quan executem `df -h`, veurem una taula amb aquesta informació:

- **S.fitxers**: El nom del sistema d'arxius
- **Mida**: Mida total del disc
- **Usats**: Espai utilitzat
- **Disp**: Espai disponible
- **% Ús**: Percentatge d'ús
- **Muntat a**: Punt de muntatge

## Consells pràctics

- Utilitzeu sempre l'opció `-h` per veure les mides de forma comprensible
- Reviseu periòdicament l'espai disponible per evitar problemes
- Si un disc està més del 90% ple, considereu netejar arxius innecessaris
=======
**Mostrar l'ús del disc amb un total:**

```bash
df -h --total
```
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

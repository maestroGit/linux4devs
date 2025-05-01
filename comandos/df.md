# df (diskfree)

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

```bash
df -h
```

**Mostrar l'ús del disc incloent el tipus de sistema de fitxers:**

```bash
df -hT
```

**Mostrar l'ús dels inodes:**

```bash
df -i
```

**Mostrar l'ús del disc per al sistema de fitxers que conté el directori `/home`:**

```bash
df -h /home
```

**Mostrar l'ús del disc amb un total:**

```bash
df -h --total
```

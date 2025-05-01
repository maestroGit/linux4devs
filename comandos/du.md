# du (Disk Usage)

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

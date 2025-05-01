# Gestió de Paquets a Debian/Ubuntu: `apt` i `dpkg`

Linux, i en particular les distribucions basades en Debian com Ubuntu, utilitzen un sistema de gestió de paquets per instal·lar, actualitzar i eliminar programari. Els dos comandaments principals per a aquesta tasca són `dpkg` i `apt`.

## `dpkg` (Debian Package)

`dpkg` és l'eina de baix nivell que gestiona els paquets individuals amb extensió `.deb`. És el fonament del sistema de paquets de Debian.

- **Funció principal:** Instal·lar, eliminar i obtenir informació sobre fitxers `.deb` que ja tens descarregats al teu sistema.
- **Limitació:** `dpkg` no resol automàticament les **dependències**. Si un paquet necessita un altre paquet per funcionar, `dpkg` no el descarregarà ni l'instal·larà per tu.

### Comandaments bàsics de `dpkg`:

- **Instal·lar un paquet `.deb` descarregat:**
  ```bash
  sudo dpkg -i /ruta/al/paquet.deb
  ```
  (Pot fallar si falten dependències).
- **Eliminar un paquet (conservant els fitxers de configuració):**
  ```bash
  sudo dpkg -r nom_del_paquet
  ```
- **Purgar un paquet (eliminant també els fitxers de configuració):**
  ```bash
  sudo dpkg -P nom_del_paquet
  ```
- **Llistar els paquets instal·lats (pot ser una llista llarga):**
  ```bash
  dpkg -l
  ```
- **Comprovar si un paquet està instal·lat i veure'n la versió:**
  ```bash
  dpkg -s nom_del_paquet
  ```

## `apt` (Advanced Package Tool)

`apt` és una eina de més alt nivell, més potent i fàcil d'utilitzar per a la majoria de tasques diàries. Treballa amb **repositoris** (servidors en línia que contenen milers de paquets) i gestiona automàticament les dependències. És l'eina recomanada per a usuaris novells i experimentats.

- **Funció principal:** Cercar, instal·lar, actualitzar i eliminar programari des dels repositoris configurats al sistema. Gestiona les dependències automàticament.
- **Avantatge:** Simplifica enormement la gestió del programari. Si vols instal·lar un programa, `apt` s'encarrega de descarregar-lo ell i tot el que necessiti per funcionar.

_(Nota: Abans existien `apt-get` i `apt-cache`. El comandament `apt` modern combina les funcions més comunes d'ambdós d'una manera més amigable)._

### Comandaments bàsics d'`apt`:

- **Actualitzar la llista de paquets disponibles des dels repositoris:** (Important fer-ho abans d'instal·lar o actualitzar paquets).
  ```bash
  sudo apt update
  ```
  - `sudo`: Executa el comandament com a superusuari (administrador), ja que modificar el programari del sistema requereix permisos especials. Et demanarà la teva contrasenya.
- **Actualitzar tots els paquets instal·lats a la seva versió més recent:**
  ```bash
  sudo apt upgrade
  ```
- **Instal·lar un nou paquet des dels repositoris:**
  ```bash
  sudo apt install nom_del_paquet
  ```
  (Exemple: `sudo apt install gimp` per instal·lar el programa d'edició d'imatges GIMP).
- **Eliminar un paquet (conservant els fitxers de configuració):**
  ```bash
  sudo apt remove nom_del_paquet
  ```
- **Purgar un paquet (eliminant també els fitxers de configuració):**
  ```bash
  sudo apt purge nom_del_paquet
  ```
- **Eliminar paquets que es van instal·lar automàticament com a dependències i ja no són necessaris:**
  ```bash
  sudo apt autoremove
  ```
- **Cercar un paquet als repositoris:**
  ```bash
  apt search terme_de_cerca
  ```
- **Mostrar informació detallada sobre un paquet:**
  ```bash
  apt show nom_del_paquet
  ```
- **Si una instal·lació amb `dpkg -i` ha fallat per dependències, pots intentar arreglar-ho amb:**
  ```bash
  sudo apt --fix-broken install
  ```

## Quan utilitzar cada un?

- **Per al dia a dia (instal·lar, actualitzar, eliminar programari):** Utilitza **`apt`**. És més fàcil, gestiona dependències i treballa amb repositoris.
- **Quan has descarregat manualment un fitxer `.deb`:** Utilitza **`dpkg -i`** per instal·lar-lo. Si et dona errors de dependències, executa `sudo apt --fix-broken install` després.
- **Per consultes específiques sobre paquets ja instal·lats o fitxers `.deb` concrets:** `dpkg` pot ser útil (`dpkg -s`, `dpkg -L` per veure els fitxers d'un paquet, etc.).

En resum, `apt` és el teu amic per a la gestió general del programari a Debian/Ubuntu, mentre que `dpkg` és l'eina subjacent que `apt` utilitza, i que pots fer servir directament en casos específics com instal·lar un `.deb` local.

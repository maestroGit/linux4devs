<<<<<<< HEAD
# Comanda `mount`

La comanda `mount` s'utilitza per muntar sistemes de fitxers. Muntar significa fer accessible un sistema de fitxers a través d'un directori específic (punt de muntatge) dins de l'estructura de directoris del sistema.

## Sintaxi bàsica
=======
## Què és `mount`?

`mount` és una ordre bàsica de GNU/Linux que permet connectar (o "muntar") sistemes de fitxers al sistema de fitxers principal. Això fa que els continguts del dispositiu muntat siguin accessibles a través d'un directori específic, conegut com a "punt de muntatge".

## Sintaxi Bàsica
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

```bash
mount [opcions] dispositiu punt_de_muntatge
```

<<<<<<< HEAD
## Opcions comunes

- `-t tipus`: Especifica el tipus de sistema de fitxers (ext4, ntfs, vfat, etc.)
- `-o opcions`: Especifica opcions de muntatge addicionals
- `-a`: Munta tots els sistemes de fitxers definits al fitxer `/etc/fstab`
- `-r`: Munta el sistema de fitxers en mode només lectura
- `-w`: Munta el sistema de fitxers en mode lectura/escriptura (predeterminat)
- `-v`: Mode detallat (verbose)
- `-h`: Mostra l'ajuda

## Exemples d'ús

### Mostrar tots els sistemes de fitxers muntats
=======
On:

- **dispositiu**: el dispositiu o sistema de fitxers a muntar (ex: `/dev/sdb1`, una partició del disc)
- **punt_de_muntatge**: el directori on es farà accessible el dispositiu (ex: `/mnt/usb`)

## Opcions Comunes

- `-t tipus`: Especifica el tipus de sistema de fitxers (ext4, ntfs, vfat, etc.)
- `-o opcions`: Opcions de muntatge específiques
- `-a`: Munta tots els sistemes de fitxers definits a `/etc/fstab`
- `-r`: Munta el sistema de fitxers en mode només lectura
- `-w`: Munta el sistema de fitxers en mode lectura-escriptura (per defecte)
- `-v`: Mode detallat (verbose), mostra més informació
- `-L etiqueta`: Munta el dispositiu amb una etiqueta específica
- `-U uuid`: Munta el dispositiu amb un UUID específic

## Exemples Pràctics

### Muntar un dispositiu USB

```bash
# Crear un punt de muntatge
sudo mkdir -p /mnt/usb

# Muntar el dispositiu USB
sudo mount /dev/sdb1 /mnt/usb

# Muntar especificant el sistema de fitxers
sudo mount -t vfat /dev/sdb1 /mnt/usb
```

### Muntar una partició NTFS amb opcions específiques

```bash
sudo mount -t ntfs-3g -o rw,uid=1000,gid=1000,umask=022 /dev/sda2 /mnt/windows
```

Això munta la partició amb permisos de lectura/escriptura per a l'usuari amb UID 1000.

### Muntar una imatge ISO

```bash
sudo mount -t iso9660 -o loop imatge.iso /mnt/iso
```

### Muntar un recurs de xarxa (NFS)

```bash
sudo mount -t nfs servidor:/compartit /mnt/xarxa
```

### Muntar un sistema de fitxers temporalment amb opcions

```bash
sudo mount -t ext4 -o noatime,nodiratime /dev/sdc1 /mnt/disc_extern
```

## Fitxer `/etc/fstab`

El fitxer `/etc/fstab` permet definir muntatges permanents que s'activaran durant l'arrencada del sistema. Estructura bàsica:

```
dispositiu   punt_muntatge   tipus_sistema_fitxers   opcions   dump   fsck
```

Exemple:

```
/dev/sda1    /               ext4    defaults        0       1
/dev/sda2    /home           ext4    defaults        0       2
UUID=1234-5678  /media/dades  ext4    defaults,noatime  0    2
```

## Desmuntar Sistemes de Fitxers

Per desmuntar un sistema de fitxers s'utilitza el comandament `umount`:

```bash
sudo umount /punt_de_muntatge
```

o

```bash
sudo umount /dev/dispositiu
```

## Mostrar els Sistemes de Fitxers Muntats

Per veure tots els sistemes de fitxers muntats:
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

```bash
mount
```

<<<<<<< HEAD
### Muntar una unitat USB

```bash
sudo mount /dev/sdb1 /mnt/usb
```

### Muntar una imatge ISO

```bash
sudo mount -o loop imatge.iso /mnt/cdrom
```

### Muntar una partició NTFS amb suport complet

```bash
sudo mount -t ntfs-3g /dev/sda1 /mnt/windows
```

### Muntar amb opcions específiques

```bash
sudo mount -o remount,rw /
```

## Desmuntar sistemes de fitxers

Per desmuntar un sistema de fitxers, s'utilitza la comanda `umount`:

```bash
sudo umount /mnt/usb
```

## El fitxer `/etc/fstab`

Aquest fitxer conté informació sobre els sistemes de fitxers que s'han de muntar automàticament en iniciar el sistema. Cada línia representa un sistema de fitxers amb els següents camps:

```
dispositiu    punt_muntatge    tipus_sistema_fitxers    opcions    dump    pass
```

## Consideracions importants

- Cal tenir permisos d'administrador (sudo) per muntar la majoria de dispositius
- No es pot desmuntar un sistema de fitxers que està en ús
- Els sistemes de fitxers removibles (com USB) es munten automàticament en la majoria de distribucions modernes

## Consells per a principiants

- Abans de desconnectar qualsevol dispositiu, assegureu-vos de desmuntar-lo correctament amb `umount`
- Per veure quins dispositius estan disponibles per muntar, podeu utilitzar `lsblk` o `fdisk -l`
- Si rebeu errors de permisos, probablement necessitareu utilitzar `sudo`
=======
O de manera més llegible:

```bash
mount | column -t
```

Alternativament:

```bash
df -h
```

## Muntar sistemes de fitxers específics

### Muntar una partició SAMBA/CIFS (Windows)

```bash
sudo mount -t cifs -o username=usuari,password=contrasenya //servidor/compartit /mnt/win_compartit
```

### Muntar un sistema de fitxers encriptat (LUKS)

```bash
# Desbloquejar el volum encriptat
sudo cryptsetup luksOpen /dev/sdb1 volum_encriptat

# Muntar el volum desbloquejat
sudo mount /dev/mapper/volum_encriptat /mnt/segur
```

### Muntar un dispositiu per UUID

```bash
# Trobar l'UUID
sudo blkid

# Muntar per UUID
sudo mount UUID=1234-5678-90ab-cdef /mnt/disc
```

## Consells i Bones Pràctiques

1. **Utilitzar UUIDs**: Són més fiables que els noms de dispositiu, ja que aquests poden canviar.
2. **Crear directoris de muntatge dedicats**: Utilitza `/mnt/` o `/media/` per als punts de muntatge.
3. **Verificar l'espai abans de desmuntar**: Utilitza `lsof` o `fuser` per comprovar si hi ha fitxers oberts abans de desmuntar.
4. **Opcions de rendiment**: Considera utilitzar opcions com `noatime` per millorar el rendiment.

## Solució de Problemes

- Si el muntatge falla amb un error "already mounted", comprova amb `mount | grep dispositiu`.
- Si no pots desmuntar, utilitza `lsof +D /punt_de_muntatge` per trobar processos que utilitzen el sistema de fitxers.
- Si necessites forçar un desmuntatge (no recomanat excepte en emergències): `umount -f /punt_de_muntatge`.
>>>>>>> f6912d2109c243dc630c7a950e9ca120a0c5f243

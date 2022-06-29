---
title: 💽 LVM
banner_icon: 💽
---

## Prerequisitos
Tener aptitude
```
apt-get install aptitude
```
Tener un segundo disco
## Instalar lvm
```
aptitude install lvm2
```
```
dpkg-query -s lvm2
```
## Crear LVM
Crear un physical volume
```
pvcreate /dev/sdb
```
```
pvs
```
Crear un volume group
```
vgcreate grupo /dev/sdb
vgs
```
Ver ambos
```
pvdisplay
vgdisplay
```
Crear logic volumen, en este caso de 10Gb y de nombre music, en el volume group grupo
```
lvcreate -L 10G -n music grupo
```
```
lvs
```
Darle formato ext4
```
mkfs.ext4 /dev/grupo/music
```
Crear un directorio en el /mnt/
```
mkdir /mnt/lvm
```
montar el disco
```
mount /dev/grupo/music /mnt/lvm/
```

### Extend
Agregar el /dev/sdc a grupo
```
vgextend grupo /dev/sdc
```
Agregar a /dev/grupo/music 5Gb
```
lvextend -L+5G /dev/grupo/music
```
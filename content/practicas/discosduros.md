---
title: 💾 Alias
banner_icon: 💾
---

## Prerequisitos
Tener un disco duro aparte del de el sistema, se pueden añadir en configuracion

## Añadir discos
Para ver los discos que hay
```
lsblk
```
o
```
fdisk -l
```
añadir al sdb una particion
```
fdisk /dev/sdb
```
dentro de la consola fdisk
poner n para agregar particion
```
n
```
luego, p para primaria y e para extendida
```
p
```
o
```
e
```
luego enter por default se pondra el numero de particion
de nuevo enter para el promer sector esta por default

Poner cuanto de memoria se necesita, ejemplo 5GB
```
+5GB
```

finalmente guardar y salir
```
wq
```

Darle formato a la particion
```
mkfs.ext4 /dev/sdb1
```
hacer un directorio en /mnt/discob1
```
mkdir /mnt/discob1
```
montar el disco
```
mount /dev/sdb1/ /mnt/discob1
```
Si se quiere montarlo cada vez que se inicia la maquina añadirlo en el fstab
```
vim /etc/fstab
```
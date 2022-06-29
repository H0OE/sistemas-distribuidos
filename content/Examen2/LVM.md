---
title: 🪴 LVM
---

Sistema de administración de una colección de unidades de almacenamiento, divididas lógicamente para su fácil uso y extensión.
    
-   Permite realizar operaciones en caliente (mover discos, expandir, tomar snapshots) sin tener que parar el sistema.
    
-   Puede ser más complicada de setup y se puede perder toda la información si una unidad falla

![Caracteristicas](/sistemas-distribuidos/Examen2/images/lvm.png)
## Physical Volume PV 
Es cualquier dispositivo físico que pueda almacenar datos. De estos dispositivos parte el LVM
    
## Volume Group 
Es un grupo de PV’s

## Logical Volume 
La división lógica de todo el VG. (Si se tiene 2 discos de 1 Gb cada uno en un VG, podemos asignar el uso de 1.5Gb en total de todo el VG)

## Cuando usar
La primera cosa que debe considerar antes de la creación de LVM es lo que se quiere lograr con sus discos y particiones. Algunas distribuciones, como Fedora, se instala LVM por defecto.
Si usted está utilizando otra distribución en una portátil con un solo disco duro interno y no necesita las características extendidas como snapshots en vivo, entonces puede que no necesite LVM. Si usted necesita una fácil expansión o desea combinar varios discos duros en un únicamente grupo de almacenamiento, LVM puede ser lo que usted ha estado buscando.

## Desventajas
La configuración inicial de LVM es más compleja que simplemente particiones un disco, y definitivamente necesitará comprender la terminología y el modelo de LVM (volúmenes lógicos, volúmenes físicos, grupos de volúmenes) antes de poder comience usándolo. (Sin embargo, una vez que está configurado, emplearlo es mucho más fácil).

Además, si usa LVM en discos duros, puede perder todos sus datos cuando falla una sola unidad.

![Caracteristicas](/sistemas-distribuidos/Examen2/images/lvm2.jpg)
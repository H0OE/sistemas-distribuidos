---
title: 🪴 LVM
---

Sistema de administración de una colección de unidades de almacenamiento, divididas lógicamente para su fácil uso y extensión.
    
-   Permite realizar operaciones en caliente (mover discos, expandir, tomar snapshots) sin tener que parar el sistema.
    
-   Puede ser más complicada de setup y se puede perder toda la información si una unidad falla
    
## Physical Volume PV 
Es cualquier dispositivo físico que pueda almacenar datos. De estos dispositivos parte el LVM
    
## Volume Group 
Es un grupo de PV’s

## Logical Volume 
La división lógica de todo el VG. (Si se tiene 2 discos de 1 Gb cada uno en un VG, podemos asignar el uso de 1.5Gb en total de todo el VG)

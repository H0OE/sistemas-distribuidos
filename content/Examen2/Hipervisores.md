---
title: 🪴 Hipervisores
---
![Caracteristicas](/sistemas-distribuidos/Examen2/images/hip.jpg)
Software que permite la virtualización

-   Tipo 1: se instala directamente y corre en el hardware
    
-   Tipo 2: corre a partir de un sistema operativo
## Tipo 1
Un hipervisor simple (Tipo 1) es una capa de software que instalamos directamente sobre un servidor físico y su hardware subyacente.

No hay software ni ningún sistema operativo en el medio, de ahí el nombre de «hipervisor simple». Por esta razón, los hipervisores de tipo 1 demostraron proporcionar un rendimiento y una estabilidad excelentes, ya que no se ejecutan dentro de Windows u otros sistemas operativos.

Los hipervisores tipo 1 son un sistema operativo en sí mismo, uno muy básico sobre el que se ejecutan máquinas virtuales. Esto significa que la máquina física en la que se ejecuta el hipervisor sirve solo para propósitos de virtualización. No podrás utilizarlo para nada más.
Por lo tanto, encontramos principalmente hipervisores de tipo 1 en entornos empresariales.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/hip1.png)

## Tipo 2
Este tipo de hipervisor se ejecuta dentro de un sistema operativo de una máquina host física.

Es por esto que llamamos hipervisores alojados de hipervisores de tipo 2. A diferencia de los hipervisores de tipo 1 que se ejecutan directamente en el hardware, los hipervisores alojados tienen una capa de software debajo. Lo que tenemos en este caso es:
- Una máquina física.
- Un sistema operativo instalado en el hardware (Windows, Linux, MacOS).
- Un software de hipervisor de tipo 2 dentro de ese sistema operativo.
- Las instancias reales de máquinas virtuales invitadas.
- Los hipervisores de tipo 2 generalmente se encuentran en entornos con una pequeña cantidad de servidores.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/hip2.png)

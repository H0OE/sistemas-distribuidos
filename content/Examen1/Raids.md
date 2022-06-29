---
title:   🖥🤯 RAID
banner_icon: 🖥
---
## HDD vs SSD
![Caracteristicas](/sistemas-distribuidos/Examen1/images/hhdssd.jpg)
### HDD
Los discos duros, también conocidos como HDD, son un componente informático que sirve para almacenar de forma permanente tus datos. Esto quiere decir, que los datos no se borran cuando se apaga la unidad como pasa en los almacenados por la memoria RAM. La primera empresa en comercializarlos fue IBM en 1956. 

Están compuestos de piezas mecánicas, de ahí que a veces se le llame discos duros mecánicos, y utilizan el magnetismo para grabar tus datos y archivos. Se compone de uno o varios discos rígidos unidos por un mismo eje y que giran a gran velocidad dentro de una caja metálica. En cada plato y en cada una de sus caras, un cabezal de lectura/escritura lee o graba tus datos sobre los discos

### SSD
Las unidades de estado sólido o SSD (Solid State Drive) son una alternativa a los discos duros. La gran diferencia es que mientras los discos duros utilizan componentes mecánicos que se mueven, las SSD almacenan los archivos en microchips con memorias flash interconectadas entre sí. Por lo tanto, casi podríamos considerarlos como una evolución de las memorias USB. 

Los SSD suelen utilizar memorias flash basadas en NAND, que como también son no-volátiles mantienen la información almacenada cuando el disco se desconecta. No tienen cabezales físicos para grabar los datos, en su lugar incluyen un procesador integrado para realizar operaciones relacionadas con la lectura y escritura de datos.


## Raid
RAID es la sigla para " Redundant Array of Independent Disks ". Su definición en español sería "Matriz Redundante de Discos Independientes ". Se trata de una tecnología que combina varios discos rígidos (HD) para formar una única unidad lógica, donde los mismos datos son almacenados en todos los discos (redundancia). 

La tecnología RAID protege los datos contra el fallo de una unidad de disco duro. Si se produce un fallo, RAID mantiene el servidor activo y en funcionamiento hasta que se sustituya la unidad defectuosa. 

La tecnología RAID se utiliza también con mucha frecuencia para mejorar el rendimiento de servidores y estaciones de trabajo. Estos dos objetivos, protección de datos y mejora del rendimiento, no se excluyen entre sí.

### Raid 0
![Caracteristicas](/sistemas-distribuidos/Examen1/images/raid0.jpg)
No ofrece tolerancia a fallos, pero si mayor velocidad, algunos no consideran a esta configuración como un RAID verdadero. Una configuración RAID 0 con dos discos es hasta dos veces más rápidas que un solo disco duro. **Se utiliza en entornos de laboratorio para medir las entradas y salidas de un sistema por su rapidez.**

### Raid 1
También conocido como "Mirroring " o " Espejado ", el RAID 1 funciona añadiendo discos rígidos paralelos a los discos rígidos principales existentes en la computadora. De esta manera, si, por ejemplo, una computadora posee 2 discos, se puede anexar un disco rígido para cada uno, totalizando 4. **Los discos que fueron añadidos, trabajan como una copia del primero. **

La consecuencia en este caso, es que la grabación de datos es más lenta, pues es realizada dos veces. Sin embargo, la lectura de esa información es más rápida, pues puede ser accedida de dos fuentes. **Se utiliza para el Sistema Operativo, debido a que es una copia tal cual, en caso de un fallo del mismo, es más lento.**
![Caracteristicas](/sistemas-distribuidos/Examen1/images/raid1.png)

### Raid 5
Este RAID ofrece tolerancia al fallo, pero además optimiza la capacidad del sistema permitiendo una utilización de hasta el 80% de la capacidad del conjunto de discos. Esto lo consigue mediante el cálculo de la información de paridad y su almacenamiento alternativo por bloques en todos lo discos del conjunto. La información del usuario se graba por bloques y de forma alternativa en todos ellos. Uso mínimo de 3 discos. En resumen, el RAID 5 es un buen sistema integral que combina almacenamiento eficiente con excelente seguridad y rendimiento. **Es ideal para servidores de archivos y aplicaciones que tienen un número limitado de unidades de datos.**
![Caracteristicas](/sistemas-distribuidos/Examen1/images/raid5.png)

### Raid 6
**Acceso independiente con doble paridad**
Similar al RAID 5, pero incluye un segundo esquema de paridad distribuido por los distintos discos y por tanto ofrece tolerancia extremadamente alta a los fallos y a las caídas de disco, ofreciendo dos niveles de redundancia. 

Si fallan más de dos unidades de disco, los datos se tienen que restaurar a partir del medio de copia de seguridad. Lógicamente, la capacidad de dos unidades de disco está dedicada a almacenar datos de paridad en un conjunto de paridad. No obstante, en la práctica, los datos de paridad se reparten entre varias unidades de disco. 

El número mínimo de unidades de disco en un conjunto de paridad es de 4. El número máximo de unidades de disco en un conjunto de paridad es de 18. RAID 6 permite almacenar grandes cantidades de datos a prueba de fallos a largo plazo al amortiguar dos posibles fallos. **Por tanto, los sistemas de servidores en los que se archivan datos son un caso de aplicación ideal.**
![Caracteristicas](/sistemas-distribuidos/Examen1/images/raid6.png)
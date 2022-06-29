---
title: ⌚ Relojes
banner_icon: ⌚
---
![Caracteristicas](/sistemas-distribuidos/Examen2/images/rel.jpg)
Existen 2 tipos de relojes:
- Relojes Físicos
Aquellos que están directamente relacionados con el tiempo real y la concepción que tenemos de este.

- Relojes Lógico
Aquellos que tienen como importancia el orden de los eventos.

Las computadoras tienen por lo general un reloj físico de cuarzo que basa su medición de tiempo en las oscilaciones del cristal. 

Las oscilaciones de los cristales pueden ser de diferentes velocidades lo que generaría un sesgo de reloj, lo que quiere decir que los relojes de 2 dispositivos se encuentran desincronizados. 

Para evitar que los relojes dentro de un sistema se encuentren desincronizados, es necesario implementar algoritmos o protocolos de sincronización. 

## Distorsion de reloj
La diferencia entre los valores del tiempo se llama **distorsión del reloj**.

Como consecuencia de esta distorsión, podrían fallar los programas que esperan que 
el tiempo asociado a un archivo, objeto, proceso o mcnsaje sea correcto e independiente del sitio donde haya sido generado (es decir, del reloj utilizado).
![Caracteristicas](/sistemas-distribuidos/Examen2/images/dist.png)
## Categoria de algoritmos
Dentro de los algoritmos podemos definir 4 categorías:
- Internos: La sincronización sucede dentro de la red.
- Externos: Se hace la petición de la hora a un servidor externo confiable.
- Pasivos: Los nodos piden la hora.
- Activos: El servidor o el maestro de la hora pregunta por las horas de los demás y envía instrucciones.

## Algoritmos
### Algoritmo de Christian
Este algoritmo propone tener un servidor externo UTC al que los nodos del sistema preguntarán la hora para poder sincronizar los relojes.

![Caracteristicas](/sistemas-distribuidos/Examen2/images/cris.png)
Hay que tomar ciertas consideraciones en cuenta al momento de usar este algoritmo:
#### Ventajas
- Los relojes no deben retroceder para evitar errores
- La sincronización requiere del intercambio de mensajes, pero el tránsito de estos consume tiempo.
- El tiempo del receptor UTC no puede ser menor que el tiempo de la máquina que le solicitó el tiempo.
- El servidor de UTC debe procesar las solicitudes de tiempo con el concepto de interrupciones, lo cual incide en el tiempo de atención.
- El intervalo de transmisión de la solicitud y su respuesta debe ser tomado en cuenta para la sincronización.
- El tiempo de propagación se suma al tiempo del servidor para sincronizar al emisor cuando éste recibe la respuesta.
##### Inconvenientes
- El problema que se presenta es la posibilidad de fallo debido a la existencia de un único servidor. Cristian sugiere múltiples servidores de tiempo sincronizados que suministren el tiempo. El cliente envía un mensaje de petición a todos los servidores y toma la primera respuesta recibida.
- El algoritmo no contempla problemas de malfuncionamiento o fraude por parte del servidor.
- La capacidad de cada nodo para leer el valor del reloj de otro nodo puede generar errores debido al retraso en la comunicación de mensajes entre nodos. La demora se puede calcular tomando en cuenta el tiempo necesario para preparar, transmitir y recibir un mensaje vacío en ausencia de errores de transmisión y carga del sistema.
### Algoritmo de Berkeley 
Este algoritmo se propone en situaciones en las que no se cuenta con un servidor UTC confiable. La idea es que dentro de las computadoras de una red, se selecciona una que sea maestra y las demás serán esclavas. Esta computadora maestra, se encargará de preguntarle a las demás las horas que están manejando, para poder sacar un promedio y mandar instrucciones para el retraso o adelanto de relojes dependiendo la situación de cada computadora. 

![Caracteristicas](/sistemas-distribuidos/Examen2/images/berk.jpg)

En este algoritmo no es importante tener en cuenta el delay entre el envío y respuesta del mensaje debido a que solo necesitamos hallar un promedio para la sincronización, más no la hora exacta. En caso de que el maestro muera, se busca uno nuevo, y si un nodo falla, simplemente no se toma en cuenta. 
##### Inconvenientes
- En caso de que el maestro falle, dejará de preguntar la hora y, en consecuencia, se perderá la sincronización.
- En el paso de mensajes entre maestro y esclavos y viceversa se ha de tener en cuenta el retraso que genera el propio envío de los mensajes, por lo que tendremos errores a la hora de sincronizar.
- Otro de los problemas de ser un algoritmo centralizado será el de tener que elegir un nuevo maestro debido a que se puedan producir fallos en el tratamiento de los datos para llevar a cabo la sincronización, buscando un maestro que cometa menor cantidad de fallos y el sistema se mantenga en correcto funcionamiento.
- La demora introducida por los equipos de conmutación, se agrava en los casos en los que el equipo cumple otras funciones, además de conmutar paquetes, como es el caso de un PC que, además de actuar como conmutador, atiende otras tareas, con lo cual, la misma tarea de conmutar puede insumir diferentes tiempos.
## NTP
Finalmente nos encontramos con el protocolo NTP para la sincronización de relojes mediante internet. Este protocolo funciona en la capa 4 de red, **con el protocolo UDP y en el puerto 123.**

![Caracteristicas](/sistemas-distribuidos/Examen2/images/ntp.png)

### Funcionamiento
El cliente NTP inicia un intercambio de solicitud de tiempo con el servidor NTP. Luego, el cliente puede calcular el retraso del enlace y su compensación local y ajustar su reloj local para que coincida con el reloj de la computadora del servidor.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/ntp-3.jpg)
**La versión actual es la NTP v4**

Como regla general, se requieren seis intercambios durante un período de aproximadamente cinco a 10 minutos para configurar inicialmente el reloj.

Una vez sincronizado, el cliente actualiza el reloj aproximadamente una vez cada 10 minutos, lo que generalmente requiere solo un único intercambio de mensajes, además de la sincronización cliente-servidor. Esta transacción ocurre a través del Protocolo de datagramas de usuario (UDP) en el **puerto 123** NTP también admite la sincronización de transmisión de los relojes de la computadora del mismo nivel.

Hay miles de servidores NTP en todo el mundo. Tienen acceso a relojes atómicos de alta precisión y relojes del Sistema de Posicionamiento Global. Se requieren receptores especializados para comunicarse directamente con los servidores NTP para estos servicios de tiempo. 

No es práctico ni rentable equipar cada computadora con uno de estos receptores. En cambio, las computadoras designadas como servidores de tiempo principales están equipadas con los receptores. Utilizan protocolos como NTP para sincronizar las horas de reloj de las computadoras en red.

NTP emplea el tiempo universal coordinado (UTC) para sincronizar las horas del reloj de la computadora con extrema precisión. Ofrece una mayor precisión en redes más pequeñas, hasta 1 milisegundo en una red de área local (LAN) y dentro de decenas de milisegundos en Internet. NTP no tiene en cuenta las zonas horarias. En cambio, depende del host para realizar tales cálculos.

Los grados de separación de la fuente UTC se definen como estratos. Los diversos estratos incluyen lo siguiente:
- Estrato 0. Un reloj de referencia recibe la hora real de un transmisor dedicado o un sistema de navegación por satélite. Se clasifica como estrato 0.
- Estrato 1. Un dispositivo está directamente vinculado al reloj de referencia.
- Estrato 2. Un dispositivo recibe su tiempo de una computadora de estrato 1.
- Estrato 3. Un dispositivo recibe su tiempo de una computadora de estrato 2.

La clasificación de estrato continúa a partir de ahí. La precisión se reduce con cada grado adicional de separación.

### Comparativa V3  vs V4
 - NTPv4  direccionamiento IPv4  e IPv6 cliente – servidor
 - Incorporar seguridad en las comunicaciones NTPv4  -
	- criptografía, clave publica y privada
- Mejora la Compatibilidad con DNS, almacena el nombre del host y la IP, a diferencia de la v3 que le nombre del host no era almacenado

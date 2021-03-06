---
title:  馃敺 Modelos de interaccion
banner_icon: 馃敺
---
![Caracteristicas](/sistemas-distribuidos/Examen1/images/modelint1.png)
Respecto a la interacci贸n, los sistemas distribuidos deben tener en cuenta que
- Hay limitaciones debidas a la comunicaci贸n
- Es imposible predecir el retraso con el que llega un mensaje
- Es imposible tener una noci贸n global de tiempo
	- La ejecuci贸n es no determinista y dif铆cil de depurar

## Algoritmo distribuido
Definici贸n de los pasos que hay que llevar a cabo por cada uno de los procesos del sistema, incluyendo los mensajes de transmisi贸n entre ellos.

## Prestaciones del canal de comunicaci贸n
![Caracteristicas](/sistemas-distribuidos/Examen1/images/com1.png)
### Latencia
- Retardo entre el env铆o de un mensaje y su recepci贸n
- Ancho de banda
- Informaci贸n que puede transmitirse en un intervalo de tiempo: Fluctuaci贸n (jitter)
- Variaci贸n del tiempo invertido en repartir una serie de mensajes

## Protocolos de Enrutamiento
- RIP: Es un protocolo de enrutamiento que se basa en el n煤mero de saltos para decidir cu谩l es la mejor ruta hacia una red de destino.
![Caracteristicas](/sistemas-distribuidos/Examen1/images/rip.jpg)
- OSPF: Es un protocolo de enrutamiento cuya m茅trica es el costo. Aquella ruta que posea el menor costo ser谩 la ideal y la que ser谩 seleccionada como mejor camino hacia una red de destino.
![Caracteristicas](/sistemas-distribuidos/Examen1/images/ospf.png)
- BGP: BGP significa Border Gateway Protocol y se utiliza para permitir la comunicaci贸n entre los routers de borde pertenecientes a sistemas aut贸nomos diferentes. BGP es un protocolo de gran importancia para las empresas Telco y para los ISPs.
![Caracteristicas](/sistemas-distribuidos/Examen1/images/bgp.webp)
- EIGRP: Fue desarrollado por la empresa Cisco Systems y usa una m茅trica compuesta para decidir la mejor ruta hacia una red de destino. Puedes obtener m谩s detalles de su configuraci贸n y funcionamiento en nuestro Curso gratuito de Fundamentos de EIGRP que encontrar谩s en nuestra plataforma de Telecapp Academy.
![Caracteristicas](/sistemas-distribuidos/Examen1/images/eigrp.png)

## Relojes y eventos de tiempo
Cada computador tiene su propio reloj interno (reloj local)
- Puede usarse en procesos locales para marcas de tiempo 
### Tasa de deriva de reloj (clock drift rate)
- Evoluci贸n de la diferencia entre un reloj local y un reloj de referencia 鈥減erfecto鈥?
- Receptores GPS
- Network Time Protocol (NTP)
- Mecanismos de ordenaci贸n de eventos

### Dos tipos de modelo de interacci贸n
- S铆ncrono
- As铆ncrono

![Caracteristicas](/sistemas-distribuidos/Examen1/images/syncasyn.png)
En la comunicaci贸n sincr贸nica, los datos se transfieren en forma de tramas, mientras que, en la asincr贸nica, los datos se env铆an de un byte en un byte. La transmisi贸n sincr贸nica necesita una se帽al de reloj entre el emisor y el receptor para informar al segundo sobre la llegada del nuevo byte o mensaje.

#### Modelos Sincr贸nicos
Conocimiento de caracter铆sticas temporales:
- El tiempo de ejecuci贸n de cada etapa de un proceso tiene ciertos l铆mites inferior y superior conocidos 
- Cada mensaje transmitido sobre un canal se recibe en un tiempo l铆mite conocido
	- Cada proceso tiene un reloj local cuya tasa de deriva sobre el tiempo de referencia tiene un l铆mite conocido
- A nivel te贸rico, podemos establecer unos l铆mites para tener una idea aproximada de c贸mo se comportar谩 el sistema 
- A nivel pr谩ctico, es imposible garantizar esos l铆mites siempre 
- Aunque a veces se pueden utilizar, por ejemplo, como tineos

#### Modelos Asincr贸nicos
No hay limitaciones en cuanto a:
- Velocidad de procesamiento.
- Retardos en la transmisi贸n de mensajes.
- Tasas de deriva de los relojes.
- Los sistemas distribuidos reales suelen ser as铆ncronos. 
	Por ejemplo, Internet.
- Una soluci贸n v谩lida para un sistema as铆ncrono lo es tambi茅n para uno s铆ncrono.
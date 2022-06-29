# Modelos de interaccion
Respecto a la interacción, los sistemas distribuidos deben tener en cuenta que
- Hay limitaciones debidas a la comunicación
- Es imposible predecir el retraso con el que llega un mensaje
- Es imposible tener una noción global de tiempo
	- La ejecución es no determinista y difícil de depurar

## Algoritmo distribuido
Definición de los pasos que hay que llevar a cabo por cada uno de los procesos del sistema, incluyendo los mensajes de transmisión entre ellos.

## Prestaciones del canal de comunicación
### Latencia
- Retardo entre el envío de un mensaje y su recepción
- Ancho de banda
- Información que puede transmitirse en un intervalo de tiempo: Fluctuación (jitter)
- Variación del tiempo invertido en repartir una serie de mensajes

## Protocolos de Enrutamiento
- RIP: Es un protocolo de enrutamiento que se basa en el número de saltos para decidir cuál es la mejor ruta hacia una red de destino.
- OSPF: Es un protocolo de enrutamiento cuya métrica es el costo. Aquella ruta que posea el menor costo será la ideal y la que será seleccionada como mejor camino hacia una red de destino.
- BGP: BGP significa Border Gateway Protocol y se utiliza para permitir la comunicación entre los routers de borde pertenecientes a sistemas autónomos diferentes. BGP es un protocolo de gran importancia para las empresas Telco y para los ISPs.
- EIGRP: Fue desarrollado por la empresa Cisco Systems y utiliza una métrica compuesta para decidir la mejor ruta hacia una red de destino. Puedes obtener más detalles de su configuración y funcionamiento en nuestro Curso gratuito de Fundamentos de EIGRP que encontrarás en nuestra plataforma de Telecapp Academy.

## Relojes y eventos de tiempo
Cada computador tiene su propio reloj interno (reloj local)
- Puede usarse en procesos locales para marcas de tiempo 
### Tasa de deriva de reloj (clock drift rate)
- Evolución de la diferencia entre un reloj local y un reloj de referencia “perfecto”
- Receptores GPS
- Network Time Protocol (NTP)
- Mecanismos de ordenación de eventos

### Dos tipos de modelo de interacción
- Sincrono
- Asincrono

En la comunicación sincrónica, los datos se transfieren en forma de tramas, mientras que, en la asincrónica, los datos se envían de un byte en un byte. La transmisión sincrónica necesita una señal de reloj entre el emisor y el receptor para informar al segundo sobre la llegada del nuevo byte o mensaje.

#### Modelos Sincrónicos
Conocimiento de características temporales:
- El tiempo de ejecución de cada etapa de un proceso tiene ciertos límites inferior y superior conocidos 
- Cada mensaje transmitido sobre un canal se recibe en un tiempo límite conocido
	- Cada proceso tiene un reloj local cuya tasa de deriva sobre el tiempo de referencia tiene un límite conocido
- A nivel teórico, podemos establecer unos límites para tener una idea aproximada de cómo se comportará el sistema 
- A nivel práctico, es imposible garantizar esos límites siempre 
- Aunque a veces se pueden utilizar, por ejemplo, como tineos

#### Modelos Asincrónicos
No hay limitaciones en cuanto a:
- Velocidad de procesamiento.
- Retardos en la transmisión de mensajes.
- Tasas de deriva de los relojes.
- Los sistemas distribuidos reales suelen ser asíncronos. 
	Por ejemplo, Internet.
- Una solución válida para un sistema asíncrono lo es también para uno síncrono.
---
title: 馃拰 Comunicacion orientada a mensajes
banner_icon: 馃拰
---
La comunicaci贸n entre procesos es el n煤cleo de todos los sistemas distribuidos *Tanenbaum & Van Steen, 2008*, por tal raz贸n es importante entender la manera en que los procesos localizados en diferentes computadoras pueden intercambiar informaci贸n. 

La comunicaci贸n entre procesos necesita compartir informaci贸n:
1. datos compartidos
2. Pasajes de mensajes o copias compartidas

En los sistemas distribuidos tradicionalmente la comunicaci贸n est谩 basada en el paso de mensaje. Esta t茅cnica aporta sincronizaci贸n entre procesos y permite la exclusi贸n mutua, su principal caracter铆stica es que no requiere memoria compartida, por lo que resulta ser muy relevante en la programaci贸n de sistemas distribuidos.

## Tipos de comunicaci贸n
### Comunicaci贸n PERSISTENTE: 
Almacena el mensaje (informaci贸n) enviado por el emisor el tiempo que tome entregarlo al receptor.

### Comunicaci贸n TRANSITORIA
Almacena un mensaje solo mientras las aplicaciones del emisor y receptor est谩n en ejecuci贸n.

### Comunicaci贸n ASINCR脫NICA 
El emisor contin煤a inmediatamente despu茅s de que ha pasado su mensaje para la transmisi贸n

### Comunicaci贸n SINCR脫NICA 
El emisor es bloqueado hasta que se sabe que su petici贸n es aceptada

![Caracteristicas](/sistemas-distribuidos/Examen3/images/pers.jpg)

![Caracteristicas](/sistemas-distribuidos/Examen3/images/ps.jpg)

![Caracteristicas](/sistemas-distribuidos/Examen3/images/tras.png)
## Paradigmas de comunicaci贸n
### Comunicaci贸n directa
Las primitivas enviar y recibir  usan directamente el nombre del proceso con el que se comunican. 

### Comunicaci贸n indirecta
Las operaciones b谩sicas Send y Receive se definen de la siguiente manera: Send (P, mensaje); env铆a un mensaje al proceso P. Receive (Q, mensaje); espera la recepci贸n de un mensaje por parte del proceso Q.
![Caracteristicas](/sistemas-distribuidos/Examen3/images/direct.png)
## Comunicaci贸n RPC
La RPC o Remote Procedure Call (en espa帽ol, llamada a procedimiento remoto) es una herramienta b谩sica para establecer estructuras colaborativas y operativas en redes y arquitecturas cliente-servidor. 

El proceso de comunicaci贸n con RPC consta del env铆o de par谩metros y el retorno de un valor de funci贸n. A menudo, no se limita a una sola llamada, ya que en la pr谩ctica se procesan muchas solicitudes en paralelo.

La idea de RPC es que una llamada a un procedimiento remoto se parezca lo m谩s posible a una llamada local, esto le permite una mayor transparencia. Para ello, el RPC usa una instancia del cliente que se encarga de empacar los par谩metros en un mensaje y le solicita al n煤cleo que env铆e el mensaje al servidor, posteriormente se bloquea hasta que regrese la respuesta. 
![Caracteristicas](/sistemas-distribuidos/Examen3/images/rpc.png)
![Caracteristicas](/sistemas-distribuidos/Examen3/images/rpc2.png)
## Multidifusi贸n Multicast
![Caracteristicas](/sistemas-distribuidos/Examen3/images/mult.jpg)
### Objetivo
entrega de mensajes a un grupo de procesos distribuidos, garantizando
-	Fiabilidad: todos los procesos del grupo reciben el mensaje
-	Orden: el orden de entrega del mensaje es acordado y se respeta
### Fundamento
-	Un proceso realiza solo una operaci贸n multicast para enviar un
	mensaje a todos los miembros del grupo
-	Un proceso obtiene mensajes mediante una orden entrega, que no
	implica una recepci贸n instant谩nea del mensaje
### Multidifusi贸n b谩sica
- **Envuelven** a las operaciones de env铆o y recepci贸n 
- Los procesos pueden pertenecer a varios grupos
- Cada mensaje se destina a un grupo en particular

Ejemplo: hilos para env铆o concurrente

## Multidifusi贸n fiable
Debe cumplir con las condiciones de:
- Integridad: un proceso entrega un mensaje a lo sumo una vez
- Validez: todo mensaje multidifundido es entregado al remitente
	- Garantiza que el remitente sigue vivo tras la multidifusi贸n
- Acuerdo: si un proceso recibe un mensaje, todo el grupo lo recibe
	-	Concepto de 鈥渁tomicidad鈥?: o todos, o ninguno
	-	Esta condici贸n no se cumple en B-multicast, que solo garantiza la comunicaci贸n fiable uno a uno.


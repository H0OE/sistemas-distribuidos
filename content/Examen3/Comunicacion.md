---
title: 💌 Comunicacion orientada a mensajes
banner_icon: 💌
---
La comunicación entre procesos es el núcleo de todos los sistemas distribuidos *Tanenbaum & Van Steen, 2008*, por tal razón es importante entender la manera en que los procesos localizados en diferentes computadoras pueden intercambiar información. 

La comunicación entre procesos necesita compartir información:
1. datos compartidos
2. Pasajes de mensajes o copias compartidas

En los sistemas distribuidos tradicionalmente la comunicación está basada en el paso de mensaje. Esta técnica aporta sincronización entre procesos y permite la exclusión mutua, su principal característica es que no requiere memoria compartida, por lo que resulta ser muy relevante en la programación de sistemas distribuidos.

## Tipos de comunicación
### Comunicación PERSISTENTE: 
Almacena el mensaje (información) enviado por el emisor el tiempo que tome entregarlo al receptor.

### Comunicación TRANSITORIA
Almacena un mensaje solo mientras las aplicaciones del emisor y receptor están en ejecución.

### Comunicación ASINCRÓNICA 
El emisor continúa inmediatamente después de que ha pasado su mensaje para la transmisión

### Comunicación SINCRÓNICA 
El emisor es bloqueado hasta que se sabe que su petición es aceptada

![Caracteristicas](/sistemas-distribuidos/Examen3/images/pers.jpg)

![Caracteristicas](/sistemas-distribuidos/Examen3/images/ps.jpg)

![Caracteristicas](/sistemas-distribuidos/Examen3/images/tras.png)
## Paradigmas de comunicación
### Comunicación directa
Las primitivas enviar y recibir  usan directamente el nombre del proceso con el que se comunican. 

### Comunicación indirecta
Las operaciones básicas Send y Receive se definen de la siguiente manera: Send (P, mensaje); envía un mensaje al proceso P. Receive (Q, mensaje); espera la recepción de un mensaje por parte del proceso Q.
![Caracteristicas](/sistemas-distribuidos/Examen3/images/direct.png)
## Comunicación RPC
La RPC o Remote Procedure Call (en español, llamada a procedimiento remoto) es una herramienta básica para establecer estructuras colaborativas y operativas en redes y arquitecturas cliente-servidor. 

El proceso de comunicación con RPC consta del envío de parámetros y el retorno de un valor de función. A menudo, no se limita a una sola llamada, ya que en la práctica se procesan muchas solicitudes en paralelo.

La idea de RPC es que una llamada a un procedimiento remoto se parezca lo más posible a una llamada local, esto le permite una mayor transparencia. Para ello, el RPC usa una instancia del cliente que se encarga de empacar los parámetros en un mensaje y le solicita al núcleo que envíe el mensaje al servidor, posteriormente se bloquea hasta que regrese la respuesta. 
![Caracteristicas](/sistemas-distribuidos/Examen3/images/rpc.png)
![Caracteristicas](/sistemas-distribuidos/Examen3/images/rpc2.png)
## Multidifusión Multicast
![Caracteristicas](/sistemas-distribuidos/Examen3/images/mult.jpg)
### Objetivo
entrega de mensajes a un grupo de procesos distribuidos, garantizando
-	Fiabilidad: todos los procesos del grupo reciben el mensaje
-	Orden: el orden de entrega del mensaje es acordado y se respeta
### Fundamento
-	Un proceso realiza solo una operación multicast para enviar un
	mensaje a todos los miembros del grupo
-	Un proceso obtiene mensajes mediante una orden entrega, que no
	implica una recepción instantánea del mensaje
### Multidifusión básica
- **Envuelven** a las operaciones de envío y recepción 
- Los procesos pueden pertenecer a varios grupos
- Cada mensaje se destina a un grupo en particular

Ejemplo: hilos para envío concurrente

## Multidifusión fiable
Debe cumplir con las condiciones de:
- Integridad: un proceso entrega un mensaje a lo sumo una vez
- Validez: todo mensaje multidifundido es entregado al remitente
	- Garantiza que el remitente sigue vivo tras la multidifusión
- Acuerdo: si un proceso recibe un mensaje, todo el grupo lo recibe
	-	Concepto de “atomicidad”: o todos, o ninguno
	-	Esta condición no se cumple en B-multicast, que solo garantiza la comunicación fiable uno a uno.


---
title:  💻 Modelo de Fallos
---
## Tipos de fallo según entidad
- Fallos de proceso
- Fallos de comunicación
## Tipo de fallo según el problema
![Caracteristicas](/sistemas-distribuidos/Examen1/images/fails.png)
- Fallos por omisión **Afecta al canal**
	-  No se consigue realizar una acción que se debería poder hacer
	-  Un mensaje insertado en un búfer de mensajes salientes nunca llega al búfer de mensajes entrantes del destino

- Fallos arbitrarios (bizantinos)  **Afecta al proceso o canal**
	- Errores de cualquier tipo, fuera del esquema de mensajes
	- El proceso/Canal presenta un comportamiento arbitrario: omisiones, paradas, envíos o pasos incorrectos sin patrón claro

- Fallos de temporización
	- Superación de tiempos límite en un sistema síncrono

- Fallo del procesamiento (crash)  **Afecta al proceso**
	- Un mensaje insertado en un búfer de mensajes saliente, otros procesos no pueden detectar la parada

- Fallo parada (fail-stop)  **Afecta al proceso**
	- Fallo de procesamiento que puede ser detectado con certeza por el resto de los procesos
	- El proceso para y permanece parado, otros procesos pueden detectar la parada

- Detección del fallo por timeouts (síncrono)
	- Si el proceso no responde consideramos que ha habido un fallo
	- En sistemas asíncronos, nunca podemos estar seguros

- Fallo por omisión en comunicaciones
	-  Fallo por omisión de envío  **Afecta al proceso**
		-  Un proceso completa el envio pero no se coloca el mensaje en el búfer de mensajes salientes
	- Fallo por omisión de comunicación **Afecta al canal**
	- Fallo por omisión de recepción  **Afecta al proceso**
		- El mensaje se coloca en el buffer de recepción pero el proceso no lo recibe

## Fallos de temporización
- Sistemas síncronos
	- Reloj Afecta al proceso
		- El reloj local del proceso excede el límite de su tasa de deriva respecto al tiempo de referencia
	- Prestaciones Afecta el proceso
		- El proceso excede el límite sobre el intervalo
	- Prestaciones Afecta el canal
		- La transmisión de un mensaje toma más tiempo que el tiempo permitido
- Sistemas Asíncronos
	- No hay fallos de temporización
## Comunicación fiable entre procesos
Se debe cumplir la:
- Validez
	- Cualquier mensaje en el búfer de mensajes salientes llegará eventualmente al búfer de mensajes entrantes
	- Es decir, no hay fallos por omisión en el canal
- Integridad
	- El mensaje recibido es idéntica al enviado y no se repiten mensajes
		- Protocolo que adjunta números de secuencia a los mensajes
		- Canales de comunicacion seguros
	- No hay fallos bizantino
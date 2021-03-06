---
title:  馃挗 Modelo de Fallos
banner_icon: 馃挗
---
## Tipos de fallo seg煤n entidad
- Fallos de proceso
- Fallos de comunicaci贸n
## Tipo de fallo seg煤n el problema
![Caracteristicas](/sistemas-distribuidos/Examen1/images/fails.png)
- Fallos por omisi贸n **Afecta al canal**
	-  No se consigue realizar una acci贸n que se deber铆a poder hacer
	-  Un mensaje insertado en un b煤fer de mensajes salientes nunca llega al b煤fer de mensajes entrantes del destino

- Fallos arbitrarios (bizantinos)聽 **Afecta al proceso o canal**
	- Errores de cualquier tipo, fuera del esquema de mensajes
	- El proceso/Canal presenta un comportamiento arbitrario: omisiones, paradas, env铆os o pasos incorrectos sin patr贸n claro

- Fallos de temporizaci贸n
	- Superaci贸n de tiempos l铆mite en un sistema s铆ncrono

- Fallo del procesamiento (crash)聽 **Afecta al proceso**
	- Un mensaje insertado en un b煤fer de mensajes saliente, otros procesos no pueden detectar la parada

- Fallo parada (fail-stop)聽 **Afecta al proceso**
	- Fallo de procesamiento que puede ser detectado con certeza por el resto de los procesos
	- El proceso para y permanece parado, otros procesos pueden detectar la parada

- Detecci贸n del fallo por timeouts (s铆ncrono)
	- Si el proceso no responde consideramos que ha habido un fallo
	- En sistemas as铆ncronos, nunca podemos estar seguros

- Fallo por omisi贸n en comunicaciones
	-  Fallo por omisi贸n de env铆o聽 **Afecta al proceso**
		-  Un proceso completa el envio pero no se coloca el mensaje en el b煤fer de mensajes salientes
	- Fallo por omisi贸n de comunicaci贸n聽**Afecta al canal**
	- Fallo por omisi贸n de recepci贸n聽 **Afecta al proceso**
		- El mensaje se coloca en el buffer de recepci贸n pero el proceso no lo recibe

![Caracteristicas](/sistemas-distribuidos/Examen1/images/enemy.png)

## Fallos de temporizaci贸n
- Sistemas s铆ncronos
	- Reloj Afecta al proceso
		- El reloj local del proceso excede el l铆mite de su tasa de deriva respecto al tiempo de referencia
	- Prestaciones Afecta el proceso
		- El proceso excede el l铆mite sobre el intervalo
	- Prestaciones Afecta el canal
		- La transmisi贸n de un mensaje toma m谩s tiempo que el tiempo permitido
- Sistemas As铆ncronos
	- No hay fallos de temporizaci贸n
## Comunicaci贸n fiable entre procesos
Se debe cumplir la:
- Validez
	- Cualquier mensaje en el b煤fer de mensajes salientes llegar谩 eventualmente al b煤fer de mensajes entrantes
	- Es decir, no hay fallos por omisi贸n en el canal
- Integridad
	- El mensaje recibido es id茅ntica al enviado y no se repiten mensajes
		- Protocolo que adjunta n煤meros de secuencia a los mensajes
		- Canales de comunicacion seguros
	- No hay fallos bizantino

![Caracteristicas](/sistemas-distribuidos/Examen1/images/memefails.png)
---
title:  馃攽 Modelos de Seguridad
banner_icon: 馃攽
---
La seguridad en un sistema distribuido se basa en la seguridad de los procesos y canales utilizados
- Entendida como seguridad de objetos
- Almacenados e invocados por los procesos
- Transmitidos a trav茅s de los canales
- Se logra mediante un sistema de derechos de acceso y distintos tipos de autoridad

## Principal
Autoridad con la que se ordena cada invocaci贸n de objetos o sus resultados
- Se contrasta con los derechos de acceso de dicho objeto
![Caracteristicas](/sistemas-distribuidos/Examen1/images/segu1.jpg)
## Modelo de enemigo
![Caracteristicas](/sistemas-distribuidos/Examen1/images/enemy2.jpg)
### Entidad
Cualquier m谩quina conectada( de forma autorizada o no) a la red 
### Enemigo 
Entidad capaz de:
- Enviar cualquier mensaje a cualquier proceso
- Leer o copiar cualquier mensaje compartido entre dos procesos
- Leer mensajes o emitir mensajes falsos de petici贸n de servicios.

## Amenazas a servidores
Ciertos servicios no comprueban la identidad del cliente
- Si la comprueban, no suele ser dif铆cil suplantarla (spoofing)

En vez de una petici贸n de servicio aut茅ntica se busca, p. ej., obtener informaci贸n no autorizada o bloquear el servicio (DoS)

## Amenazas a clientes
- Reciben un resultado falso de la invocaci贸n al servicio
- Generalmente, acompa帽ado de suplantaci贸n de identidad

## Amenazas a canales de comunicaci贸n
- Inyecci贸n, copia o alteraci贸n de mensajes que viajan por el canal

Por ejemplo: obtener un mensaje de transferencia de dinero, cambiar la cuenta y re enviarlo despu茅s

## T茅cnicas de seguridad
- Autenticaci贸n: Comprobaci贸n de la identidad del proceso
- Criptograf铆a: Uso de claves p煤blicas y privadas
- Canales seguros: Canal de comunicaci贸n sobre el que dos procesos han establecido una capa de seguridad basada en criptograf铆a + autenticaci贸n:
	- Se garantiza la identidad fiable de servidores y clientes
	- Se garantiza la integridad y privacidad de los mensajes enviados
	- Los mensajes incluyen una marca de tiempo para prevenir su repetici贸n o reordenaci贸n maliciosa

# Modelos de Seguridad
```toc
```
La seguridad en un sistema distribuido se basa en la seguridad de los procesos y canales utilizados
- Entendida como seguridad de objetos
- Almacenados e invocados por los procesos
- Transmitidos a través de los canales
- Se logra mediante un sistema de derechos de acceso y distintos tipos de autoridad

## Principal
Autoridad con la que se ordena cada invocación de objetos o sus resultados
- Se contrasta con los derechos de acceso de dicho objeto
## Modelo de enemigo
### Entidad
Cualquier máquina conectada( de forma autorizada o no) a la red 
### Enemigo 
Entidad capaz de:
- Enviar cualquier mensaje a cualquier proceso
- Leer o copiar cualquier mensaje compartido entre dos procesos
- Leer mensajes o emitir mensajes falsos de petición de servicios.

## Amenazas a servidores
Ciertos servicios no comprueban la identidad del cliente
- Si la comprueban, no suele ser difícil suplantarla (spoofing)

En vez de una petición de servicio auténtica se busca, p. ej., obtener información no autorizada o bloquear el servicio (DoS)

## Amenazas a clientes
- Reciben un resultado falso de la invocación al servicio
- Generalmente, acompañado de suplantación de identidad

## Amenazas a canales de comunicación
- Inyección, copia o alteración de mensajes que viajan por el canal

Por ejemplo: obtener un mensaje de transferencia de dinero, cambiar la cuenta y re enviarlo después

## Técnicas de seguridad
- Autenticación: Comprobación de la identidad del proceso
- Criptografía: Uso de claves públicas y privadas
- Canales seguros: Canal de comunicación sobre el que dos procesos han establecido una capa de seguridad basada en criptografía + autenticación:
	- Se garantiza la identidad fiable de servidores y clientes
	- Se garantiza la integridad y privacidad de los mensajes enviados
	- Los mensajes incluyen una marca de tiempo para prevenir su repetición o reordenación maliciosa

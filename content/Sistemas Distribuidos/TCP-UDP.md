# TCP y UDP
## TCP
TCP (Protocolo de Control de Transmisión, por sus siglas en inglés Transmission Control Protocol) es protocolo de red importante que permite que dos anfitriones (hosts) se conecten e intercambien flujos de datos. TCP garantiza la entrega de datos y paquetes (en-US) en el mismo orden en que se enviaron.

## UDP
El Protocolo de datagrama de usuario (UDP) es un protocolo ligero de transporte de datos que funciona sobre IP. UDP proporciona un mecanismo para detectar datos corruptos en paquetes, pero no intenta resolver otros problemas que surgen con paquetes, como cuando se pierden o llegan fuera de orden.

## Diferencias
- Conexión: TCP es un protocolo orientado a la conexión mientras que UDP no utiliza conexión. TCP establece una conexión entre un remitente y un receptor antes de que se puedan enviar los datos. UDP en cambio, no establece ninguna conexión antes de enviar los datos. 
- Fiabilidad: TCP es confiable ya que garantiza que los datos enviados mediante el protocolo TCP se entreguen al receptor. Si los datos se pierden en el camino, los recuperará y los reenviará. TCP también verifica los paquetes en busca de errores y los rastrea para que los datos no se pierdan ni se corrompan. En cambio, UDP no es confiable. Este no garantiza la entrega de los paquetes y los paquetes pueden corromperse o perderse en tránsito. 
- Control de Flujo: TCP utiliza un mecanismo de control de flujo que garantiza que el remitente no sature al receptor enviando demasiados paquetes a la vez. Este, almacena los datos en un búfer de envío y los recibe en un búfer de recepción. Cuando la aplicación está lista, lee los datos del búfer de recepción. Si el búfer de recepción está lleno, el receptor no puede manejar más datos y los elimina. Cada vez que el receptor recibe un paquete, envía un mensaje al remitente. UDP, no proporciona control de flujo. Con UDP, los paquetes llegan de forma continua o se descartan. 
- Ordenación: TCP ordena los paquetes para garantizar que se entreguen al cliente en el mismo orden en que se enviaron. En cambio, UDP envía los paquetes sin importar el orden. 
- Velocidad: Otra diferencia entre TCP y UDP, es que TCP es más lento, porque hace mucho más que enviar datos. TCP establece una conexión, verifica los errores y garantiza que los archivos se reciban en el orden en que fueron enviados tal y como hemos comentado anteriormente. Por lo tanto, la velocidad es uno de los aspectos en los que destaca UDP. 

- Uso: TCP es el protocolo más adecuado para usarse en aplicaciones que requieren una alta confiabilidad.
	- Páginas web (HTTP, HTTPS) 
	- Correo electrónico (SMTP, IMAP/POP) 
	- SSH 
	- FTP
- UDP es más adecuado para aplicaciones que requieren velocidad y eficiencia.
	- VPN 
	- Juegos online 
	- Videos en directo
	- DNS 
	- Voz a través de internet (VoIP) 
	- TFTP
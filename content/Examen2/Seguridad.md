---
title: ⌨️ Seguridad
banner_icon: ⌨️
---
## DES 56 bit
DES es el nombre del documento FIPS (Federal Information Processing Standard), es un algoritmo de cifrado por bloques de 64 bits de tamaño. Emplea una clave de 56 bits durante la ejecución.
- Cuando se utiliza en comunicaciones ambos participantes deben conocer la clave secreta 
- El algoritmo se puede usar para encriptar y desencriptar mensajes, 
- Puede generar y verificar códigos de autentificación de mensajes
- El problema principal es que el tamaño de la clave (56 bits) es demasiado pequeño para la potencia de cálculo actual. De hecho, el DES dejó de ser el algoritmo empleado por el gobierno norteamericano en noviembre de 1998 y de momento (hasta que el AES sea elegido), emplean el Triple DES
![Caracteristicas](/sistemas-distribuidos/Examen2/images/des.jpg)

## 3DES
Consiste en encriptar tres veces una clave DES:
- DES-EEE3: Tres encriptaciones DES con tres claves distintas.

- Diffie y Hellman propusieron una máquina con un coste estimado de 20 millones de dólares que podría encontrar una clave DES en un solo día.
- Wiener sugirió una máquina de búsqueda de claves con un coste de un millón de dólares que encontraría una clave en 7 horas.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/3des.png)
## RSA
- El algoritmo asimétrico por excelencia
- Este algoritmo se basa en la pareja de claves
- La seguridad de este algoritmo radica en el problema de la factorización de números enteros muy grandes
- Actualmente como mínimo se debe utilizar una longitud de 2048 bits, aunque es recomendable que sea de 4096 bits o superior para tener una mayor seguridad.
- El sistema RSA permite longitudes variables, siendo aconsejable actualmente el uso de claves de no menos de 1024 bits (se han roto claves de hasta 512 bits, aunque se necesitaron más de 5 meses y casi 300 ordenadores trabajando juntos para hacerlo).

El cifrado RSA funciona bajo la premisa de que el algoritmo es fácil de calcular en una dirección, pero casi imposible en sentido inverso. Como ejemplo, si te dijeran que 701.111 es un producto de dos números primos, ¿serías capaz de averiguar cuáles son esos dos números?

-   En RSA de **2048 bits, se unirían para crear claves de 617 dígitos**

![Caracteristicas](/sistemas-distribuidos/Examen2/images/rsa.png)
## DIFFIE HELLMAN
Se usa para generar una clave privada a ambos extremos de un canal de comunicación inseguro.
- Se emplea para obtener la clave privada con la que posteriormente se cifrará la información junto con un algoritmo de cifrado simétrico. 
- No es un algoritmo asimétrico propiamente dicho, es un protocolo de establecimiento de claves
- Su seguridad radica en la dificultad de calcular el logaritmo discreto de números grandes
- El problema de este algoritmo es que no proporciona autenticación, no puede validar la identidad de los usuarios, por tanto, si un tercer usuario se pone en medio de la comunicación, también se le facilitaría las claves y, en consecuencia, podría establecer comunicaciones con el emisor y el receptor suplantando las identidades. 
- Certificaciones digitales
![Caracteristicas](/sistemas-distribuidos/Examen2/images/diffi.png)
## TLS
TLS se traduce a Transport Layer Security o en español Seguridad de la Capa de Transporte y su sucesor SSL 
-   TLS provee una comunicación segura entre los navegadores de internet y los servidores. La conexión en sí, es segura gracias a que se usa una criptografía segura para encriptar los datos transmitidos.
-   Las llaves son generadas de forma única por cada conexión y se basan en un secreto compartido negociado al comienzo de la sesión, también conocido como “saludo de mano TLS”.
-   Con la TLS 1.2, se hubieran requerido dos rondas de viaje para completar un saludo de mano TLS.
-   Con el 1.3, requiere tan solo una ronda de viaje, la cual termina cortando hasta por la mitad la latencia de la encriptación.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/tls.png)
![Caracteristicas](/sistemas-distribuidos/Examen2/images/tls2.webp)
## HASH
Es un algoritmo matemático que transforma cualquier bloque arbitrario de datos en una nueva serie de caracteres con una longitud fija.
-   Independientemente de la longitud de los datos de entrada, el valor hash de salida tendrá siempre la misma longitud.
-   No existen dos entradas que produzcan el mismo hash de salida
- Se utilizan las funciones criptográficas hash para detectar malware
- Las funciones criptográficas hash se utilizan también para asegurar la “integridad de los mensajes
- gestión de los identificadores y contraseñas
![Caracteristicas](/sistemas-distribuidos/Examen2/images/hash.jpg)
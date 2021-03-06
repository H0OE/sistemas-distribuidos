---
title: 馃か VPN IPsec
banner_icon: 馃か
---
## VPN
Una red privada virtual (VPN, por sus siglas en ingl茅s) es una tecnolog铆a que permite a los usuarios enviar y recibir datos a trav茅s de redes compartidas o p煤blicas, como si sus equipos inform谩ticos estuvieran conectados directamente a la red privada. 

Un protocolo de tunelizaci贸n es un protocolo que encapsula en su datagrama otro paquete de datos completo que utiliza un protocolo de comunicaciones diferente. Esencialmente, crea un t煤nel entre dos puntos de una red por el cual se puede transmitir de forma segura cualquier tipo de datos.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/vpn.png)
## IPsec
IPsec es un tipo de protocolo que ofrece un conjunto de est谩ndares para que se piensa una conexi贸n VPN. Este protocolo permite encriptar los paquetes que se env铆an para que viaje por ese t煤nel y llegue al otro punto de manera segura, este protocolo cubre los siguientes puntos:
-   Autenticaci贸n de origen de datos: Verifica si el origen de los paquetes son realmente el origen indicado.
-   Integridad de los datos: Comprueba si el paquete es exactamente igual a como salieron el origen.聽
-   Confidencialidad de los datos: Significa que oculto el contenido por un cifrado.
-   Protecci贸n de reproducci贸n: Impide que los paquetes puedan ser interceptados y despu茅s volverlos a reproducir.
-   Gesti贸n automatizada de claves criptogr谩ficas y asociaciones de seguridad: Permite utilizar VPN sin configuraci贸n manual o con muy poca.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/ipsec.jpg)
## Protocolos
Los protocolos que usa para las cabeceras y para el cuerpo son los siguientes

-   AH: protocolo de cabecera de autenticaci贸n, ofrece protecci贸n de reproducci贸n, integridad de los datos y autenticaci贸n del origen de los datos, pero este no ofrece confidencialidad, por lo que los datos son enviados en texto plano.
    
-   ESP: Ofrece la confidencialidad de los datos que no ofrece AH y de tambi茅n puede ofrecer autenticaci贸n del origen de los datos, protecci贸n contra la reproducci贸n y comprobaci贸n de la integridad.

Este protocolo implica cinco componentes principales:
-   Protocolos de seguridad: Los datagramas son protegidos con los dos protocolos mencionados y explicados anteriormente.
-   Base de datos de asociaciones de seguridad (SADB): Esta base de datos es la que asocia un protocolo de seguridad con la direcci贸n de destino IP y un n煤mero de 铆ndice. La base de datos garantiza que se pueda reconocer un paquete que llega a su destino debidamente protegido.
-   Administraci贸n de claves: La distribuci贸n y generaci贸n de claves para los algoritmos criptogr谩ficos y SPI
-   Mecanismos de seguridad:Los algoritmos de cifrado y autenticaci贸n que protegen los datos de los datagramas IP.
-   Base de datos de directivas de seguridad (SPD): Esta base de datos especifica el nivel de protecci贸n que se aplicar谩 a un paquete, este filtra el tr谩fico IP para que se pueda hallar el modo en el que se procesaran los paquetes.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/ipsecp.png)
## Fases
Las negociaciones IPsec se dan en dos fases: 
- Fase 1, en esta fase se crea un canal seguro para negociar la asociaci贸n de seguridad IPsec(SA) 
- Fase 2, los participantes negocian esta SA para la autenticaci贸n del tr谩fico que pasa en este t煤nel.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/ipsecphas.jpg)
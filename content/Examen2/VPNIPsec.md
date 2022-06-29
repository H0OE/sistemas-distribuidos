---
title: 🪴 VPN IPsec
---
## VPN
Una red privada virtual (VPN por sus siglas en inglés) es una tecnología que permite a los usuarios enviar y recibir datos a través de redes compartidas o públicas como si sus equipos informáticos estuvieran conectados directamente a la red privada. 

Un protocolo de tunelización es un protocolo que encapsula en su datagrama otro paquete de datos completo que utiliza un protocolo de comunicaciones diferente. Esencialmente, crea un túnel entre dos puntos de una red por el cual se puede transmitir de forma segura cualquier tipo de datos.

## IPsec
IPsec es un tipo de protocolo que ofrece un conjunto de estándares para que se cree una conexión VPN. Este protocolo permite encriptar los paquetes que se envían para que viaje por ese túnel y llegue al otro punto de manera segura, este protocolo cubre los siguientes puntos:
-   Autenticación de origen de datos: Verifica si el origen de los paquetes son realmente el origen indicado.
-   Integridad de los datos: Verifica si el paquete es exactamente igual a como salieron el origen. 
-   Confidencialidad de los datos: Significa que oculto el contenido por un cifrado.
-   Protección de reproducción: Impide que los paquetes puedan ser interceptados y después volverlos a reproducir.
-   Gestión automatizada de claves criptográficas y asociaciones de seguridad: Permite utilizar VPN sin configuración manual o con muy poca.

## Protocolos
Los protocolos que usa para las cabeceras y para el cuerpo son los siguientes

-   AH: protocolo de cabecera de autenticación, ofrece protección de reproducción, integridad de los datos y autenticación del origen de los datos, pero este no ofrece confidencialidad por lo que los datos son enviados en texto plano.
    
-   ESP: Ofrece la confidencialidad de los datos que no ofrece AH y de también puede ofrecer autenticación del origen de los datos, protección contra la reproducción y comprobación de la integridad.

Este protocolo implica cinco componentes principales:
-   Protocolos de seguridad: Los datagramas son protegidos con los dos protocolos mencionados y explicados anteriormente.
-   Base de datos de asociaciones de seguridad (SADB): Esta base de datos es la que asocia un protocolo de seguridad con la dirección de destino IP y un número de índice. La base de datos garantiza que se pueda reconocer un paquete que llega a su destino debidamente protegido.
-   Administración de claves: La distribución y generación de claves para los algoritmos criptográficos y SPI
-   Mecanismos de seguridad:Los algoritmos de cifrado y autenticación que protegen los datos de los datagramas IP.
-   Base de datos de directivas de seguridad (SPD): Esta base de datos especifica el nivel de protección que se aplicará a un paquete, este filtra el tráfico IP para que se pueda hallar el modo en el que se procesaran los paquetes.

## Fases
Las negociaciones IPsec se dan en dos fases: 
- Fase 1, en esta fase se crea un canal seguro para negociar la asociación de seguridad IPsec(SA) 
- Fase 2, los participantes negocian este SA para la autenticación del tráfico que pasa en este túnel.
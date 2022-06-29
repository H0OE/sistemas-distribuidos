---
title: 🪴 DNS
---
![Caracteristicas](/sistemas-distribuidos/Examen2/images/dns.png)
 Una base de datos jerárquica y distribuida que almacena nombres de dominios y su relación a otra información como IP’s
    
## Jerarquía
- Root
-  Nivel Superior (net,com,org)
- Segundo Nivel (nombre)
- Subdominio
![Caracteristicas](/sistemas-distribuidos/Examen2/images/dnsjer.png)

## Fully Qualified Domain Name FQDN 
Es la ruta completa de una página o recurso en internet con respecto a toda la jerarquía.
- Consulta Recursiva: Se tiene la información del recurso en el servidor y el mismo logra proveer una respuesta
- Consulta Iterativa: El servidor tiene que buscar el recurso externamente y una vez que lo encuentra lo guarda en su cache y devuelva la respuesta (outsourcing)
- Reenviadores: básicamente un servidor mucho más rápido y con más memoria para resolver requests mucho más eficientemente 

![Caracteristicas](/sistemas-distribuidos/Examen2/images/fqdn.jpg)

## Registro de recursos:
 - A: Resuelve un nombre de host a una IP
 - Ptr: Resuelve IP a un host name
 - Mx: Servidor de correo
 - Ns: identifica el servidor de dns para cada zona
 ![Caracteristicas](/sistemas-distribuidos/Examen2/images/dns%20regi.png)
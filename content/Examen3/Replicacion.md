---
title: 🟣 Replicacion
banner_icon: 🟣
---
Mantenimiento de copias de la información en múltiples computadores
- Es un recurso utilizado ampliamente en sistemas distribuidos
- Servidores web: servidores caché y proxies
- DNS: copias de los mapeos URL-IP, actualizadas diariamente
- Google: Google Data Centers
Ayuda a mejorar un SD en distintos aspectos:
- Rendimiento
- Disponibilidad
- Tolerancia a fallos

- Se da principalmente a través de cachés en clientes o servidores
- Mantener copias de los resultados obtenidos en llamadas anteriores al servicio reduce el coste de llamadas idénticas. Evita el tiempo de latencia del cálculo del resultado o de las consultas a otros servidores
- La replicación de datos inmutables es trivial
- La replicación de datos cambiantes (frecuentes en la red) conlleva un coste en protocolos de intercambio y actualización, que pueden limitar la efectividad de la réplica

![Caracteristicas](/sistemas-distribuidos/Examen3/images/replica.jpg)
## Transparencia
Los clientes no son conscientes de que hay múltiples copias del recurso al que acceden para los clientes, solo existen recursos lógicos individuales

## Consistencia
Las operaciones sobre un conjunto de objetos replicados deben dar resultados que sigan 
 la especificación de corrección definida para dichos objetos

## Objeto
Cualquier entidad de información a replicar: Archivos, objetos Java, etc.

## Objeto lógico
Entidad de información visible por el usuario, implementada por distintas copias físicas o réplicas. Las réplicas de un objeto lógico no tienen por qué ser todas
iguales en todo momento.

Ejemplo: algunas pueden haberse actualizado y otras no
- Sistema asíncrono
- Los procesos fallan solo por caída

## Gestor de réplicas
Componentes que almacenan réplicas de un determinado objeto o servicio y operan sobre ellas.
## Frontal
Componente que atiende las llamadas de los clientes y se comunica con los gestores de réplicas.

## Petición
1. Petición: El frontal envía la petición a un gestor o bien envía la petición a un gestor y este reenvía a otros o multidifunde la petición a varios gestores
2. Coordinación: los gestores se coordinan para ejecutar la petición de manera consistente
3. Ejecución: se ejecuta la petición (puede ser de forma tentativa)
4. Acuerdo: se llega a un consenso antes de consumar la ejecución
5. Respuesta: uno o más gestores de réplicas responden al frontal

## Tolerancia a fallos
- Una alta disponibilidad no implica necesariamente corrección
- Puede haber datos no actualizados, o inconsistentes (concurrencia)
- Podemos utilizar replicación para ganar tolerancia a fallos, parada o caída
- Si tenemos n servidores, pueden fallar n-1 sin alterar el servicio
- Fallo bizantino:c

Deben proporcionar un servicio correcto, aunque fallen n procesos, mediante la replicación de datos y la funcionalidad asociada a los gestores de réplicas, de dos modelos principales:
- Replicación pasiva o primario-respaldo
- Replicación activa

### Replicación pasiva
Un gestor de réplicas primario y uno o más gestores secundarios (‘respaldos’ o ‘esclavos’)
- Los frontales solo se comunican con el gestor primario
- Ejecuta las operaciones y manda copias a los respaldos
- Si el primario falla, uno de los respaldos promociona a primario

#### Fases
1. Petición: el frontal envía la petición al gestor primario
2. Coordinación: el gestor primario ejecuta las peticiones siguiendo una ordenación FIFO
3. Ejecución: se ejecuta la petición y se almacena la respuesta
4. Acuerdo: si es una petición de actualización, el gestor primario envía la actualización a todos los respaldos, que confirman la recepción
5. Respuesta: el gestor primario responde al frontal

#### Análisis
- Tolera fallos de proceso (gestor primario o respaldos)
- No tolera fallos bizantinos
- El frontal requiere poca funcionalidad
- Al controlar el orden de modificación mediante el gestor primario, mantiene la consistencia secuencial
- Problemas de cuello de botella en el gestor primario
- Actualización de todos los respaldos antes de dar respuesta
- Los respaldos no dan servicio directo

### Replicación Activa
Todos los gestores de réplicas tienen el mismo papel los frontales multidifunden las peticiones a todos los gestores,  los gestores de réplicas procesan la petición de manera independiente, pero idéntica.

#### Fases
1. Petición: el frontal multidifunde la petición a los gestores. Se utiliza multidifusión fiable y de ordenación total*. No envía otra petición hasta que recibe la respuesta a la actual
2. Coordinación: el sistema de comunicación entrega la petición a todos los gestores según una ordenación total (multidifusión)
3. Ejecución: cada gestor ejecuta la petición
4. Acuerdo: no es necesaria, debido al tipo de multidifusión
5. Respuesta: cada gestor manda su respuesta al frontal. El nº de respuestas que recoge el frontal depende de las asunciones de fallo y del algoritmo de multidifusión

![Caracteristicas](/sistemas-distribuidos/Examen3/images/rdp2.png)
![Caracteristicas](/sistemas-distribuidos/Examen3/images/rdp.png)

## Alta disponibilidad
La proporción de tiempo que un servicio está accesible con tiempos de respuesta razonables debe ser ~ 100%
- Factores de pérdida de disponibilidad
- Fallos en el servidor
- Si un servidor tiene una posibilidad de fallo p del 5%, tendrá disponibilidad del 95%
	- Si replicamos n veces el servidor, la disponibilidad será 1-pn 
	- Con n=2 servidores: 1 - 0.052 = 99.75%
- Particiones de red o desconexiones
- Desconexión intencionada (p. ej. BitTorrent) o no intencionada (p. ej. conexión inalámbrica viajando en bus)
![Caracteristicas](/sistemas-distribuidos/Examen3/images/disp.png)
### Convergencia
Todas las réplicas del documento tienen que ser iguales tras aplicar todas las operaciones.
### Consistencia
Las operaciones deben aplicarse en el mismo orden en todos los nodos
- Basándose en la relación ‘sucede antes que’
- No lo garantiza TO → uso de ordenación causal
#### Intención
El efecto de ejecutar una operación debe ser el mismo que el efecto buscado en la réplica local sobre la que se aplica inicialmente.

## Consenso por Quorum
#### Operación de lectura
- Recuperar un quórum de lectura (cualquier conjunto de r copias)
- De las r copias, seleccionar la copia con el n.º de versión más alto
- Retornar el valor de dicha copia
#### Operación de escritura
- Tomar un quórum de escritura (cualquier conjunto de w copias)
- De las w copias, obtener el n.º de versión más alto
- Incrementar el nº de versión
- Escribir el nuevo valor y el nuevo n.º de versión en todas las w copias del quórum de escritura
![Caracteristicas](/sistemas-distribuidos/Examen3/images/quo.webp)
## Clúster
Este tipo de sistemas se basa en la unión de varios servidores que trabajan como si de uno únicamente se tratase. Los sistemas clúster han evolucionado mucho desde su primera aparición, ahora se pueden crear distintos tipos de clústeres, en función de lo que se necesite:
- Unión de Hardware
- Clústeres de Software
- Alto rendimiento de bases de datos

![Caracteristicas](/sistemas-distribuidos/Examen3/images/cluster.png)
Estas son solo algunas de las opciones que tenemos disponibles. En resumen, cluster es un grupo de múltiples ordenadores unidos mediante una red de alta velocidad, de tal forma que el conjunto es visto como un único ordenador, más potente que los comunes de escritorio

- Alto rendimiento
- Alta disponibilidad
- Equilibrio de carga
- Escalabilidad
### Ventajas
- Relación costo/performance.
- Escalabilidad incremental.
- Escalabilidad incremental.
- Sistema “multipropósito” (no dedicado)

#### DESVENTAJAS
Ninguna, este tipo de sistemas son los más fiables, ya que para la parada total del proceso deben de pararse todas las máquinas que componen el grupo. Es la mejor solución para crecer según las necesidades reales, porque puede añadir tantas máquinas necesite.

### Qué necesita para servir
Por norma general, un clúster hace uso de diferentes componentes para funcionar, entre estos están:
- Nodos (Ordenadores o servidores)
- Sistema operativo
- Conexión de Red (ampliado más abajo)
- Middleware (capa entre el usuario y el sistema operativo)
- Protocolos de comunicación y servicio
- Aplicaciones





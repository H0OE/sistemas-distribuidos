
---
title: 🪴 Sección crítica
---
Existen múltiples características que un sistema distribuido debe de cumplir, como:
- confiabilidad
- disponibilidad
- apertura
- integridad de información

Dentro de la integridad de información, un problema relevante son las condiciones de competencia que se generan al tener recursos compartidos. Por esta razón, el tema de la **exclusión mutua** se vuelve de sumo interés. 

Este problema debe de ser resuelto para asegurar el acceso de forma correcta a los recursos compartidos, con la finalidad de mantener la integridad y consistencia en los datos.

![Caracteristicas](/sistemas-distribuidos/Examen2/images/seccion.webp)

## Deadlock
Cada proceso debe de pedir permiso para poder entrar en la región crítica y debe de liberarla después de haberla ocupado en su ejecución, para permitir, a otro proceso, entrar a la región crítica. Un algoritmo de exclusión mutua se define como el mecanismo

Para poder asegurar que solo un proceso esté en la región crítica, debe de asegurar que no existan deadlocks.

Un Deadlock (también llamado "bloqueo mutuo", "abrazo mortal", “punto muerto", etc.) sucede cuando dos o más transacciones intentan hacer bloqueos de claves en orden opuesto, por ejemplo:
![Caracteristicas](/sistemas-distribuidos/Examen2/images/deadlock.png)

## Sección crítica (sección crítica y región crítica son denominaciones equivalentes) 
En programación concurrente de ciencias de la computación, a la porción de código de un programa de ordenador en la que se accede a un recurso compartido (estructura de datos o dispositivo) que no debe ser accedido por más de un proceso o hilo en ejecución. 

La sección crítica por lo general termina en un tiempo determinado y el hilo, proceso o tarea únicamente tendrá que esperar un período determinado de tiempo para entrar. Se necesita un mecanismo de sincronización en la entrada y salida de la sección crítica para asegurar la utilización en exclusiva del recurso, por ejemplo un semáforo, monitores, el algoritmo de Dekker y Peterson, los candados.

## Requisitos 
Se denomina región crítica, (sección crítica y región crítica son denominaciones equivalentes) en programación concurrente de ciencias de la computación, a la porción de código de un programa de ordenador en la que se accede a un recurso compartido (estructura de datos o dispositivo) que no debe ser accedido por más de un proceso o hilo en ejecución.

Proceso entra a ejecutar una sección crítica en al que accede a unas variables compartidas, entonces otro proceso no puede entrar a ejecutar una sección crítica
Las secciones críticas se pueden agrupar en clases, siendo mutuamente exclusivas.

Se debe implementar protocolos de software que impidan o bloqueen en acceso a una sección crítica.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/secc3.png)
## Exclusión mutua distribuida
Dicho problema es conocido como el problema de la sección crítica en el dominio de los SO. En los sistemas distribuidos se requiere una solución que esté basada exclusivamente en el paso de mensajes.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/exclusion.png)
### Requisitos
Los requisitos esenciales para la exclusión mutua son:
- EM1 (seguridad): a lo sumo un proceso puede estar ejecutándose una vez en la sección crítica.
- EM2 (superveniencia): las peticiones para entrar y salir de la sección crítica al final deben ser concedidas. Esto implica la inexistencia de deadlocks e inanición.
- EM3 (ordenación): si una petición parar entrar en la SC ocurrió antes que otra, entonces la entrada en la SC se garantiza en ese orden.

### Mecanismos para garantizar la exclusión mutua
##### Semáforos
Método clásico para restringir o permitir el acceso a recursos compartidos (por ejemplo, un recurso de almacenamiento del sistema o variables del código fuente) en un entorno de multiprocesamiento

Un tipo simple de semáforo es el binario, que puede tomar solamente los valores 0 y 1. Se inicializan en 1 y son usados cuando solo un proceso puede acceder a un recurso a la vez

Controla los procesos dentro de memoria en el área de datos compartidos (lectura, lectura/escritura, escritura).

Trabaja con dos elementos:
- señal (despertar)
- espera (dormir)

Dependiendo del tipo de operación en el área de datos compartidos, será el semáforo que se implante.

El uso de semáforos depende del número de procesos; en áreas de datos no compartidos no tiene razón de ser.

Cuando cualquier proceso accede a los recursos compartidos, realiza la operación wait() en el semáforo y cuando el proceso libera los recursos compartidos, realiza la operación signal() en el semáforo. El semáforo no tiene variables de condición. 

Cuando un proceso está modificando el valor del semáforo, ningún otro proceso puede modificar simultáneamente el valor del semáforo.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/sem.jpg)

#### Monitores
un monitor es un programa que observa y administra los procesos dentro del CPU.

Se pueden implementar monitores en memoria en áreas de datos compartidos y no compartidos.

Un monitor contiene el código relativo a un recurso compartido en un solo módulo de programa

La interfaz del monitor es un conjunto de funciones que representan las diferentes operaciones que pueden hacerse con el recurso.

Una construcción de sincronización de alto nivel de tipo Monitor. Es un tipo de datos abstracto. El tipo Monitor contiene variables compartidas y el conjunto de procedimientos que operan en la variable compartida.

Cuando cualquier proceso desea acceder a las variables compartidas en el monitor, necesita acceder a ellas a través de los procedimientos. Estos procesos se alinean en una cola y solo se les proporciona acceso cuando el proceso anterior libera las variables compartidas. Únicamente un proceso puede estar activo en un monitor a la vez. El monitor tiene variables de condición.

##### Ventajas:
• Mantenimiento más simple
• Menos errores de programación
![Caracteristicas](/sistemas-distribuidos/Examen2/images/mon.jpg)

### Monitores vs Semaforos
#### Ventajas monitores
- Los monitores son fáciles de implementar que los semáforos.
- La exclusión mutua en los monitores es automática, mientras que en los semáforos, la exclusión mutua debe implementarse explícitamente.
- Los monitores pueden superar los errores de sincronización que se producen al utilizar semáforos.
- Las variables compartidas son globales para todos los procesos en el monitor, mientras que las variables compartidas están ocultas en semáforos.

#### Ventajas semaforos
- Los semáforos son independientes de la máquina (porque están implementados en los servicios del kernel).
- Los semáforos permiten que más de un hilo acceda a la sección crítica, a diferencia de los monitores.
- En los semáforos no hay desperdicio de recursos debido a que no hay esperas ocupadas.

### Algoritmo de Dekker
Es un algoritmo de programación concurrente para exclusión mutua, que permite a dos procesos o hilos de ejecución compartir un recurso sin conflictos si ambos procesos intentan acceder a la sección crítica simultáneamente, el algoritmo elige un proceso según una variable turno. Si el otro proceso está ejecutando en su sección crítica, deberá esperar su finalización.

Existen cinco versiones del algoritmo Dekker, teniendo ciertos fallos los primeros cuatro. **La versión 5 es la que trabaja más eficientemente, siendo una combinación de la 1 y la 4.**

1. Versión 1: Alternancia estricta. Garantiza la exclusión mutua, pero su desventaja es que acopla los procesos fuertemente, esto significa que los procesos lentos atrasan a los procesos rápidos.
2. Versión 2: Problema interbloqueo. No existe la alternancia, aunque ambos procesos caen a un mismo estado y nunca salen de ahí.
3. Versión 3: Colisión región crítica no garantiza la exclusión mutua. Este algoritmo no evita que dos procesos puedan acceder al mismo tiempo a la región crítica.
4. Versión 4: Postergación indefinida. Aunque los procesos no están en interbloqueo, un proceso o varios se quedan esperando a que suceda un evento que tal vez nunca suceda.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/dekker.png)
### Algoritmo Petterson
Algoritmo de programación concurrente para exclusión mutua, que permite a dos o más procesos o hilos de ejecución compartir un recurso sin conflictos, utilizando solo memoria compartida para la comunicación 
Cada proceso tiene un turno para entrar en la sección crítica, di desea entrar debe activar su señal y puede que tenga que esperar a que llegue su turno
- Version simplificada del algoritmo de Dekker
- El protocolo de entrada es más elegante con las mismas garantías de exclusión mutua, imposibilidad de bloqueo mutuo y de aplazamiento indefinido.
- El algoritmo de Decker resuelve el problema de la exclusión mutua pero mediante un programa complejo, difícil de seguir y cuya corrección es difícil de demostrar. Peterson ha desarrollado una solución simple y elegante. Como antes, la variable global señal indica la posición de cada proceso con respecto a la exclusión mutua y la variable global turno resuelve los conflictos de simultaneidad.


![Caracteristicas](/sistemas-distribuidos/Examen2/images/pet.png)

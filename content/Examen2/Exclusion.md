
---
title: 馃 Secci贸n cr铆tica
---
Existen m煤ltiples caracter铆sticas que un sistema distribuido debe de cumplir, como:
- confiabilidad
- disponibilidad
- apertura
- integridad de informaci贸n

Dentro de la integridad de informaci贸n, un problema relevante son las condiciones de competencia que se generan al tener recursos compartidos. Por esta raz贸n, el tema de la **exclusi贸n mutua** se vuelve de sumo inter茅s. 

Este problema debe de ser resuelto para asegurar el acceso de forma correcta a los recursos compartidos, con la finalidad de mantener la integridad y consistencia en los datos.

![Caracteristicas](/sistemas-distribuidos/Examen2/images/seccion.webp)

## Deadlock
Cada proceso debe de pedir permiso para poder entrar en la regi贸n cr铆tica y debe de liberarla despu茅s de haberla ocupado en su ejecuci贸n, para permitir, a otro proceso, entrar a la regi贸n cr铆tica. Un algoritmo de exclusi贸n mutua se define como el mecanismo

Para poder asegurar que solo un proceso est茅 en la regi贸n cr铆tica, debe de asegurar que no existan deadlocks.

Un Deadlock (tambi茅n llamado "bloqueo mutuo", "abrazo mortal", 鈥減unto muerto", etc.) sucede cuando dos o m谩s transacciones intentan hacer bloqueos de claves en orden opuesto, por ejemplo:
![Caracteristicas](/sistemas-distribuidos/Examen2/images/deadlock.png)

## Secci贸n cr铆tica (secci贸n cr铆tica y regi贸n cr铆tica son denominaciones equivalentes) 
En programaci贸n concurrente de ciencias de la computaci贸n, a la porci贸n de c贸digo de un programa de ordenador en la que se accede a un recurso compartido (estructura de datos o dispositivo) que no debe ser accedido por m谩s de un proceso o hilo en ejecuci贸n. 

La secci贸n cr铆tica por lo general termina en un tiempo determinado y el hilo, proceso o tarea 煤nicamente tendr谩 que esperar un per铆odo determinado de tiempo para entrar. Se necesita un mecanismo de sincronizaci贸n en la entrada y salida de la secci贸n cr铆tica para asegurar la utilizaci贸n en exclusiva del recurso, por ejemplo un sem谩foro, monitores, el algoritmo de Dekker y Peterson, los candados.

## Requisitos 
Se denomina regi贸n cr铆tica, (secci贸n cr铆tica y regi贸n cr铆tica son denominaciones equivalentes) en programaci贸n concurrente de ciencias de la computaci贸n, a la porci贸n de c贸digo de un programa de ordenador en la que se accede a un recurso compartido (estructura de datos o dispositivo) que no debe ser accedido por m谩s de un proceso o hilo en ejecuci贸n.

Proceso entra a ejecutar una secci贸n cr铆tica en al que accede a unas variables compartidas, entonces otro proceso no puede entrar a ejecutar una secci贸n cr铆tica
Las secciones cr铆ticas se pueden agrupar en clases, siendo mutuamente exclusivas.

Se debe implementar protocolos de software que impidan o bloqueen en acceso a una secci贸n cr铆tica.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/secc3.png)
## Exclusi贸n mutua distribuida
Dicho problema es conocido como el problema de la secci贸n cr铆tica en el dominio de los SO. En los sistemas distribuidos se requiere una soluci贸n que est茅 basada exclusivamente en el paso de mensajes.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/exclusion.png)
### Requisitos
Los requisitos esenciales para la exclusi贸n mutua son:
- EM1 (seguridad): a lo sumo un proceso puede estar ejecut谩ndose una vez en la secci贸n cr铆tica.
- EM2 (superveniencia): las peticiones para entrar y salir de la secci贸n cr铆tica al final deben ser concedidas. Esto implica la inexistencia de deadlocks e inanici贸n.
- EM3 (ordenaci贸n): si una petici贸n parar entrar en la SC ocurri贸 antes que otra, entonces la entrada en la SC se garantiza en ese orden.

### Mecanismos para garantizar la exclusi贸n mutua
##### Sem谩foros
M茅todo cl谩sico para restringir o permitir el acceso a recursos compartidos (por ejemplo, un recurso de almacenamiento del sistema o variables del c贸digo fuente) en un entorno de multiprocesamiento

Un tipo simple de sem谩foro es el binario, que puede tomar solamente los valores 0 y 1. Se inicializan en 1 y son usados cuando solo un proceso puede acceder a un recurso a la vez

Controla los procesos dentro de memoria en el 谩rea de datos compartidos (lectura, lectura/escritura, escritura).

Trabaja con dos elementos:
- se帽al (despertar)
- espera (dormir)

Dependiendo del tipo de operaci贸n en el 谩rea de datos compartidos, ser谩 el sem谩foro que se implante.

El uso de sem谩foros depende del n煤mero de procesos; en 谩reas de datos no compartidos no tiene raz贸n de ser.

Cuando cualquier proceso accede a los recursos compartidos, realiza la operaci贸n wait() en el sem谩foro y cuando el proceso libera los recursos compartidos, realiza la operaci贸n signal() en el sem谩foro. El sem谩foro no tiene variables de condici贸n. 

Cuando un proceso est谩 modificando el valor del sem谩foro, ning煤n otro proceso puede modificar simult谩neamente el valor del sem谩foro.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/sem.jpg)

#### Monitores
un monitor es un programa que observa y administra los procesos dentro del CPU.

Se pueden implementar monitores en memoria en 谩reas de datos compartidos y no compartidos.

Un monitor contiene el c贸digo relativo a un recurso compartido en un solo m贸dulo de programa

La interfaz del monitor es un conjunto de funciones que representan las diferentes operaciones que pueden hacerse con el recurso.

Una construcci贸n de sincronizaci贸n de alto nivel de tipo Monitor. Es un tipo de datos abstracto. El tipo Monitor contiene variables compartidas y el conjunto de procedimientos que operan en la variable compartida.

Cuando cualquier proceso desea acceder a las variables compartidas en el monitor, necesita acceder a ellas a trav茅s de los procedimientos. Estos procesos se alinean en una cola y solo se les proporciona acceso cuando el proceso anterior libera las variables compartidas. 脷nicamente un proceso puede estar activo en un monitor a la vez. El monitor tiene variables de condici贸n.

##### Ventajas:
鈥? Mantenimiento m谩s simple
鈥? Menos errores de programaci贸n
![Caracteristicas](/sistemas-distribuidos/Examen2/images/mon.jpg)

### Monitores vs Semaforos
#### Ventajas monitores
- Los monitores son f谩ciles de implementar que los sem谩foros.
- La exclusi贸n mutua en los monitores es autom谩tica, mientras que en los sem谩foros, la exclusi贸n mutua debe implementarse expl铆citamente.
- Los monitores pueden superar los errores de sincronizaci贸n que se producen al utilizar sem谩foros.
- Las variables compartidas son globales para todos los procesos en el monitor, mientras que las variables compartidas est谩n ocultas en sem谩foros.

#### Ventajas semaforos
- Los sem谩foros son independientes de la m谩quina (porque est谩n implementados en los servicios del kernel).
- Los sem谩foros permiten que m谩s de un hilo acceda a la secci贸n cr铆tica, a diferencia de los monitores.
- En los sem谩foros no hay desperdicio de recursos debido a que no hay esperas ocupadas.

### Algoritmo de Dekker
Es un algoritmo de programaci贸n concurrente para exclusi贸n mutua, que permite a dos procesos o hilos de ejecuci贸n compartir un recurso sin conflictos si ambos procesos intentan acceder a la secci贸n cr铆tica simult谩neamente, el algoritmo elige un proceso seg煤n una variable turno. Si el otro proceso est谩 ejecutando en su secci贸n cr铆tica, deber谩 esperar su finalizaci贸n.

Existen cinco versiones del algoritmo Dekker, teniendo ciertos fallos los primeros cuatro. **La versi贸n 5 es la que trabaja m谩s eficientemente, siendo una combinaci贸n de la 1 y la 4.**

1. Versi贸n 1: Alternancia estricta. Garantiza la exclusi贸n mutua, pero su desventaja es que acopla los procesos fuertemente, esto significa que los procesos lentos atrasan a los procesos r谩pidos.
2. Versi贸n 2: Problema interbloqueo. No existe la alternancia, aunque ambos procesos caen a un mismo estado y nunca salen de ah铆.
3. Versi贸n 3: Colisi贸n regi贸n cr铆tica no garantiza la exclusi贸n mutua. Este algoritmo no evita que dos procesos puedan acceder al mismo tiempo a la regi贸n cr铆tica.
4. Versi贸n 4: Postergaci贸n indefinida. Aunque los procesos no est谩n en interbloqueo, un proceso o varios se quedan esperando a que suceda un evento que tal vez nunca suceda.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/dekker.png)
### Algoritmo Petterson
Algoritmo de programaci贸n concurrente para exclusi贸n mutua, que permite a dos o m谩s procesos o hilos de ejecuci贸n compartir un recurso sin conflictos, utilizando solo memoria compartida para la comunicaci贸n 
Cada proceso tiene un turno para entrar en la secci贸n cr铆tica, di desea entrar debe activar su se帽al y puede que tenga que esperar a que llegue su turno
- Version simplificada del algoritmo de Dekker
- El protocolo de entrada es m谩s elegante con las mismas garant铆as de exclusi贸n mutua, imposibilidad de bloqueo mutuo y de aplazamiento indefinido.
- El algoritmo de Decker resuelve el problema de la exclusi贸n mutua pero mediante un programa complejo, dif铆cil de seguir y cuya correcci贸n es dif铆cil de demostrar. Peterson ha desarrollado una soluci贸n simple y elegante. Como antes, la variable global se帽al indica la posici贸n de cada proceso con respecto a la exclusi贸n mutua y la variable global turno resuelve los conflictos de simultaneidad.


![Caracteristicas](/sistemas-distribuidos/Examen2/images/pet.png)

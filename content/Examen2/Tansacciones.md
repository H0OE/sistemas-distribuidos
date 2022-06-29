---
title: 💸 Transacciones
banner_icon: 💸
---

Una transacción es la ejecución consistente y confiable de un conjunto de operaciones agrupadas como una unidad que acceden a una base de datos compartida

Una transacción es una secuencia de una o más operaciones agrupadas como una unidad

## Operaciones atómicas
Las operaciones atómicas en programación concurrente son operaciones de programa que se ejecutan de forma completamente independiente de cualquier otro proceso.

Las operaciones atómicas se utilizan a menudo en el kernel, el componente principal de la mayoría de los sistemas operativos. Sin embargo, la mayor parte del hardware, los compiladores y las bibliotecas de las computadoras también proporcionan distintos niveles de operaciones atómicas.
    
-   Se dice que una operación es atómica cuando se completa de principio a fin sin interrupciones.

-   Java garantiza que son atómicos los accesos a las variables de tipos primitivos, excepto double y long

Las operaciones que contiene una transacción se van almacenando temporalmente, no a nivel de disco. Es hasta que termina la transacción que se tienen efecto de manera permanente o no

En algunas situaciones, el cliente necesita que una secuencia de solicitudes al servidor se ejecuten de manera atómica:

- Libres de interferencia por operaciones de otros clientes
- Todas las operaciones se deben completar con éxito o no tener ningún efecto si el servidor falla.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/tra.jpg)
### Características
- El manejo de transacciones puede venir como parte del middleware que proporciona la especificación para un servicio de transacciones sobre objetos.
- Una transacción aplica a datos recuperables, puede estar formada por operaciones simples o compuestas y su intención es que sea atómica.
- Hay dos aspectos que se deben cumplir para lograr la atomicidad: todo-o-nada, aislamiento.
- Una transacción siempre termina, aun en la presencia de fallas. Si una transacción termina de manera exitosa se dice que la transacción hace un commit.
- Cuando la transacción es abortada, su ejecución se detiene y todas las acciones ejecutadas hasta el momento se deshacen (undone) regresando a la base de datos al estado antes de su ejecución. **rollback**

## Propiedades de las transacciones ACID
1. Atomicidad **atomicity**
2. Consistencia **consistency**
3. Aislamiento **isolation**
4. Durabilidad **durability**
![Caracteristicas](/sistemas-distribuidos/Examen2/images/acid.jpg)
### Atomicidad
Aseguran que todas las operaciones dentro de la secuencia de trabajo se completen satisfactoriamente. Si no es así, la transacción se abandona en el punto del error y las operaciones previas retroceden a su estado inicial.
**TODO O NADA**

### Consistencia
Aseguran que la base de datos cambie estados en una transacción exitosa.

#### Aislamiento
Permiten que las operaciones sean aisladas y transparentes unas de otras. **Sin interferencias**

### Durabilidad
Una vez que una transacción se completa correctamente, sus efectos no se pueden modificar sin ejecutar una transacción de compensación. Los cambios realizados por una transacción correcta sobreviven a posteriores anomalías del sistema.

## Tipos
![Caracteristicas](/sistemas-distribuidos/Examen2/images/tras.jpg)
### Planas
Estas transacciones tienen un punto de partida simple **Begin** y **End**

### Anidadas
- Las operaciones de una transacción anidada pueden incluir otras transacciones.

- Una transacción anidada dentro de otra transacción conserva las mismas propiedades que la de sus padres, esto implica, que puede contener así mismo transacciones dentro de ella.
#### Restricciones de las anidadas
- Debe empezar después que su padre y debe terminar antes que él.
- El commit de una transacción padre está condicionada al commit de sus transacciones hijas
- Si alguna transacción hija aborta (rollback), la transacción padre también será abortada (rollback).
## Bitácora
- Es un archivo que permite deshacer las operaciones realizadas sobre una o varias bases de datos en caso de que falle la transacción.
- Esto se hace con el fin de mantener la integridad de la información y que la transacción sea atómica

## Seguridad en transacciones
1. Autenticación: asegura la identidad del servidor participante en la comunicación.
2. Confidencialidad: asegura que la información transmitida en la comunicación entre el cliente y el servidor sólo sea legible por estas dos entidades.
3. Integridad: asegura que la información transmitida en la comunicación entre el cliente y el servidor no haya sido alterada en su viaje por la red

SSL – SECURE SOCKET LAYER
SET – SECURE ELECTRONIC TRANSACTION 
	Es un sistema que garantiza la seguridad e integridad 
     de las transacciones electrónicas realizadas en un escenario. 
     SET no es un sistema que permita el pago, pero es un protocolo de seguridad aplicado a esos pagos. Utiliza diferentes técnicas de encriptación y hash para asegurar los pagos a través de Internet a través de tarjetas de crédito. Este protocolo fue apoyado en el desarrollo por las principales organizaciones como Visa, Mastercard.

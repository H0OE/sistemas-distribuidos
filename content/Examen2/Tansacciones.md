---
title: 馃捀 Transacciones
banner_icon: 馃捀
---

Una transacci贸n es la ejecuci贸n consistente y confiable de un conjunto de operaciones agrupadas como una unidad que acceden a una base de datos compartida

Una transacci贸n es una secuencia de una o m谩s operaciones agrupadas como una unidad

## Operaciones at贸micas
Las operaciones at贸micas en programaci贸n concurrente son operaciones de programa que se ejecutan de forma completamente independiente de cualquier otro proceso.

Las operaciones at贸micas se utilizan a menudo en el kernel, el componente principal de la mayor铆a de los sistemas operativos. Sin embargo, la mayor parte del hardware, los compiladores y las bibliotecas de las computadoras tambi茅n proporcionan distintos niveles de operaciones at贸micas.
    
-   Se dice que una operaci贸n es at贸mica cuando se completa de principio a fin sin interrupciones.

-   Java garantiza que son at贸micos los accesos a las variables de tipos primitivos, excepto double y long

Las operaciones que contiene una transacci贸n se van almacenando temporalmente, no a nivel de disco. Es hasta que termina la transacci贸n que se tienen efecto de manera permanente o no

En algunas situaciones, el cliente necesita que una secuencia de solicitudes al servidor se ejecuten de manera at贸mica:

- Libres de interferencia por operaciones de otros clientes
- Todas las operaciones se deben completar con 茅xito o no tener ning煤n efecto si el servidor falla.
![Caracteristicas](/sistemas-distribuidos/Examen2/images/tra.jpg)
### Caracter铆sticas
- El manejo de transacciones puede venir como parte del middleware que proporciona la especificaci贸n para un servicio de transacciones sobre objetos.
- Una transacci贸n aplica a datos recuperables, puede estar formada por operaciones simples o compuestas y su intenci贸n es que sea at贸mica.
- Hay dos aspectos que se deben cumplir para lograr la atomicidad: todo-o-nada, aislamiento.
- Una transacci贸n siempre termina, aun en la presencia de fallas. Si una transacci贸n termina de manera exitosa se dice que la transacci贸n hace un commit.
- Cuando la transacci贸n es abortada, su ejecuci贸n se detiene y todas las acciones ejecutadas hasta el momento se deshacen (undone) regresando a la base de datos al estado antes de su ejecuci贸n. **rollback**

## Propiedades de las transacciones ACID
1. Atomicidad **atomicity**
2. Consistencia **consistency**
3. Aislamiento **isolation**
4. Durabilidad **durability**
![Caracteristicas](/sistemas-distribuidos/Examen2/images/acid.jpg)
### Atomicidad
Aseguran que todas las operaciones dentro de la secuencia de trabajo se completen satisfactoriamente. Si no es as铆, la transacci贸n se abandona en el punto del error y las operaciones previas retroceden a su estado inicial.
**TODO O NADA**

### Consistencia
Aseguran que la base de datos cambie estados en una transacci贸n exitosa.

#### Aislamiento
Permiten que las operaciones sean aisladas y transparentes unas de otras. **Sin interferencias**

### Durabilidad
Una vez que una transacci贸n se completa correctamente, sus efectos no se pueden modificar sin ejecutar una transacci贸n de compensaci贸n. Los cambios realizados por una transacci贸n correcta sobreviven a posteriores anomal铆as del sistema.

## Tipos
![Caracteristicas](/sistemas-distribuidos/Examen2/images/tras.jpg)
### Planas
Estas transacciones tienen un punto de partida simple **Begin** y **End**

### Anidadas
- Las operaciones de una transacci贸n anidada pueden incluir otras transacciones.

- Una transacci贸n anidada dentro de otra transacci贸n conserva las mismas propiedades que la de sus padres, esto implica, que puede contener as铆 mismo transacciones dentro de ella.
#### Restricciones de las anidadas
- Debe empezar despu茅s que su padre y debe terminar antes que 茅l.
- El commit de una transacci贸n padre est谩 condicionada al commit de sus transacciones hijas
- Si alguna transacci贸n hija aborta (rollback), la transacci贸n padre tambi茅n ser谩 abortada (rollback).
## Bit谩cora
- Es un archivo que permite deshacer las operaciones realizadas sobre una o varias bases de datos en caso de que falle la transacci贸n.
- Esto se hace con el fin de mantener la integridad de la informaci贸n y que la transacci贸n sea at贸mica

## Seguridad en transacciones
1. Autenticaci贸n: asegura la identidad del servidor participante en la comunicaci贸n.
2. Confidencialidad: asegura que la informaci贸n transmitida en la comunicaci贸n entre el cliente y el servidor s贸lo sea legible por estas dos entidades.
3. Integridad: asegura que la informaci贸n transmitida en la comunicaci贸n entre el cliente y el servidor no haya sido alterada en su viaje por la red

SSL 鈥? SECURE SOCKET LAYER
SET 鈥? SECURE ELECTRONIC TRANSACTION 
	Es un sistema que garantiza la seguridad e integridad 
     de las transacciones electr贸nicas realizadas en un escenario. 
     SET no es un sistema que permita el pago, pero es un protocolo de seguridad aplicado a esos pagos. Utiliza diferentes t茅cnicas de encriptaci贸n y hash para asegurar los pagos a trav茅s de Internet a trav茅s de tarjetas de cr茅dito. Este protocolo fue apoyado en el desarrollo por las principales organizaciones como Visa, Mastercard.

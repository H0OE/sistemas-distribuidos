---
title: 🪴 "Teorema CAP"
---
El Teorema CAP indica que los sistema distribuido de almacenamiento de datos pueden llegar a ser vulnerables a fallos por conectividad en la red, es por esto que indica que estos sistemas solo pueden llegar a tener dos de los tres siguientes atributos:
-   Consistencia: Este atributo quiere decir que sin importar el lugar o la instancia del servicio que se esté usando, este siempre tiene que ser el mismo, por ejemplo las bases de datos SQL quieren lograr esto por lo que existe diferentes métodos y restricciones para lograrlo, en MYSQL existen las transacciones que garantiza esto y también el comando LOCK TABLE para evitar que otro usuario lea esta base de datos mientras otro la escribe, con el fin de evitar lecturas sucias.
-   Disponibilidad: Esto quiere decir que la respuesta será válida y se deberá dar en un tiempo razonable, es decir que no tarde más de lo debido. Esto es importante si lo que se quiere es obtener los datos de manera rápida y garantizar que se obtendrán como es el caso de las bases de datos SQL.
-   Tolerancia a particiones: Esto quiere decir que el sistema debe permanecer estable aun cuando algunos nodos no se encuentren disponibles, ya que se supone que el resto de los nodos tienen la información de manera consistente.
    

Ahora como se mencionó anteriormente este teorema dice que solo se puede garantizar dos de estos tres atributos creando combinaciones entre ellos, por ejemplo tener Consistencia y disponibilidad como es el caso de las bases de datos SQL, tener disponibilidad y tolerancia a particiones o tener consistencia y tolerancia a particiones.

Ejemplos:

- CA : MySQL, Postgres, Aster Data, Greenpium, Vertica.

- AP: SimpleDB, CouchDB, Cassandra, Riak, Dynamo, [Voldemort](https://www.project-voldemort.com/voldemort/)

- CP: MongoDB, Terrastore, Scalaris, Berkeley DB, MemcacheDB.

# Arquitecturas
## Modelos Arquitectónicos En Sistemas Distribuidos 
Un modelo arquitectónico puede ser definido como un prototipo o representación de la estructura de un sistema, construido con el fin de estudiar distintos aspectos en torno al mismo, como pueden ser el diseño o la eficiencia. 

Los tipos de modelos arquitectónicos se diferencian en 
- El reparto de responsabilidades entre componentes del sistema
- La ubicación de los componentes del sistema 
Tipos de modelos 
- Cliente-servidor 
- Servicios proporcionados por múltiples servidores 
- Servidores proxy y cachés
- Otros derivados
- Sistemas de igual a igual (peer to peer)

## Arquitectura De Software 
El término arquitectura de software puede ser definido como aquella organización lógica que se enfoca en los componentes de software y como estos interactúan con otras estructuras.

### Clasificación 
Una vez entendiendo dicho término es que se puede hablar de los siguientes modelos: 
#### Modelo Arquitectónico En Capas
Como su nombre indica, este modelo proporciona un enfoque modular al software, es decir, separa cada componente con el fin de ser más eficiente; de esta manera, se crea un orden en la secuencia de pasos y cuando se realiza una modificación a una capa de manera independiente no se afecta al resto del sistema.

Para dejar la idea un poco más clara, un ejemplo que se puede dar de este tipo de arquitectura es el modelo OSI (modelo de interconexión de sistemas abiertos) el cual utiliza este modelo para obtener mejores resultados. 

#### Modelo Arquitectónico Basado En Objetos
El modelo basado en objetos se basa en la idea de tener una cierta disposición de objetos que se encuentran débilmente acoplados y sin una arquitectura fija. A diferencia del anterior modelo no existe una secuencia de pasos a seguir, en cambio, la interacción está dada a través de un conector o interfaz donde cada objeto puede interactuar con otro a través de la llamada de uno o varios métodos.

Ejemplo de este tipo de modelo arquitectónico son los sistemas de navegación y ayuda a la gestión de transportes, donde distintos componentes (objetos) interactúan entre sí.

#### Modelo Arquitectónico Centrado En Datos
Este modelo de arquitectura funciona en base a un repositorio de datos central, tal y como indica su nombre, desde el cual se pueden ingresar y solicitar datos. 

Un ejemplo simple de este tipo de modelo es el de un almacén de productos el cual “ingresa y actualiza” datos cuando recibe nuevos productos los cuales pueden ser a su vez solicitados por sus clientes.

#### Modelo Arquitectónico Basado En Eventos
Al igual que en los casos anteriores el nombre de esta arquitectura resume de buena manera su funcionamiento, el cual está dado a través de eventos; es decir, cuando ocurre un evento el sistema suscrito recibe una notificación y actúa en consecuencia a la misma. 

Una de las ventajas y principales diferencias con los anteriores modelos explicados es que los componentes de este modelo están acoplados de manera flexible, lo que facilita el modificarlos, agregarlos o eliminarlos. Ejemplo de este modelo es Facebook, debido a las características antes mencionadas.
## Arquitetura del sistema
Este concepto puede ser definido como aquella arquitectura que se basa en el sistema en si y en la ubicación de todos los componentes del mismo. Teniendo como punto el de un sistema distribuido, se puede decir que los modelos arquitectónicos que más relevancia tienen en este ámbito son dos.

### Modelo Arquitectónico Cliente-Servidor (Centralizadas)
Este modelo, como su nombre indica consta de un cliente y un servidor. El servidor es donde se encuentran todos los procesos y el cliente es donde el usuario interactúa con dicho servidor; en ese sentido si el cliente solicita algo al servidor, este le responderá. Este es un modelo que es más estable y seguro que el modelo punto a punto, pero es más lento que el mismo. El ejemplo más grande que se puede dar de un sistema de este tipo es de la World Wide Web, donde se utiliza un programa (navegador) como cliente

### Modelo Arquitectónico Punto A Punto (Descentralizadas)
También llamado peer-to-peer o P2P, este modelo funciona teniendo como base la falta de un control central en un sistema distribuido; es decir, un nodo puede actuar como cliente o como servidor en cualquier momento; si el nodo hace una solicitud es tratado como un cliente y si por el contrario proporciona algo en respuesta a una solicitud se lo trata como el servidor. Existen tres tipos de Modelos P2P, el modelo estructurado, el no estructurado y el híbrido. Ejemplo de esto son los servicios de telefonía por Internet.

### Hibiridas
Mezcla de las 2

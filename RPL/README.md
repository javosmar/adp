Autor: Ing. Martin Acosta - 2020
# Trabajo Práctico RPL - ADP - CEIoT - FIUBA
## Introducción 🚀
El protocolo RPL es un protocolo de enrutamiento para redes LLNs (Low-Power & Lossy Networks) las cuales son susceptibles a la pérdida de paquetes. Se trata de un protocolo proactivo y opera sobre la norma IEEE 802.15.4, optimizado para multisalto y soporta comunicación muchos-uno, uno-muchos y uno-uno.
Es un protocolo que resulta de grán utilidad para la comunicación de dispositivos IoT.
## Descripción 📋
El siguiente trabajo práctico corresponde a la asignatura Arquitectura de Protocolos, dictada en la Carrera de Especialización en Internet de las Cosas de la Facultad de Ingeniería de la Universidad de Buenos Aires.

La simulación se realizó utilizando el simulador [Cooja](https://github.com/contiki-os/contiki/wiki/An-Introduction-to-Cooja), corriendo sobre el sistema operativo [Contiki](https://github.com/contiki-os/contiki).
## Desarrollo 📃
### 1. Identifique los mensajes de RPL. ¿cuántos tipos de mensaje puede diferenciar? Enumérelos.
```sh
En la captura se aprecian 4 tipos de mensajes RPL, los cuales son:
    a) Destination Advertisement Object (DAO)
    b) Destination Advertisement Object Acknowledgement (DAO-ACK)
    c) DODAG Informatino Solicitation (DIS)
    d) DODAG Information Object (DIO)
Estos mensajes se identifican por el campo 'Code' de los mensajes de control de RPL.
Los códigos para estos mensajes son:
```
Códigos de identificación de tipo de mensajes RPL
| DAO | DAO-ACK  | DIS  | DIO  |
| ------- | --- | --- | --- |
| 0x00 | 0x01 | 0x02 | 0x03 |
### 2. ¿Cuál es la dirección de destino de los mensajes? ¿Qué clase de dirección es?
```sh
Las direcciones de destino de los mensajes son:
    DAO -> La dirección IPv6 del nodo raiz, ya que el modo de operación está establecido en Non-Storing. Esto es que todos los mensajes pasan por el nodo raiz del DODAG. Es una dirección unicast.
    DAO-ACK -> La dirección del nodo que solicitó el mensaje DAO. Es una dirección unicast.
    DIS -> Es la dirección del grupo de multicast de RPL para los routers cercanos.
    DIO -> La dirección del grupo de multicast de RPL y las direcciones de los nodos que enviaron el mensaje DIS
```
Ejemplos de direcciones IPv6 de destino de los mensajes RPL
| DAO | DAO-ACK  | DIS  | DIO  |
| ------- | --- | --- | --- |
| ::201:1:1:1 | ::202:2:2:2	| ff02::1a | fe80::206:6:6:6 |

### 3. ¿Mediante qué protocolo de IPv6 se establece el DODAG?
```sh
Para establecer el DODAG se utiliza el protocolo RPL, los cuales son mensajes ICMPv6.
```
### 4. ¿Cómo lo identifica?
```sh
La identificación de los mensajes está dada por el campo de código, dentro de la trama de los mensajes de control RPL.
```
### 5. ¿Qué valor tiene el DODAGID en los mensajes RPL? ¿Con qué lo relaciona?
```sh
El valor del DODAGID es fd00::201:1:1:1, el cual corresponde a la dirección IPv6 del nodo raiz del DODAG.
```
### 6. Ubique los mensajes UDP del nodo 2 al nodo 1. ¿A qué puerto están dirigidos?
```sh
Los mensajes UDP del nodo 2 al nodo 1 están dirigidos al puerto 5678.
```
### 7. ¿Qué tipo de dirección es?
```sh
La dirección de destino de los mensajes UDP enviados por el nodo 2 al nodo 1 se trata de una dirección unicast, ya que es la dirección del nodo de destino.
```
### 8. En Wireshark identifique los primeros mensajes originados en el nodo 1 (se puede establecer un filtro haciendo click con el botón derecho sobre el campo que se va a usar como filtro y seleccionado “Apply as filter” – por ejemplo “ipv6.src == fe80::c30c:0:0:1”). ¿Qué tipo de mensaje es?
```sh
Los mensajes enviados por el nodo 1 son mensajes de tipo DIO (DODAG Information Object), los cuales contienen información que permite a los nodos descubrir instancias RPL, aprender los parámetros de configuración del DODAG, seleccionar un conjunto de padres y mantener el la integridad del DODAG.
```
### 9. ¿Cuál es la dirección de destino?
```sh
La dirección de destino es la ff02::1a, la cual es la dirección del grupo de multicast de RPL para todos los routers del DODAG.
```
### 10. ¿Cómo identifica que es un mensaje RPL?
```sh
La identificación del mensaje RPL está determinada por el campo de tipo al inicio de la trama. El valor de este campo es 155, lo que indica que se trata de un mensaje RPL.
```
## Contribuir 🖇️
Para contribuir realizar un pull request con las sugerencias.
## Licencia 📄
GPL

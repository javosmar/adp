Autor: Ing. Martin Acosta - 2020
# Trabajo Práctico RPL Border Router - ADP - CESIoT - FIUBA
## Introducción 🚀
El protocolo RPL es un protocolo de enrutamiento para redes LLNs (Low-Power & Lossy Networks) las cuales son susceptibles a la pérdida de paquetes. Se trata de un protocolo proactivo y opera sobre la norma IEEE 802.15.4, optimizado para multisalto y soporta comunicación muchos-uno, uno-muchos y uno-uno.
Es un protocolo que resulta de grán utilidad para la comunicación de dispositivos IoT.
## Descripción 📋
El siguiente trabajo práctico corresponde a la asignatura Arquitectura de Protocolos, dictada en la Carrera de Especialización en Internet de las Cosas de la Facultad de Ingeniería de la Universidad de Buenos Aires.

La simulación se realizó utilizando el simulador [Cooja](https://github.com/contiki-os/contiki/wiki/An-Introduction-to-Cooja), corriendo sobre el sistema operativo [Contiki](https://github.com/contiki-os/contiki).
## Desarrollo 📃
### Topología utilizada
![dao rpl](https://i.ibb.co/hCwCN0J/topologia.png)

### 1. Identifique los mensajes de RPL. ¿cuántos tipos de mensaje puede diferenciar? Enumérelos.
```sh
En la captura se aprecian 4 tipos de mensajes RPL, los cuales son:
    a) Destination Advertisement Object (DAO)
```
![dao rpl](https://i.ibb.co/C2VCs3K/dao.png)
```sh
    b) Destination Advertisement Object Acknowledgement (DAO-ACK)
```
![dao-ack rpl](https://i.ibb.co/cT5TFyK/dao-ack.png)
```sh
    c) DODAG Informatino Solicitation (DIS)
```
![dis rpl](https://i.ibb.co/ssRtJbb/dis.png)
```sh
    d) DODAG Information Object (DIO)
```
![dio rpl](https://i.ibb.co/GQpWDTr/dio.png)
```sh
Estos mensajes se identifican por el campo 'Code' de los mensajes de control de RPL.
Los códigos para estos mensajes son:
```
Códigos de identificación de tipo de mensajes RPL
| DIS | DIO  | DAO  | DAO-ACK  |
| ------- | --- | --- | --- |
| 0x00 | 0x01 | 0x02 | 0x03 |
### 2. ¿Mediante qué protocolo de IPv6 se establece el DODAG?
```sh
Para establecer el DODAG se utiliza el protocolo ICMPv6, dentro del cual el código 155 identifica a RPL.
```
### 3. ¿Cómo lo identifica?
```sh
La identificación de los mensajes está dada por el campo de código, dentro de la trama de los mensajes de control RPL.
```
### 4. ¿Qué valor tiene el DODAGID en los mensajes RPL? ¿Con qué lo relaciona?
```sh
El valor del DODAGID es aaaa::201:1:1:1, el cual corresponde a la dirección IPv6 del nodo raiz del DODAG establecida en la consigna.
```
## Contribuir 🖇️
Para contribuir realizar un pull request con las sugerencias.
## Licencia 📄
GPL
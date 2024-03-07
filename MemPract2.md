# Practica 2<span style="float: right; font-size: medium;">[Anterior practica](MemPract1.md) | [Siguiente practica](MemPract3.md)
</span>

- [3.1](#3.1)
- [3.2](#3.2)

## 3.1 <a id="3.1">

**a), b), c), d) y e)**

Mirar apuntes de la [practica 1](MemPract1.md)

**Importante**  
- La primera IP (la .0) es la que identifica la red, no usarla
- La segunda IP (la .1) deberia de ser el gateway, por lo que tampoco se deberia de usar, solo para esto
- La ultima IP es la direccion de broadcast, por lo que tampoco se usa
- Con esto, empieza a nombrar a los PC con IPs del .2 en adelante

**f)**  

Lo primero que hay que hacer es abrir el puerto de la interfaz 

    interface F0/0
    no shutdown

Lo siguiente habria que hacerlo con las 2 vlans, entramos a la subinterfaz, creamos el encapsulation de la vlan y fijamos su IP de salida (Gateway), la primera, en nuestro caso la 1 con su mascara. Lo siguiente es un ejemplo con la vlan 2s:

    interface F0/0.2
    encapsulation dotlq 2
    ip address 192.168.1.1 255.255.255.0

**g)**

Fijamos la IP de Gateway a cada uno de los PCs

**h)**

Hacer ping entre dos ordenadores de distinta vlan

**i)**

Guardar la configuracion con el comando ``wr``

## 3.2 <a id="3.2">

**a)**

Colocamos los switchs y los PCs y fiamos las IPs

**b)**

Entramos a la interfaz del router hacia el sitch desde el modo de configuracion, abrimos el puerto y fijamos el IP de Gateway:

    interface F0/0
    no shutdown
    ip address 192.168.3.1 255.255.255.0

Fijamos este Gateway a los PCs

**c) y d)**

Hacemos los mismos pasos que en a) y b) pero para la nueva red

**e)**

Conectamos ambos ruters y fijamos la IP como antes lo unico que en el otro puerto:

    interfac F0/1
    no shutdown
    ip address 192.168.5.2 255.255.255.0

Hacemos lo mismo pero con otra ip en el otro router

**f)**

Fijamos las rutas estaticas con ``ip route`` ip destino, mascara destino y ip de puerto de destino en el primer router

    ip route 192.168.4.0 255.255.255.0 192.168.5.3

Y ahora en el segundo router

    ip route 192.168.3.0 255.255.255.0 192.168.5.2

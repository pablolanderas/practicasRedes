# Practica 3<span style="float: right; font-size: medium;">[Anterior practica](MemPract2.md) | [Siguiente practica](MemPract4.md)
</span>

- [3.1](#3.1)
- [3.2](#3.2)
- [3.3](#3.3)

## 3.1 <a id="3.1">

**a)**

Lo siguiente es una plantilla para poder realizar correctamente la tabla:

| Subred | #Host | Bits host | Dir totales | Dir red | Dir broadcast | Mascara |
|:------:|:-----:|:---------:|:-----------:|:-------:|:-------------:|:-------:|
| El nombre de la subred | El numero de elementos de la subred | El numero necesario de bits para alacenar todos los host. Hay que tener en cuenta que al numero de hosts hay que sumarle la direccion de identificador de la red, la direccion de Broadcast, y en caso de haber, la direccion de GateWay | El numero de direcciones totales de la red siendo n el numero de bits por host se calcula de la siguiente manera: $$2^n$$ | La primera direcccion de la red | La ultima direccion de la red |  Empieza con 255.255.255. y el  ultimo elemento se calcula de la siguiente manera sinendo n el numero de bits del host: $$2^{32-n}$$


**b)**

Crear la estrucutura con los 4 routers, 2 switch a cada router inferior, un total de 6 switches y 2 PCs por switch, 6 PCs en tontal, uno por cada subred

Ahora por cada salida de los routers de abajo creamos una nueva red como en la practica anterior con su GateWay ([Practica 2 3.2 b)](MemPract2.md#3.2b)). Tambien creamos las 4 subredes que conectan los switches entre ellos ([Practica 2 3.2 e)](MemPract2.md#3.2e)). Seguido configuramos los PCs, cada uno en una de las subredes y les fijamos los GateWay

## 3.2 <a id="3.2">

**c)**

Sacamos la tabla de rutas como indica la practica

**d)**

Habilitamos ``RIPv2`` en todos los routers con los siguientes comandos para anunciar la red

    router RIP
    version 2
    network 192.168.1.0

**e)**

Vemos que las tablas de rutas han cambiado

**f)**

Hacemos un ping al ser posible desde una esquina a la otra para comprobar que funciona correctamente

**g)**

Al desconectar uno de los cables que unen al ruter inferior central, como sigue habiendo camino posible hacia el otro lado, tras esperar unos segundos a que se actualicen las tablas, el ping volvera a funcionar

**h)**

Al hacer eso, las tablas no se actualizan, por lo que no se podria realizar el ping

## 3.3 <a id="3.3">

**i)** <a id="3.3i">

Para hacer esto hay que crear una ruta estatica. Estas son las ultimas que se comrpueban, entonces lo que hay que hacer es una generica con mascara 0 y con destino a la IP del puerto del router de salida en caso de los dos routers de los laterales. Y en el router del centro, tiene que ir direccionado a uno de los de los lados. El siguiente es un ejemplo de como se haria:

    ip route 0.0.0.0 0.0.0.0 192.168.1.153

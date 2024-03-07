**

# Practica 3<span style="float: right; font-size: medium;">[Anterior practica](MemPract2.md) | [Siguiente practica](MemPract4.md)
</span>

## 3.1

**a)**

TODO: HACER LA TABLA

**b)**

Crear la estrucutura con los 4 routers, 2 swithc a cada router inferior, un total de 6 switches y 2 PCs por switch, 6 PCs en tontal, uno por cada subred

Ahora por cada salida de los routers de abajo creamos una nueva red como en la practica anterior con su GateWay, y creamos las 4 subredes que conectan los switches entre ellos. Seguido configuramos los PCs, cada uno en una de las subredes y les fijamos los GateWay

## 3.2

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

## 3.3

**i)**


## Vlans

Las vlans se utilizan cuando hay varias redes dentro de un mismo red, y ambas cruzan por el mismo switch.

#### Parte del switch comun
1. Ejecutamos desde el switch comun
2. Hacemos el ``enable`` y ``configure t``
3. El los siguientes pasos, una por cada vlan que necesites:  
    3.1. ``vlan <numero>``  
    3.2. ``name <nombre>``   Utilizar algo como vlan\<numero>  
    3.3. ``exit``  Para salir de la vlan
4. Por cada salida del switch que vaya a una vlan:  
    4.1. ``interface <interfaz>``  
    4.2. ``switchport access vlan <numeroVlan>``
5. Por cada salida del switch que vayan varias vlans:  
    5.1. ``interface <interfaz>``  
    5.2. ``switchport mode trunk``
6. Guardar la informacion con ``wr``

#### Parte del router

1. Ejecutamos desde el router que da al switch comun
2. Hacemos el ``enable`` y ``configure t``
3. Abrimos el puerto con ``interface <interfaz>`` y ``no shutdown``
4. Por cada interfaz, entramos en su subinterfaz y creamos el encapsulation y su IP de Gateway:  
    4.1. ``interface <interfaz>.<subinterfaz>``  
    4.2. ``encapsulation dotlq <numeroVlan>``  
    4.3. ``ip address <ipGateway> <mascara>``
5. Guardar la configuracion ``wr``

#### Que no se te olvide fijar los gateways

## Conexion entre routers por eternet



## Conexion entre routers por serial

1. Entras a la interfaz
2. La enciendes
3. Haces el ``encapsulation <ppp o lo que sea>``
4. Se hace el ``ip address <direccionPuerto> <mascara>``
5. (En caso de ser DCE) ``clock rate 2048000``
6. ``ip route <direccion> <mascara> <interfaz>``





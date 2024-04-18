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
    4.2. ``encapsulation dot1q <numeroVlan>``  
    4.3. ``ip address <ipGateway> <mascara>``
5. Guardar la configuracion ``wr``

#### Que no se te olvide fijar los gateways

## Conexion estatica entre routers por eternet

1. Hacemos el ``enable`` y ``configure t``
2. Abrimos los ambos puertos, el del otro router y el de direccion la red
3. Fijamlos las ip de Gateway en la interfaz del router con ``ip address <ip> <mascara>``
4. Fijamos la ip del enlace entre los routers en su interfaz ``ìp address <ip> 255.255.255.252``
5. Fijamos la ruta estatica hacia el otro router: ``ip route <redDestino> <mascaraDestino> <ipPuertoSiguienteRouter>``

## Conexion estatica entre routers por serial

1. Hacemos el ``enable`` y ``configure t``
2. Abrimos los ambos puertos, el del otro router y el de direccion la red
3. En la interfaz hacia el siguiente router haces el ``encapsulation <ppp o lo que sea>``
4. Se hace el ``ip address <direccionPuerto> <mascara>``
5. (En caso de ser DCE) ``clock rate 2048000`` #bits/seg
6. Fijamos las rutas estaticas: ``ip route <direccion> <mascara> <interfaz>``

## Conexion dinamica entre routers

1. Hacemos el ``enable`` y ``configure t``
2. Abrimos los ambos puertos, el del otro router y el de direccion la red
3. Fijamlos las ip de Gateway en la interfaz del router con ``ip address <ip> <mascara>``
4. Fijamos la ip del enlace entre los routers en su interfaz ``ìp address <ip> 255.255.255.252`` 
5. (En caso de ser un enlace serial se configura)
6. Configurar el RIP:
~~~
router RIP
version 2
network <Red interna>
~~~

## Asignar IPs dinamicas

1. Hacemos el ``enable`` y ``configure t``
2. Abrimos el puerto del interior de la red y hacemos ``ip nat inside``
3. Abrimos el puerto del exterior de la red y hacemos ``ip nat outside``
4. Salimos de la interfaz y para cada PC, hacemos lo siguiente:
~~~
access-list <num_acl> permit <IP> # El num_acl es un identificador el pool, poner 1 en todos por ejemplo
~~~
5. Configuramos el almacen de direciones:
~~~
 ip nat pool <nombre_pool> <prim_dir> <ult_dir> netmask <mascara>
~~~
6. Activar el NAT:
~~~
ip nat inside source list <num_acl> pool <nombre_pool> overload
~~~






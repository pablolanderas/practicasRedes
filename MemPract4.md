# Practica 4<span style="float: right; font-size: medium;">[Anterior practica](MemPract3.md) | [Siguiente practica](MemPract5.md)
</span>

- [3.1](#3.1)
- [3.2](#3.2)

## 3.1 <a id="3.1">

**a)**

Crear el switch con la IP y la mascara dada

**b)**

Crear y configurar el GateWay como en [practica 2 3.2 b)](MemPract2.md#3.2b)

**c)**

Colocar el ISP y conectarlo al router

**d)** <a id="3.1.d">

Configurar el puerto de salida al ISP dandole una IP y creando la ruta estatica como en la [practica 3 3.3 i)](MemPract3.md#3.3i)

**e)** <a id="3.1.e">

Colocar un nuevo router B, con un ordenador. Fijar la IP que le asigna el ISP (doble click y ISP configuration) y la mascara /27 (255.255.255.224). Abrir los puertos , fijarle el GateWay y crear la ruta estatica de salida como en el [apartado d)](#3.1.d)

**f)**

Hacer el mismo pase que en el [apartado e)](#3.1.e) pero con la nueva IP asignada

**g)**

Al hacer el ping entre la red B y la C funciona correctamente

**h)**

Desde la red A pueden enviar cosas a las redes B y C ya que son publicas (utilizan la IP que les ha asignado el ISP), pero por ejemplo al hacer un ping, el paquete les llega pero no hay respuesta, por lo que no se pueden comunicar

**i)**

1. Acceder a la interfaz interior de la red, la que apunta al switch y escribir:

        ip nat inside

2. Acceder a la interfaz exterior, la que apunta al ISP y escibir

        ip nat outside

3. Para todas las IPs de los PCs, hacer el siguiente comando fuera de la intefaz:

        access-list [num_acl] permit [ip]

    El num_acl debe de ser siempre el mismo, por ejemplo 1

4. Configurar el almacen de direcciones IPs

        ip nat pool [nombre_pool] [prim_dir] [ult_dir] netmask [mascara]

    nombre_pool = por ejemplo pool1  
    prim_dir = ip.0  
    ult_dir = ip.31  
    mascara = 255.255.255.224

 5. Activar el NAT

        ip nat inside source list [num_acl] pool [nombre_pool] overload

**j)**

Se muestran con el siguiente comando:

         show ip nat translations

**k)**

Al hacer un ping desde la red A a cualquier otra lo hace correctamente ya que ahora las redes publicas pueden devolver correctamente el paquete

## 3.2 <a id="3.2">

**a)**

Hay que acceder al PC que quieres usar como servidor, abrir la aplicacion en el de ``Server Applications`` y activar el ``HTTP (web) Sever``, la ultima opcion.

**b)**

Acceder al PC y abrir la aplicacion en el de ``Server Applications`` y activar el ``DNS Server``. Dentro de este, darle a ``DNS setup`` y añadir el dominio www.practica.es a la IP del servidor donde hemos desplegado el HTTP Server

**c)**

En los PCs, en el apartado de configurar la IP, hacer click en ``DNS Config`` y añadir la IP del servidor de DNS

**d)**

Desde cualquier ordenador de la red A, se deberia poder abrir en el navegador la página con el URL

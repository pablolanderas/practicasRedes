# Practica 1 <span style="float: right; font-size: medium;">[Siguiente practica](MemPract2.md)</span>

- [3.1](#3.1)
- [3.2](#3.2)
- [3.3](#3.3)

3.1 <a id="3.1">

    a)  
        Poner los PCs, Switch 2950 24+2 y cables rectos al ser distinta capa
    b)  
        Abrir la terminal y hacer un un ping  
    c)  
        Conectar el cable "console" y habir el hyperterminal  
    d)  
        Usar enable para entrar modo administrador y despues show interface  
  
3.2  <a id="3.2">

    a)  
        Creamos los nuevos PCs y el Switch como antes
    b)  
        Conectamos pero esta vez con cable cruzado al ser de la misma capa y hacemos el ping  
    c)  
        Utilizando el comando show mac-address-table podemos mostrar la tabla  
  
3.3  <a id="3.3">
  
    a)  
        1. Entramos en modo configuracion: configure t  
        2. Cambio a la vlan 2: vlan 2  
        3. Le cambio el nombre: name vlan2
        4. Vuelvo a la configuracion: exit  
        5. Accedo a la interfaz del primer puerto: interface Fa0/1  
        6. Cambio el puerto a la vlan 2: switchport access vlan 2  
        7. Accedo ahora a la interfaz del segundo puerto: interface Fa0/2  
        8. Cambio el puesto a la vlan 2: switchport access vlan 2 
    b) 
        Cambiar las mascaras de todos los dipositivos a 128 y la ip a los dispositivos que 
        no estan en la vlan a 128 en adelante                  
    c) 
        Acceder a las dos interfaces que los conecta y escribir switchport mode trunk
    d) 
        Al hacer un ping se conectan adecuadamente
    e)
        Para guardar la configuracion escribir: wr
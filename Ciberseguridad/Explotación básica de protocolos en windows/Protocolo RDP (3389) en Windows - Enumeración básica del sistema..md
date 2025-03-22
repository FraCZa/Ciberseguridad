-  Se encuentra en el puerto 3389.
- El protocolo RDP permite a un usuario conectarse de manera remota a otra computadora a través de una red. Permite a los administradores y usuarios acceder a sus equipos de forma segura desde prácticamente cualquier lugar.

- Vamos a entrar a una maquina victima Windows 7, vamos a utilizar la herramienta ==xfreerdp==, utilizando las credenciales que nos han entregado en Tryhackme.
```
xfreerdp /u:(USUARIO) /p:(PASSWORD) /v:(IP_VICTIMA):(PUERTO_DONE_ESTE_CORRIENDO_RDP)
```

![](../Imagenes/Pasted%20image%2020241221174908.png)

- Cuando lo ejecutemos se nos abrirá una ventana de Windows.

![](../Imagenes/Pasted%20image%2020241221174958.png)

- Estando dentro podemos usar los siguientes comandos:
```
net user
```
- Nos muestra que usuarios hay en la maquina.
```
net user (NOMBRE_USUARIO)
```
- Nos entrega información de ese usuario.
```
net localgroup administrators
```
- Listado de administradores.
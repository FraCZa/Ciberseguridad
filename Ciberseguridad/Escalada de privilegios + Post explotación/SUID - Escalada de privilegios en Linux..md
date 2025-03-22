SUID --> Permiso especial en sistemas Unix y Linux que permite a los usuarios ejecutar un archivo con los privilegios del propietario del archivo en lugar de los usuarios que lo ejecutan.

- Tenemos una maquina victima con el puerto 3333 abierto, en este puerto corre un servidor ==apache==.
- Vamos a ver que tiene esta pagina web.
![](../Imagenes/Pasted%20image%2020250111180039.png)
- Vamos a hacer fuzzing para encontrar algo.
- Encontramos el directorio internal.

![](../Imagenes/Pasted%20image%2020250111180434.png)
- Podemos subir un archivo .php para hacer una reverse shell y entrar en la maquina victima.
- Al subirlo, nos avisa que la extensión no es correcta.

![](../Imagenes/Pasted%20image%2020250111180840.png)
- Vamos a cambiarle la extensión con el siguiente comando:
```
mv (NOMBRE_ARCHIVO) (NUEVO_NOMBRE)
```

![](../Imagenes/Pasted%20image%2020250111181055.png)
![](../Imagenes/Pasted%20image%2020250111181116.png)
- Ahora vamos a ver si existe un upload en esta pagina.
- Para eso vamos a usar ==gobuster== y en la -u vamos a agregar el fichero completo. (Hasta el internal)
![](../Imagenes/Pasted%20image%2020250111181446.png)
- Tenemos el uploads.
- Dejamos en escucha y ejecutamos el archivo en el directorio uploads.
- Hacemos ==TTY==.
- Ya dentro, si usamos el comando `sudo -l` nos saldra lo siguiente:
![](../Imagenes/Pasted%20image%2020250111182155.png)
- En este caso, vamos a usar el siguiente comando para buscar binarios:
```
find / -perm -4000 2>/dev/null
```
![](../Imagenes/Pasted%20image%2020250111182431.png)
- Cada vez que ejecutamos este comando estamos hablando de binarios ==SUID==.
- El binario que nos interesa es el ==systemctl==.
- Buscamos en la pagina web y encontramos esto:
![](../Imagenes/Pasted%20image%2020250111182722.png)
- Tenemos que crear un fichero que tenga esa información (Desde la tercera línea de código, hasta el final.)
- Nos vamos al fichero ==/tmp==.
![](../Imagenes/Pasted%20image%2020250111183222.png)
- Vamos a usar ==nano==.
![](../Imagenes/Pasted%20image%2020250111183324.png)
.sh --> Especifica que el archivo tendrá códigos ==shell==
- Pegamos el contenido:
![](../Imagenes/Pasted%20image%2020250111183536.png)
- Esto es importante, hay que modificar el código en naranjo, ya que este código estaría ejecutando una acción como root.
- ingresamos el siguiente comando:
```
chmod u+s /bin/bash
```
- Este comando sirve para cambiar los permisos de un archivo o programa en sistema Linux.
==chmod==: Comando para cambiar los permisos de un archivo.
==u+s==: Significa "añadir el bit SUID para el propietario del archivo". Cuando el bit SUIT está establecido en un programa ejecutable, cualquiera que lo ejecute lo hará como root.
==/bin/bash==: Archivo al que se están aplicando los cambios de permisos. En este caso, es la shell Bash.
![](../Imagenes/Pasted%20image%2020250111184512.png)
- Guardamos y lo ejecutamos.
![](../Imagenes/Pasted%20image%2020250111184708.png)
- Nos sale un error.
- Vamos a ver las líneas 7 y 8 del código.
- Hay que poner la ruta absoluta del binario que estamos atacando.
![](../Imagenes/Pasted%20image%2020250111185031.png)
- Vamos a probar nuevamente ejecutándolo.
![](../Imagenes/Pasted%20image%2020250111185152.png)
- Ya no nos sale error.
- Ahora ejecutamos el comando:
```
bash -p
```
- Ya somos root.
![](../Imagenes/Pasted%20image%2020250111185323.png)
- Somos root.
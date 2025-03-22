Drupal -> Gestión de contenido de código abierto, para crear y administrar sitios web y aplicaciones. Conocido por su flexibilidad y capacidad para manejar grandes volúmenes de contenido y tráfico.

- Tenemos nuestra maquina victima.
- En el escáner de puerto, este dominio Drupal se encuentra en el puerto 80, podemos ver que hay si ponemos la versión en el URL.
- ==PARA SABER LA INFORMACIÓN DE UNA PAGINA WEB, USAMOS EL COMANDO `whatweb` + URL==
![[Pasted image 20250110174928.png]]
- Ya comprobamos la versión de este Drupal.
	- Si no lo sabemos aun, podemos encontrarlo en el código fuente.
- Como tenemos la versión vamos a ver un exploit en ==metasployd==.
- Vamos a buscar con el comando `searc` druplal 7.
![[Pasted image 20250110175210.png]]
- Drupal 7 es vulnerable con el exploit ==drupalgeddon2==.
- usamos el exploit con el comando `use`, luego le seleccionarlo usamos el comando `show options` para configurarlo.
![[Pasted image 20250110175415.png]]
- En RHOST tenemos que poner el URL donde se encuentra el Drupal.
- Le damos a `run` y ya estamos dentro.
- Estando dentro, estamos en una sesión de interpreter. Para poder hacer todos los comandos a nivel raíz vamos a utilizar el comando `shell`.
- Tenemos que buscar un archivo llamado ==settings.php==.
	- Para eso ocupamos este comando:
```
find / -name setting.php 2>/dev/null
```
![[Pasted image 20250110180904.png]]
- Ya encontrada, vamos a leerlo con el comando `cat`.
- Podemos encontrar una contraseña que nos la pidan en el test.
![[Pasted image 20250110181018.png]]

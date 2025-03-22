
- Sabemos que la maquina es Linux al usar el comando `ping`
- Tenemos los puertos 80 y 443 abiertos
	- 443 --> Este puerto está asociado principalmente con el protocolo HTTPS.
 - Si queremos entrar por el puerto 443 tenemos que anteponer https:// y lP.
 - Vamos a hacer fuzzing para descubrir directorios.
 - Encontramos un wp-login
![[Pasted image 20250215174301.png]]
- Que como sabemos esto es Wordpress.
![[Pasted image 20250215174338.png]]
- Sabemos que el usuario es Elliot, vamos a hacer una fuerza bruta pero no con hydra, si no que con ==wpscan==. El comando seria el siguiente:
```
wpscan --url http://(IP_VICTIMA) --password (DICCIONARIO) --usernames (USUARIO)
```
- Ya teniendo los datos, ingresamos al wp-login
![[Pasted image 20250215174919.png]]
- Para tener acceso a la maquina iremos primero a ==Appearance==, ==Editor==.
![[Pasted image 20250215175143.png]]
- Vamos a editar una plantilla para inyectar un código malicioso y asi tener acceso a la maquina victima.
- Vamos  a usar ==msfvenom==
![[Pasted image 20250215175312.png]]
- Al crearlo, hacemos un cat al archivo creado y copiamos todo en una plantilla para que se puede ejecutar.
- Vamos a cambiar esta plantilla:
![[Pasted image 20250215175456.png]]
- Ya que si ingresamos mal la URL al tirar el error 404 va a ejecutar el comando malicioso.

![[Pasted image 20250215175535.png]]
- Ahora nos vamos a /wp-content que aquí es donde se guardan las plantillas.
![[Pasted image 20250215175659.png]]
- Y le ponemos una ruta que no exista para ejecutar el comando.
- Pero antes tenemos que estar en escucha.
![[Pasted image 20250215175902.png]]
- Hacemos antes otra conexión ya que sabemos que las reverse en msfvenom no son estables.
- Podriamos hacer la TTY pero no nos dejara hacerla, en este caso podemos usar este otro comando:
```
python -c "import pty; pty.spawn('/bin/bash')"
```
- Ya dentro encontramos un usuario y una contraseña hasheada, podemos usar ==john== o podemos irnos a la pagina ==crackstation== y descifrar la contraseña.
![[Pasted image 20250215180639.png]]
- Hacemos un su robot y ingresamos la contraseña y ya somos root.
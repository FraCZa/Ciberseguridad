kali
Port:22,80,8089

- Vamos a ver la pagina.
- No hay nada interesante, vamos a hacer fuzzing.
- No encontramos nada, vamos a meternos en el puerto 8089
![[Pasted image 20250309180727.png]]
- Vamos a ver que encontramos acá.
- Si ingresamos comandos o palabras al asar no nos sale nada, pero puede que sea vulnerable al ==SSTI==.
	- Esto es una vulnerabilidad de seguridad que ocurre cuando se pueden inyectar código malicioso en plantillas.
	- Si ingresamos `{{7*7}}`, y nos sale ==Hola, 49!== , es porque estamos frente a la vulnerabilidad por ==SSTI==.
![[Pasted image 20250309182410.png]]
- Vamos a buscar un payload por el cual nos permita ejecutar comandos de forma remota.
- Encontramos el siguiente:
```
{{ self.__init__.__globals__.__builtins__.__import__('os').popen('id').read() }}
```
- En este comando, si agregamos un comando de reverse en el ==id==, podríamos ingresar a la maquina.
- Vamos a dejar en escucha nuestra maquina y a crear una reverse.
![[Pasted image 20250309182858.png]]
![[Pasted image 20250309183217.png]]
- Ya estamos dentro.
- Hacemos TTY
- Vamos a escalar privilegios
![[Pasted image 20250309183431.png]]
![[Pasted image 20250309183453.png]]
- Como sabemos que tenemos el puerto 22 abierto, vamos a leer el id_rsa de ese puerto, el comando seria asi:
```
sudo -u root /usr/bin/base64 /root/.ssh/id_rsa | base64 --decode
```
![[Pasted image 20250309183941.png]]
- Tenemos una key.
- Si queremos ingresar con la key y nos pide contraseña, vamos a tener que sacar el hash con john.
![[Pasted image 20250309184709.png]]
- Ahora hacemos fuerza bruta con john
![[Pasted image 20250309185017.png]]
- Volvemos a probar en el ssh.
![[Pasted image 20250309185051.png]]

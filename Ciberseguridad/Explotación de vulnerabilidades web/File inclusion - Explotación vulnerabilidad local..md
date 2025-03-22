- Tenemos un puerto 80
- Vamos a hacerle fuzzing a la pagina web para encontrar otros directorios.
- Tenemos esto:
![[Pasted image 20241220160248.png]]
- Cada vez que en la URL tenemos un ==doc= ===, estamos frente a una posible vulnerabilidad.
- Esto quiere decir que podemos retroceder por directorios.
- Para poder retroceder por directorios lo hacemos de la siguiente forma:
```
doc=../../../../../../../../../
```
==IMPORTANTE, PONER MUCHOS ../../../==
- Lo ideal es encontrar el directorio ==passwd== , para eso al final de los ../ ponemos `/etc/passwd`.
![[Pasted image 20241220160702.png]]
- Dentro de esta información, tenemos a un usuario.
- Si hay un nombre después del fichero /home/ eso quiere decir que es un usuario. En este caso el usuario es gh0st.
- Entonces ahora vamos a eliminar /etc/passwd/ de la URL e ingresar /home/gh0st/.ssh/id_rsa
	- Siempre en los ficheros de usuario se encuentra oculto el fichero .ssh.
	- id_rsa se encuentra dentro del fichero oculto .ssh, y nos entrega una key que la podemos codificar con la herramienta ==john==.
![[Pasted image 20241220161244.png]]
- Vamos a pegar esto en un nano.
- Le vamos a agregar un permiso especial.
```
chmod 600 (NOMBRE)
```
![[Pasted image 20241220161457.png]]
- Vamos a ingresar por el puerto 22 utilizando esta key con el siguiente comando:
```
ssh -i (NOMBRE_ARCHIVO_KEY) (USUARIO)@(IP_VICTIMA)
```
![[Pasted image 20241220161709.png]]
![[Pasted image 20241220161735.png]]
- Nos pide una contraseña para abrir la key, aquí utilizamos la herramienta ==john==
 - Vamos a craquearlo.
 - En este caso como es ssh el comando seria asi:
```
ssh2john (NOMBRE_ARCHIVO_KEY) > (HASH)
```
![[Pasted image 20241220162008.png]]
- Ahora que lo tenemos vamos a hacer fuerza bruta con la herramienta ==john== , en ese archivo para descubrir la contraseña que nos permitirá craquearlo.
```
john --wordlist=/usr/share/wordlists/rockyou.txt (HASH)
```
![[Pasted image 20241220162213.png]]
- La contraseña seria ==celtic==
- Ahora ingresamos los datos y ya estamos dentro de la maquina.
- Este protocolo al igual que el puerto es utilizado principalmente en maquinas Windows.
- Este puerto permite compartir recursos por la red.

- Vamos a usar la herramienta ==smbclient== para enumerar este protocolo.
- Para usar esta herramienta debemos usar el siguiente comando:
```
smbclient -L (IP_VICTIMA) -N
```
==N -> Enumerar recurso compartido sin poner credenciales.==
![[Pasted image 20241221152431.png]]
- En este caso no podemos enumerar este protocolo sin credenciales.
- En este caso sabemos que el usuario es `mario` y la clave es `123123`. 
- Ya teniendo esta información ahora vamos a listar los recursos compartidos ingresando el siguiente comando con el usuario y a continuación ingresando la clave:
```
smbclient -L (IP_VICTIMA) -U '(USUARIO)'
```
![[Pasted image 20241221152930.png]]
- Ingresamos la clave.
![[Pasted image 20241221152954.png]]
- Ya tenemos los recursos compartidos.
- Ahora, como sabemos cual de estos recursos nosotros tenemos acceso.
	- Para eso vamos a utilizar ==smbmap==.
```
smbmap -H (IP_VICTIMA) -u '(USUARIO)' -p '(CONTRASEÑA)'
```
![[Pasted image 20241221153310.png]]
- Solo tenemos permiso en ==Users==.
- Ahora como podemos entrar en el recurso compartido?
	- Usamos ==smbclient==.
```
smbclient -U '(USUARIO)' //(IP_VICTIMA)/(NOMBRE_RECURSO)
```
![[Pasted image 20241221153722.png]]
- ya estamos dentro.

==EXPLOTACIÓN BÁSICA CON METASPLOIT==

- Vamos a hacer un ataque de fuerza bruta al puerto SMB.
- Ya en la herramienta ==metasploit==.
- Vamos a ocupar el exploit:
```
use auxiliary/scanner/smb/smb_login
```
![[Pasted image 20241221160050.png]]
- vamos a configurarlo con el comando `show options`
- Configuramos el ==RHOSTS== con la IP victima.
- Se recomienda quitar ==VERBOSE== , para que el ataque sea mas rápido.
![[Pasted image 20241221160608.png]]
- Estas opciones son por si tenemos el usuario y la contraseña (que si sabemos), pero solo vamos a rellenar el del usuario para que se nos haga fuerza bruta en password.
![[Pasted image 20241221160755.png]]
- Cargamos el diccionario que vamos a utilizar en ==PASS_FILE==
- Hacemos run
![[Pasted image 20241221160939.png]]
- Tenemos la contraseña.

==METASPLOIT CON PSEXEC==
- Vamos a buscar otra forma de como entrar utilizando ==psexec==.
- psexec -> Es una herramienta de línea de comando que permite ejecutar procesos en sistemas remotos sin necesidad de instalar software adicional en esos sistemas.
- El comando es el siguiente:
```
use exploit/windows/smb/psexec
```
![[Pasted image 20241221162311.png]]
- Vamos a configurarlo.
![[Pasted image 20241221162340.png]]
- Como ya tenemos todas las credenciales, vamos a rellenar ==RHOSTS==, ==SMBUser== y ==SMBPass==.
- Lo ejecutamos con run.
- En este caso no se pudo ya que no esta habilitado, pero puede que si lo este en el examen.
![[Pasted image 20241221162651.png]]

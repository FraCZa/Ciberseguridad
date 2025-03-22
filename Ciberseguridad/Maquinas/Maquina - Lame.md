10.10.10.3
Linux
Port: 139,21,22,445,3632
- Tenemos 2 puertos que funcionan como ftp, 445 y 139 , pero primero vamos a ver que encontramos en el puerto 21.
- No encontramos nada, vamos a ver los puertos 445 y 139 especialmente el 445.
- Como no tenemos credenciales vamos a enumerar con la herramienta ==rpcclient==.
```
rpcclient -U "" -N (IP_VICTIMA)
```
![[Pasted image 20250317183214.png]]
- Nos redirecciona a un lugar donde podemos ejecutar comandos.
- No encontramos nada de utilidad, vamos a usar el comando ==smbnap== para ver si encontramos algún directorio
```
smbmap -H (IP_VICTIMA)
```
![[Pasted image 20250317183630.png]]
- Vemos que podemos leer y escribir en /tmp, para ingresar usamos el siguiente comando.
```
smbclient -N //(IP_VICTIMA/tmp)
```
![[Pasted image 20250317183812.png]]
- Pero no hay nada de interés
![[Pasted image 20250317183916.png]]
- Vamos a ver si Samba tiene una vulnerabilidad.
- Sabemos que la version de samba es 3.0.20
```
searchsploit "Samba 3.0.20"
```
![[Pasted image 20250317184250.png]]
- la segunda opción nos funciona, vamos a abrir metasploit
![[Pasted image 20250317184421.png]]
- Usamos este y lo configuramos.
![[Pasted image 20250317184540.png]]
- Lo ejecutamos.
![[Pasted image 20250317184818.png]]
- Estamos dentro como root.
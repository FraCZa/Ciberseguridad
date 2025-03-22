- Vamos a hacer la maquina Cyborg

- Tenemos 2 puertos abiertos, 22 y 80.
- Si nos sale un archivo .tar, para extraer archivos comprimidos usamos el siguiente comando:
```
tar -xvf (NOMBRE_ARCHIVO)
```

![[Pasted image 20250124172408.png]]
- Se nos descomprimió en este archivo:
![[Pasted image 20250124172536.png]]
- Para poder ver bien su contenido (ya que hay muchas carpetas) podemos usar el comando `tree`.
![[Pasted image 20250124172617.png]]
- Vamos a leer lo que tiene el archivo ==README==.
![[Pasted image 20250124172950.png]]
- Nos lanza a una pagina donde hay un programa que tenemos que instalar en nuestra maquina atacante para poder ver el contenido de este de forma completa.
![[Pasted image 20250124173044.png]]
- Instalamos.
- El programa se llama==Borg==.
	- Herramienta de copias de seguridad gratuita y de código abierto para Linux.
- Ahora vamos a montar el contenido que descomprimimos a otra carpeta.
```
borg mount (RUTA_REPOSITORIO) + (DONDE_MONTAR)
```
![[Pasted image 20250124173603.png]]
![[Pasted image 20250124173755.png]]
- Me pide una contraseña.
- Tenemos otro directorio web llamado /etc
![[Pasted image 20250124174001.png]]
- Acá tenemos una credencial que esta hasheada.
- Vamos a crear un archivo y copiaremos ese código.
![[Pasted image 20250124174106.png]]
- Vamos a utilizar la herramienta ==hashcat== para poder craquearlo.
```
hashcat -a 0 -m (MODULO) (NOMBRE_ARCHIVO) /usr/share/wordlists/rockyou.txt
```
-a --> El ataque siendo 0 el general o predeterminado.
-m --> Modulo del hash para que la herramienta y se pueda trabajar de forma especifica.
	- El modulo lo podemos encontrar en esta pagina: https://hashcat.net/wiki/doku.php?id=example_hashes, en este caso seria el 1600.
![[Pasted image 20250124174714.png]]
- Ejecutamos.
![[Pasted image 20250124174926.png]]
- En este caso tenemos un error porque hashcat utiliza la tarjeta grafica del equipo, en este caso como estoy en un MV no puedo ejecutarlo pero si lo podria hacer en una maquina principal con Linux. Así que, vamos a utilizar john.
![[Pasted image 20250124175506.png]]
- Nos sale este error, detecta que el hash es ==md5crupt==, pero la cadena también se reconoce como ==md5crypt-long==. entonces quedaría asi el comando:
```
john --format=md5crypt-long --wordlist=/usr/share/wordlists/rockyou.txt hash
```
- Nos da como contraseña ==squidward==
- Ahora podemos utilizarla para montar el repositorio que descomprimimos. 
![[Pasted image 20250124180016.png]]
![[Pasted image 20250124180034.png]]
- Ahí esta.
![[Pasted image 20250124180116.png]]
- Teniendo ya esto, vamos  a investigar los .txt
![[Pasted image 20250124180230.png]]
- Tenemos credencial para entrar por el puerto 22.
![[Pasted image 20250124180316.png]]
- Escalamos credencial y listo.
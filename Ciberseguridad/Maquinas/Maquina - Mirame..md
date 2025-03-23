kali 
Port: 22, 80

- Vamos a ver la pagina web por si encontramos algo interesante.

![](../Imagenes/Pasted%20image%2020250310183127.png)

- Encontramos un login web, pero de todas formas vamos a hacer fuzzing web para ver si encontramos algo mas.
- Vamos a usar sqlmap para encontrar alguna base de dato.

![](../Imagenes/Pasted%20image%2020250310184037.png)

- Vamos a investigar el users con este comando:
```
sqlmap -u (URL_CORRESPONDIENTE) --forms -D (NOMBRE_BASE_DATOS) --tables --batch
```
- Encontramos esta tabla

![](../Imagenes/Pasted%20image%2020250310184206.png)

- Vamos a ver sus columnas con el siguiente comando:
```
sqlmap -u (URLS_CORRESPONDIENTE) --forms -D (NOMBRE_BASE_DATOS) -T (TABLA) --columns --batch
```
- Nos da estas 3 columnas.

![](../Imagenes/Pasted%20image%2020250310184431.png)

- Ahora vamos a ver el registro de cada columna con el siguiente comando:
```
sqlmap -u (URLS_CORRESPONDIENTE) --forms -D (NOMBRE_BASE_DATOS) -T (TABLA) -C(COLUMNAS) --dump --batch
```

![](../Imagenes/Pasted%20image%2020250310184625.png)

- Ya tenemos credenciales, vamos a ver si podemos loggear por la pagina o por el puerto 22
- Al ingresar cada uno de las credenciales nos arroja a esta pagina:

![](../Imagenes/Pasted%20image%2020250310184833.png)

- Vamos a ver si logramos algo en el puerto 22

![](../Imagenes/Pasted%20image%2020250310185421.png)

- No se conecto con ninguna credencial.
- Pero la contraseña "directoriotravieso" sobre sale de todos, vamos a ver si no hay un directorio que se llame asi haciendo fuzzing.
![](../Imagenes/Pasted%20image%2020250310185550.png)
- Encontramos un directorio.
![[Pasted image 20250310185609.png]]
- Encontramos una imagen, debe tener información importante.
![[Pasted image 20250310185655.png]]
- Vamos a descargarla.
- Vamos a ver que información tiene con ==exiftool==.
- No hay nada interesante, vamos a utilizar ==steghide==
![[Pasted image 20250310190322.png]]
- Vamos a tener que utilizar ==stegseek== para crackearlo.
![[Pasted image 20250310190444.png]]
- Vemos que la pass es chocolate, vamos a usar nuevamente ==steghide== para sacar lo que tiene dentro.
![[Pasted image 20250310190606.png]]
- Nos da un archivo .zip, vamos a descomprimirlo.
- Pero nos pide otra contraseña y no chocolate asi que vamos a usar john para hacer fuerza bruta.
- Vamos a usar ==zip2john== para hacerlo hash.
![[Pasted image 20250310190858.png]]
- Ahora hacemos fuerza bruta.
![[Pasted image 20250310190945.png]]
- Ahora si vamos a descomprimir.
![[Pasted image 20250310191106.png]]
- Tenemos nuestra credencial, vamos a entrar al puerto 22
![[Pasted image 20250310191136.png]]
- Vamos a escalar privilegios. 
- No funciona el comando sudo -l , vamos  a escalar por SUID.
![[Pasted image 20250310191324.png]]

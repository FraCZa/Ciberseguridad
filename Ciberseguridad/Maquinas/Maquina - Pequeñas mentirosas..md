Kali
Port: 22, 80

- Vamos a ver la pagina de esta maquina.
![[Pasted image 20250303170609.png]]
- Tenemos como pista, "A"
- Vamos a hacer Fuzzing por si encontramos algo.
![[Pasted image 20250303171026.png]]
- No encontramos nada.
- Puede que "a" sea un usuario, vamos a hacer fuerza bruta en el puerto 22.
![[Pasted image 20250303171337.png]]
- Tenemos usuario y contraseña.
- Ingresamos
![[Pasted image 20250303171635.png]]
- Vamos a ver que podemos encontrar.
- No encontramos nada pero, en el directorio ==/srv/ftp== podemos encontrar archivos asociados con los servidores.
![[Pasted image 20250303172003.png]]
- Vamos a descargar  toda estos archivos a nuestra maquina atacante.
- Tenemos que poner el siguiente comando en nuestra maquina atacante.
```
scp (usuario)@(IP_VICTIMA):/srv/ftp/* ~/Desktop/
```
![[Pasted image 20250303172245.png]]
- Vamos ahora a nuestra maquina.
- En clave privada tenemos una key
- Tenemos un hash, que seria hash_spence.txt eso lo podemos descifrar con john usando el siguiente comando:
```
john --format=raw-md5 hash_spencer.txt
```
![[Pasted image 20250303174508.png]]
- Este mismo resultado tendriamos si hacemos fuerza bruta con el usuario spencer.
![[Pasted image 20250303174631.png]]
- Vamos a entrar por el puerto ssh.
- Ya estamos dentro.
- Si usamos sudo -l
![[Pasted image 20250303174812.png]]
- Nos dice que todos podemos usar el binario python3 como root.
![[Pasted image 20250303175058.png]]

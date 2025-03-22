Kali
Port: 80,22

- Vemos su pagina y no encontramos nada interesante, vamos a hacer Fuzzing.
![[Pasted image 20250309165050.png]]
- Encontramos un wordpress.
- Vamos a usar ==wpscam==.
- Pero no encontramos nada, hacemos fuzzing en wordpress y encontramos un directorio .php, entonces vamos a usar wfuzz.
```
wfuzz -c --hc=404 --hl 40 --hw 169 -t 200 -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt http://172.17.0.2/wordpress/index.php?FUZZ=../../../../../../../../etc/passwd
```
![[Pasted image 20250309171127.png]]
- Vamos a ingresar love a la URL.
![[Pasted image 20250309171206.png]]
- Encontramos un usuario, vamos a hacer fuerza bruta para ver que nos encuentra.
- Pero también tenemos otro usuario "rosa".
![[Pasted image 20250309171937.png]]
- Tenemos credencial con rosa.
- Vamos a ingresar al puerto 22.
![[Pasted image 20250309172021.png]]
- Vamos a ver si podemos escalar privilegios con sudo -l
![[Pasted image 20250309172156.png]]
- Esto quiere decir que podemos listar cualquier cosa y a la vez leer cualquier cosa con permiso root.
- Para hacer eso tenemos que anteponer `sudo -u root cat o ls`
![[Pasted image 20250309172701.png]]
- Vamos a leer secret.txt usando cat.
![[Pasted image 20250309172753.png]]
- Tenemos este código que podemos codificar con ==cyberchef==
![[Pasted image 20250309172900.png]]
- Tenemos contraseña, lo mas probable es que sea de pedro. 
- Vamos a ingresar como pedro
![[Pasted image 20250309172945.png]]
- Vamos a escalar como root desde el usuario Pedro.
![[Pasted image 20250309173012.png]]
![[Pasted image 20250309173030.png]]
![[Pasted image 20250309173057.png]]

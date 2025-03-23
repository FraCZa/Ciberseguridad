Kali
Port: 80,22

- Vemos su pagina y no encontramos nada interesante, vamos a hacer Fuzzing.

![](../Imagenes/Pasted%20image%2020250309165050.png)

- Encontramos un wordpress.
- Vamos a usar ==wpscam==.
- Pero no encontramos nada, hacemos fuzzing en wordpress y encontramos un directorio .php, entonces vamos a usar wfuzz.
```
wfuzz -c --hc=404 --hl 40 --hw 169 -t 200 -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt http://172.17.0.2/wordpress/index.php?FUZZ=../../../../../../../../etc/passwd
```

![](../Imagenes/Pasted%20image%2020250309171127.png)

- Vamos a ingresar love a la URL.

![](../Imagenes/Pasted%20image%2020250309171206.png)

- Encontramos un usuario, vamos a hacer fuerza bruta para ver que nos encuentra.
- Pero también tenemos otro usuario "rosa".

![](../Imagenes/Pasted%20image%2020250309171937.png)

- Tenemos credencial con rosa.
- Vamos a ingresar al puerto 22.

![](../Imagenes/Pasted%20image%2020250309172021.png)

- Vamos a ver si podemos escalar privilegios con sudo -l

![](../Imagenes/Pasted%20image%2020250309172156.png)

- Esto quiere decir que podemos listar cualquier cosa y a la vez leer cualquier cosa con permiso root.
- Para hacer eso tenemos que anteponer `sudo -u root cat o ls`

![](../Imagenes/Pasted%20image%2020250309172701.png)

- Vamos a leer secret.txt usando cat.

![](../Imagenes/Pasted%20image%2020250309172753.png)

- Tenemos este código que podemos codificar con ==cyberchef==

![](../Imagenes/Pasted%20image%2020250309172900.png)

- Tenemos contraseña, lo mas probable es que sea de pedro. 
- Vamos a ingresar como pedro

![](../Imagenes/Pasted%20image%2020250309172945.png)

- Vamos a escalar como root desde el usuario Pedro.

![](../Imagenes/Pasted%20image%2020250309173012.png)


![](../Imagenes/Pasted%20image%2020250309173030.png)


![](../Imagenes/Pasted%20image%2020250309173057.png)


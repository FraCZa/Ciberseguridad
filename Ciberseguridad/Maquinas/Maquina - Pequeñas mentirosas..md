Kali
Port: 22, 80

- Vamos a ver la pagina de esta maquina.

![](../Imagenes/Pasted%20image%2020250303170609.png)

- Tenemos como pista, "A"
- Vamos a hacer Fuzzing por si encontramos algo.

![](../Imagenes/Pasted%20image%2020250303171026.png)

- No encontramos nada.
- Puede que "a" sea un usuario, vamos a hacer fuerza bruta en el puerto 22.

![](../Imagenes/Pasted%20image%2020250303171337.png)

- Tenemos usuario y contraseña.
- Ingresamos

![](../Imagenes/Pasted%20image%2020250303171635.png)

- Vamos a ver que podemos encontrar.
- No encontramos nada pero, en el directorio ==/srv/ftp== podemos encontrar archivos asociados con los servidores.

![](../Imagenes/Pasted%20image%2020250303172003.png)

- Vamos a descargar  toda estos archivos a nuestra maquina atacante.
- Tenemos que poner el siguiente comando en nuestra maquina atacante.
```
scp (usuario)@(IP_VICTIMA):/srv/ftp/* ~/Desktop/
```


![](../Imagenes/Pasted%20image%2020250303172245.png)

- Vamos ahora a nuestra maquina.
- En clave privada tenemos una key
- Tenemos un hash, que seria hash_spence.txt eso lo podemos descifrar con john usando el siguiente comando:
```
john --format=raw-md5 hash_spencer.txt
```

![](../Imagenes/Pasted%20image%2020250303174508.png)

- Este mismo resultado tendríamos si hacemos fuerza bruta con el usuario spencer.

![](../Imagenes/Pasted%20image%2020250303174631.png)

- Vamos a entrar por el puerto ssh.
- Ya estamos dentro.
- Si usamos sudo -l

![](../Imagenes/Pasted%20image%2020250303174812.png)

- Nos dice que todos podemos usar el binario python3 como root.

![](../Imagenes/Pasted%20image%2020250303175058.png)


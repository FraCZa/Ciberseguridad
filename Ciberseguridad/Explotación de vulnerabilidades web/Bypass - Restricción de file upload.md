- Pagina web que no nos deje subir archivos .php.
- Paginas con barrera que nos impida subir archivos maliciosos.



- Vamos a entrar por el puerto 3333:

![](../Imagenes/Pasted%20image%2020241219170506.png)

- Podemos ver que esta corriendo un Apache http.
- Pero, vemos que el no es un puerto 80. Entonces para poder entrar, pegamos la IP victima en la URL acompañado del puerto.

![](../Imagenes/Pasted%20image%2020241219170648.png)

- Vamos a hacer un Fussing web para ver si encontramos otra directorio.

![](../Imagenes/Pasted%20image%2020241219171951.png)

- Nos interesa el directorio ==/internal==.

![](../Imagenes/Pasted%20image%2020241219172036.png)

- Se puede subir archivos.
- En este caso la web tiene un limitador para archivos .php.
- Vamos a crear un payloads con ==msfvenom== pero diferente.
	- Diferente es cambiar la extensión del .php por sus otras extensiones. 
- Tenemos nuestro payloads `pichi.php` creado, le vamos a cambiar la extensión con el siguiente comando:
```
mv (NOMBRE.PHP) (NOMBRE.NUEVA_EXTENSIÓN)
```

![](../Imagenes/Pasted%20image%2020241219172730.png)

- Ahora vamos a probar en subirlo.

![](../Imagenes/Pasted%20image%2020241219172815.png)

- Vamos a ver si se subió.

![](../Imagenes/Pasted%20image%2020241219172917.png)

- Se subió correctamente.
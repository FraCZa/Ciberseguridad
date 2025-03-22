- Podemos ocupar esta herramienta para cambiar la extensión .php por cualquier otra sin la necesidad de cambiarlo desde la shell.

- Vamos a abrir Burp Suite.
- Ya tenemos configurado el navegador para que al momento de mandar algo por el navegador ==Burp Suite== lo intercepte y lo cambiemos.
- Para eso vamos a crear un .php y lo subiremos a una pagina que no acepta .php pero si un derivado de este.
- Cuando intercepte, lo que nos va a interesar es el ==filename== 

![](../Imagenes/Pasted%20image%2020241219190344.png)

- Este lo podemos cambiar por .phtml y lo mandamos apretando el botón ==forward==.
- Comprobamos si se subió:

![](../Imagenes/Pasted%20image%2020241219190510.png)

- Ahora desactivamos ==Burp Suite== y seguimos atacando la maquina.


==USO DEL REPEATER==

- Apartado de ==Burp Suite== 
- Nuevamente vamos a subir un .php pero esta vez vamos a ver que extensiones puede ser la correcta.
- Para eso vamos a utilizar el ==Repeater== para probar muchas extensiones.

![](../Imagenes/Pasted%20image%2020241219191832.png)

- Para activar ==Repeater== usamos ctrl + r y se manda la petición.
- Ya en ==Repeater==, apretamos el botón send y nos saldrá la respuesta de que no es la extensión correcta.

![](../Imagenes/Pasted%20image%2020241219192116.png)

- Así iremos probando hasta dar con la extensión correcta que en este caso es .phtml

![](../Imagenes/Pasted%20image%2020241219192225.png)

- Luego volvemos al ==Proxy== y enviamos la solicitud con la extensión correcta.

==USO DEL INTRUDER==

- Vamos a hacer otra prueba con la misma maquina.
- Activamos ==Burp Suite==
- ==Intruder== permite hacer una búsqueda de la extensión correcta para subir el archivo.
- Vamos a crear un .txt con posibles extensiones correctas.

![](../Imagenes/Pasted%20image%2020241219193148.png)

- Ya en ==Burp Suite== tenemos que especificar donde queremos que pruebe todas las extensiones posibles.
- Apretamos `ctrl + i` para mandar la petición a intruder.
![[Pasted image 20241219193953.png]]
- Ya acá vamos a seleccionar lo que queremos que ==intruder== nos ataque y vamos a apretar el botón ==add==.
- Nos vamos a ==settings==, a la opción ==Grep - Extract==
![[Pasted image 20241219194319.png]]
- Le damos a ==add== y luego  a ==refetch response==.
![[Pasted image 20241219194424.png]]
- Seleccionamos el siguiente mensaje para que ==Burp Suite== nos indique cuando una extensión es fallida, y le damos a ok.
![[Pasted image 20241219194546.png]]
- Si el mensaje es diferente, quiere decir que se encontró la extensión correcta.
- Nos vamos a la opción de ==payloads== y subimos nuestro .txt con las extensiones.
![[Pasted image 20241219194754.png]]
- Apretamos el botón ==Start Attack==.
- Y empezara el ataque.
![[Pasted image 20241219194907.png]]
- Y ya sabemos que petición es la correcta.
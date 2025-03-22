- Esto es una alternativa de los payloads en HP.


- Estamos nuevamente en un login web.
- Vamos a registrarnos

![](../Imagenes/Pasted%20image%2020241219131801.png)

- Ya dentro tenemos donde subir un archivo.

![](../Imagenes/Pasted%20image%2020241219131909.png)

- Vamos a crear un archivo .php

![](../Imagenes/Pasted%20image%2020241219132006.png)

- Vamos a ingresar este comando en el archivo ya creado.

![](../Imagenes/Pasted%20image%2020241219132240.png)

- Este código nos permite ejecutar comandos dentro de la maquina victima.
- Guardamos.
- Ahora la subimos a la pagina
- Si nos vamos a ==/uploads== , vamos a encontrar el archivo que subimos.

![](../Imagenes/Pasted%20image%2020241219132444.png)

- Si apretamos en el archivo nos va a tirar una pagina en blanco.

![](../Imagenes/Pasted%20image%2020241219132549.png)

- Lo que tenemos que hacer es agregar lo siguiente al final del URL:
```
?cmd=(COMANDO)
```
- Vamos a escribir el comando `whoami` y veremos como se ejecuta.

![](../Imagenes/Pasted%20image%2020241219132701.png)

- Podemos ejecutar cualquier otro comando.
- Para hacer una reverse shell debemos url-codear, y esto lo logramos usando ==Burp Suite== .
- Dentro de ==Burp Suite== , Entramos en la pestaña ==Decoder== y pegamos la reverse shell con la IP Atacante.

![](../Imagenes/Pasted%20image%2020241219133344.png)

- Anteponemos un `bash -c` seguido de comillas y el código del reverse shell.
- A la derecha hay unos recuadros, en el primer ==Encode as== , apretamos en la opción URL.

![](../Imagenes/Pasted%20image%2020241219133604.png)

- Nos saldrá esto:

![](../Imagenes/Pasted%20image%2020241219133635.png)

- Ya lo tenemos URL-Codeado.
- Ahora en el terminal, dejamos en escucha:

![](../Imagenes/Pasted%20image%2020241219133730.png)

- Nos vamos al navegador, y en la URL, justo al final, donde estamos poniendo comandos para que se ejecuten de forma remota, pegamos el URL que generamos en ==Burp Suite==.
- Ya estamos conectados:

![](../Imagenes/Pasted%20image%2020241219133929.png)


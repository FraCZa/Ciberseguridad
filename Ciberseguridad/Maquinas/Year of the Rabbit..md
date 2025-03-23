- Empezamos haciendo nmap.
- Tenemos los siguientes puertos abiertos:

![](../Imagenes/Pasted%20image%2020250217171613.png)

- Vemos que tiene el puerto 80 HTTP:

![](../Imagenes/Pasted%20image%2020250217171936.png)

- Solo una pagina Apache.
- Vamos a usar Gobuster ya que no encontramos nada en el código fuente.
- En este caso vamos a usar la herramienta ==wfuzz==
```
wfuzz -c -L --sc=200,301 -w /user/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt http://(IP_VICTIMA)/FUZZ
```

![](../Imagenes/Pasted%20image%2020250217172619.png)

- Vamos a investigar esta ruta.

![](../Imagenes/Pasted%20image%2020250217172651.png)

- Vamos a ver todo lo que nos entrega, empezando por el video.

![](../Imagenes/Pasted%20image%2020250217172756.png)

- Nada importante, veremos el archivo style.
- A primera vista se ve como un archivo .css normal, pero si leemos con cuidado encontramos este mensaje:

![](../Imagenes/Pasted%20image%2020250217172911.png)

- Vamos a investigar

![](../Imagenes/Pasted%20image%2020250217173000.png)

- Nos sale un mensaje pidiendo que desinstalemos el ==javascrit==.
- Se puede hacer de 2 formas:
	- Con una extensión:

![](../Imagenes/Pasted%20image%2020250217173251.png)

- Escribiendo lo siguiente en la URL:

![](../Imagenes/Pasted%20image%2020250217173344.png)

- Aceptamos, y en la barra de búsqueda escribimos javascript

![](../Imagenes/Pasted%20image%2020250217173516.png)

- En el .enable, desactivamos con click.
- Si volvemos a ingresar a la pagina, vamos a poder entrar pero seguirá siendo un trolleo.

![](../Imagenes/Pasted%20image%2020250217173639.png)

- Tampoco podemos entrar al puerto FTP ya que el reporte de nmap nos dice que no hay acceso de anonymous.
- Lo que podemos hacer es que con la ayuda de ==Burp Suite== podemos ver un directorio oculto
- Abrimos la herramienta e interceptamos la pagina que encontramos.

![](../Imagenes/Pasted%20image%2020250217174614.png)

- Ya interceptado, vamos a la pestaña ==Forward==, y vemos que llama al siguiente recurso:

![](../Imagenes/Pasted%20image%2020250217174718.png)

- El valor que nos va a servir es /WExYY2Cv-qU , este lo vamos a pegar en la URL

![](../Imagenes/Pasted%20image%2020250217175022.png)

- Tenemos una imagen .png, vamos a extraer información de esta imagen.
- Usamos la herramienta ==exiftool== para enumerar metadatos de la imagen.
```
exiftool (NOMBRE_IMAGEN)
```

![](../Imagenes/Pasted%20image%2020250217175350.png)

- Warnin nos da una pista de que puede haber algo dentro de la imagen.
- Vamos a utilizar el comando `strings` para leer el código fuente de la imagen.

![](../Imagenes/Pasted%20image%2020250217175522.png)

- Buscando en el código, nos sale el siguiente mensaje:

![](../Imagenes/Pasted%20image%2020250217175648.png)

- Ya tenemos el Username del FTP y nos dice que la password puede ser cualquiera de todas las líneas que vienen a continuación, vamos a tener que hacer un diccionario con todos esos dato y hacer fuerza bruta en el puerto 21 para dar con la contraseña.
- Vamos a usar la herramienta ==hydra== ejecutar este ataque.

![](../Imagenes/Pasted%20image%2020250217175936.png)

- Ya tenemos la contraseña.
- Vamos a ingresar al puerto FTP.
- Ya dentro buscamos que nos podemos encontrar,

![](../Imagenes/Pasted%20image%2020250217180110.png)

- Descargamos este .txt para ver su información desde nuestra maquina.

![](../Imagenes/Pasted%20image%2020250217180244.png)

- Nos va a salir unos símbolos raros, codificamos y ya tenemos nuestra credencial:

![](../Imagenes/Pasted%20image%2020250217180539.png)

- Vamos a probar por el puerto 22 si podemos ingresar con estas credenciales.

![](../Imagenes/Pasted%20image%2020250217180653.png)

- Estamos dentro.
- Al iniciar nos da un mensaje que hay una carpeta llamada "s3cr3t", vamos  a buscar esa carpeta con el siguiente comando:
```
find / -name '(NOMBRE)' 2>/dev/null
```
- Nos sale donde encontrar la carpeta:

![](../Imagenes/Pasted%20image%2020250217181204.png)

- Ya en la carpeta nos sale oculto el archivo:

![](../Imagenes/Pasted%20image%2020250217181255.png)


![](../Imagenes/Pasted%20image%2020250217181420.png)

- Vamos a hacer un movimiento lateral con esta credenciales para entrar en la maquina de Gwendoline.

![](../Imagenes/Pasted%20image%2020250217181546.png)

- Vamos a buscar la primera flag que se encuentra en su maquina en /home

![](../Imagenes/Pasted%20image%2020250217181638.png)

- Vamos a escalar privilegios.

![](../Imagenes/Pasted%20image%2020250217181925.png)

- Vamos a copiar el (ALL, !root) para ver que encontramos en google.
- Encontramos este exploit.
- ==VI es una herramienta de escritura==

![](../Imagenes/Pasted%20image%2020250217182034.png)

- Encontramos esto:

![](../Imagenes/Pasted%20image%2020250217182437.png)

- Esto significa que ==sudo== ejecute el comando como el usuario con el UID (USER ID) ==-1==. Los UIDS son números positivos que identifican a los usuarios. Sin embargo, ==-1== es un valor especial.
- El comando ==/bin/bash== se ejecutará con los privilegios del usuario especificado. En este caso, se inicia una shell de bash.
![[Pasted image 20250217182833.png]]
- Le damos a ejecutar.

![](../Imagenes/Pasted%20image%2020250217182933.png)

- Nos saldra la primera flag pero, abajo escribimos el siguiente comando:
```
:!/bin/bash
```
- Lo ejecutamos y ya seremos root.

![](../Imagenes/Pasted%20image%2020250217183053.png)

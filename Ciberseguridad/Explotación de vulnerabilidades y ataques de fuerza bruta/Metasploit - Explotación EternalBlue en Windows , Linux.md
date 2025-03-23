- Vamos a usar `"vuln"` en `nmap` para encontrar las vulnerabilidades en la maquina windows 7.

![](../Imagenes/Pasted%20image%2020241212185025.png)

- Como podemos ver, tenemos la CVE que es la vulnerabilidad que vamos a buscar en metasploit.
- Para abrir metasploit tenemos 2 formar:
	- 1.- Escribiendo el comando `msfconsole`.
	- 2.- Abriendo la herramienta como tal desde el inicio de kali (Recomendado)

![](../Imagenes/Pasted%20image%2020241212185231.png)


![](../Imagenes/Pasted%20image%2020241212185315.png)

- Para buscar las vulnerabilidades usamos el comando `search` acompañado de la CVE o del nombre de la vulnerabilidad.

![](../Imagenes/Pasted%20image%2020241212185618.png)

- Para cargar un sploit usamos el comando `use` + el numero del sploit, en este caso vamos a utilizar el sploit 0.

![](../Imagenes/Pasted%20image%2020241212185744.png)

- Ya teniendo el sploit cargado, debemos ver sus opciones de configuración. Para esto utilizamos el comando `show options`. 

![](../Imagenes/Pasted%20image%2020241212185910.png)

- Podemos ver que el sploit ya viene con un payload. El payload que es la carga útil, Es la que se ejecuta cuando el sploit entra en la maquina victima para generar la riverse shell.
- Para configurar las opciones como por ejemplo RHOSTS que seria la IP de la maquina victima usamos el comando `set` + name en mayúsculas.

![](../Imagenes/Pasted%20image%2020241212190300.png)

- Ya configurado nuestro sploit, podemos ejecutarlo con 2 comandos diferentes, `run` o `exploit`.
- Ya estamos dentro:

![](../Imagenes/Pasted%20image%2020241212190713.png)

- En este caso como estamos dentro de un windows debemos saber utilizar comandos de windows.
- Funcionan:
	- pwd
	- cd
	- dir (Enlistar)
	- mkdir

==METASPLOIT EN LINUX==

- Vamos a utilizar la maquina metasploitable2
- Tenemos nuestra maquina victima reconocida:

![](../Imagenes/Pasted%20image%2020241212192521.png)

- Vamos a escanear y buscar una vulnerabilidad para ingresar a la maquina.
- Vamos a usar `"vuln"` en unos de sus puertos, en este caso el 21.
- Encontramos una vulnerabilidad:

![](../Imagenes/Pasted%20image%2020241212193537.png)

- Vamos nuevamente a Metasploit.
- En este caso no nos encontró nada:

![](../Imagenes/Pasted%20image%2020241212193733.png)

- Vamos a probar poniendo la versión del vsFTPd.

![](../Imagenes/Pasted%20image%2020241212193856.png)

- Cargamos el sploit con el comando `use`  y lo configuramos con el comando `show options`.

![](../Imagenes/Pasted%20image%2020241212194023.png)

- Usamos el comando `run` y ya estamos dentro:

![](../Imagenes/Pasted%20image%2020241212194338.png)



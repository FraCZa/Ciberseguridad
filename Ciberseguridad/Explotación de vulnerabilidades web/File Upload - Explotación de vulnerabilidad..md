- Crear payloads, subirlo en pagina web para hacer una reverse shells. 

- Tenemos una maquina con solo el puerto 80 abierto, al ingresar nos arroja a una web login

![](../Imagenes/Pasted%20image%2020241214203105.png)

- IMPORTANTE : Si en la certificación te sale una web login donde te puedes registrar, lo ideal es hacerlo.

![](../Imagenes/Pasted%20image%2020241214203239.png)

- Ya adentro si tenemos el nombre de una web como en este caso que se llama "Cutenews dashboard", podemos investigarlo en metasploit. Pero este no es la intrusión. 
- Si apretamos en Personal options se nos abre esta ventana:

![](../Imagenes/Pasted%20image%2020241214203403.png)

- Como podemos ver tenemos la opción de subir un archivo.
- Si podemos subir archivos, existe una vulnerabilidad por ahí.
- Es importante saber, donde se ubican los archivos que uno suba. La forma de saberlo es haciendo fuzzing con `Gobuster`.
- Pero antes vamos a usar msvenom para generar un payloads que va a ser el que nos permita hacer una reverse shells.
	- En este caso lo haremos en formato .php

![](../Imagenes/Pasted%20image%2020241214204930.png)

- Lo subimos y guardamos los cambios.

![](../Imagenes/Pasted%20image%2020241214203928.png)

- Ahora no sabemos donde estará encontrado, Para eso hacemos fuzzing.

![](../Imagenes/Pasted%20image%2020241214204359.png)

- Encontramos el directorio `uploads`, vamos a ingresar y veremos el archivo que subimos. 

![](../Imagenes/Pasted%20image%2020241214204448.png)

- Este es el archivo que creamos con msfvenom.
- Ahora tenemos que dejar en escucha con `netcat` y apretamos el archivo.

![](../Imagenes/Pasted%20image%2020241214205034.png)

- Ya estamos dentro.
- IMPORTANTE: La reverse shell que generamos con Msfvenom no es tan confiable para eso vamos a abrir otra terminal dejando en escucha en puerto 444
- Vamos a ir a la pagina `revshells.com` y crear una reverse.

![](../Imagenes/Pasted%20image%2020241214205417.png)

- Copiamos la reverse.
- Y en la otra pestaña donde teníamos el escucha 443 y que ya estamos dentro ponemos lo siguiente

![](../Imagenes/Pasted%20image%2020241214205555.png)

```
bash -c "(LA_RIVERSE_SHELLS)"
```
- Y ahora si tenemos una conexón mas estable:

![](../Imagenes/Pasted%20image%2020241214205643.png)


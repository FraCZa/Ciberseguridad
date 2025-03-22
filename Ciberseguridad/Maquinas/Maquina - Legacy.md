10.10.10.4
Windows
Port:135,139,445
- Nuevamente tenemos el puerto 445, vamos a ver que encontramos dentro.
![[Pasted image 20250317191253.png]]
- Creo que no podemos ver su contenido, vamos a ver si encontramos una vulnerabilidad con nmap.
![[Pasted image 20250317191439.png]]
- Encontramos esta vulnerabilidad "ms08-067" , vamos a buscar este script.
![[Pasted image 20250317191532.png]]
- Lo encontramos, vamos a abrir metasploit.
- Configuramos y entramos como root.
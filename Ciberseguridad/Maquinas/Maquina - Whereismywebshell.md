172.17.0.2
kali
Port: 80

- Vamos a hacer fuzzing.
![[Pasted image 20250303180955.png]]
- Nos vamos a meter a warning.html
![[Pasted image 20250303181015.png]]
- Vamos a probar haciendo fuzzing en este directorio.
- Pero tampoco encontramos nada.
- La forma correcta es usar ==wfuzz==, con el siguiente codigo:
- Sabemos que el otro directorio de interes en shell.php
```
wfuzz -c -t 200 --hl=0 -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u "http://172.17.0.2/shell.php?FUZZ=id"

```
![[Pasted image 20250303183520.png]]
- Ahora ponemos ese dato en la URL.
![[Pasted image 20250303183624.png]]
- Ya podemos ejecutar comandos en la pagina web.
![[Pasted image 20250303183648.png]]
- Como podemos ejecutar comandos, podemos hacer una reverse shell
![[Pasted image 20250303184211.png]]
- Pero las & hay que cambiarlas por %26 para que sean reconocidas en la URL.
![[Pasted image 20250303184232.png]]
- Ya estamos dentro.
![[Pasted image 20250303184517.png]]

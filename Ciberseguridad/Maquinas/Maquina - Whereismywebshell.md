172.17.0.2
kali
Port: 80

- Vamos a hacer fuzzing.

![](../Imagenes/Pasted%20image%2020250303180955.png)

- Nos vamos a meter a warning.html


![](../Imagenes/Pasted%20image%2020250303181015.png)

- Vamos a probar haciendo fuzzing en este directorio.
- Pero tampoco encontramos nada.
- La forma correcta es usar ==wfuzz==, con el siguiente codigo:
- Sabemos que el otro directorio de interes en shell.php
```
wfuzz -c -t 200 --hl=0 -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u "http://172.17.0.2/shell.php?FUZZ=id"

```

![](../Imagenes/Pasted%20image%2020250303183520.png)

- Ahora ponemos ese dato en la URL.

![](../Imagenes/Pasted%20image%2020250303183624.png)

- Ya podemos ejecutar comandos en la pagina web.

![](../Imagenes/Pasted%20image%2020250303183648.png)

- Como podemos ejecutar comandos, podemos hacer una reverse shell

![](../Imagenes/Pasted%20image%2020250303184211.png)

- Pero las & hay que cambiarlas por %26 para que sean reconocidas en la URL.

![](../Imagenes/Pasted%20image%2020250303184232.png)

- Ya estamos dentro.

![](../Imagenes/Pasted%20image%2020250303184517.png)


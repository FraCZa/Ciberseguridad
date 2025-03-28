Port:80, 445, 139

- En esta maquina lo que nos va interesar son los puertos 80  y 445. 
- Como no tenemos puerto 22, lo mas probable es que tengamos que hacer una reverse en la URL de la maquina enemiga.
- Sabemos que el puerto 445 corre un servidor SAMBA, vamos a ver la pagina web para ver que encontramos.

![](Ciberseguridad/Imagenes2/Pasted%20image%2020250328175620.png)

- Vamos a hacer fuzzing web.

![](Ciberseguridad/Imagenes2/Pasted%20image%2020250328175951.png)

- No encontramos nada interesante. 
- Vamos a utilizar smbmap para encontrar algo de información.
- En el puerto 139 no tenemos conexión.


![](Ciberseguridad/Imagenes2/Pasted%20image%2020250328180208.png)

- Vamos a usar la herramienta rpcclient :
```
rpcclient -U '' -N (IP_VICTIMA)
```


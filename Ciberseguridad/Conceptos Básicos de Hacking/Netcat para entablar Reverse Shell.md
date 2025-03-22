- Nos permite tener una conexión por parte de la maquina victima.
- Vamos a utilizar una pagina para generar un Reverse Shell llamada:
```
revshells
```
#Solo_abrir_en_las_Maquinas_Virtuales
![](../Imagenes/Pasted%20image%2020241211183850.png)
- Para rellenar los espacios:
	- Primero usamos la opción `Bash -i` 
	- Después ponemos la IP atacante (La nuestra).
	- Por ultimo usamos el puerto, Por lo general se usa el 443.
- Como consecuencias obtenemos lo siguiente:

![](../Imagenes/Pasted%20image%2020241211184210.png)
- Ya teniendo esta información vamos a poner en modo escucha nuestra maquina atacante usando el comando:
```
nc -nlvp 443
```

![](../Imagenes/Pasted%20image%2020241211184342.png)

- Ahora, en la maquina victima vamos a ocupar el Reverse Shell que nos entrego la pagina.
![[Pasted image 20241211184536.png]]
- Ya estamos dentro.

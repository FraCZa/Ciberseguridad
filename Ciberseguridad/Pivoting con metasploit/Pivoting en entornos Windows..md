- Primero vamos a hacer la intrusión a la maquina Windows 7 para posterior hacer Pivoting para la tercera maquina.
- Vamos a explotar una vulnerabilidad por ==metasploit== como ya se a echo.
- Vamos a ejecutar `search eternalblue` para ingresar.

![](../Imagenes/Pasted%20image%2020250112160615.png)

- Usamos este.
- Revisamos que falta por ingresar, ingresamos la IP victima (Windows 7)

![](../Imagenes/Pasted%20image%2020250112160836.png)
- Ejecutamos comando run.

![](../Imagenes/Pasted%20image%2020250112160909.png)

- Ya estamos dentro.
- Para hacer Pivoting tenemos que estar en la session meterpreter si o si.
- Dentro de esta session usamos el comando `ifconfig`

![](../Imagenes/Pasted%20image%2020250112161122.png)

- Aquí tenemos otra IP.
- Ahora apretamos `ctrl + z` , decimos que si y nos movemos a ==msf==.

![](../Imagenes/Pasted%20image%2020250112161344.png)

- Aquí usamos el comando:
```
sessions -l
```


![](../Imagenes/Pasted%20image%2020250112161441.png)

- Y vemos la session se windows.
- Vamos a usar un modulo de metasploit que sirve para identificar otros equipos dentro de la red interna.
```
use windows/gather/arp_scanner
```


![](../Imagenes/Pasted%20image%2020250112161646.png)

- Vamos a configurarlo.

![](../Imagenes/Pasted%20image%2020250112161730.png)

- Nos pide 2 cosas:
	- 1.- SESSIONS -> La session de windows.
	- 2.- RHOSTS -> El rango entero de red que vamos a utilizar para escanear equipos.


![](../Imagenes/Pasted%20image%2020250112161948.png)

- La /24 es para decirle que escanee toda esa red interna.

![](../Imagenes/Pasted%20image%2020250112162032.png)

- Ejecutamos run.

![](../Imagenes/Pasted%20image%2020250112162138.png)

- Ya nos encontró las maquinas que están dentro de la red interna.
==IMPORTANTE --> apuntar toda esta información==
- Ya identificado, hay que enrutar el tráfico.
- Le pedimos a windows 7 que nos envíe esta información a mi maquina atacante.
```
use multi/manage/autoroute
```


![](../Imagenes/Pasted%20image%2020250112162424.png)

- Lo configuramos.

![](../Imagenes/Pasted%20image%2020250112162454.png)

- Nos pide la SESSION.
- Lo ingresamos y ejecutamos run.

![](../Imagenes/Pasted%20image%2020250112162557.png)

- Ya tenemos localizada la IP de la maquina victima y ahora el trafico enrutado.
- Ahora hacemos un escaneo de puertos abiertos.
```
use scanner/portscan/tcp
```


![](../Imagenes/Pasted%20image%2020250112162730.png)

- Lo configuramos.

![](../Imagenes/Pasted%20image%2020250112162756.png)

- Esto se parece mucho a usar nmap.
- Ingresamos en RHOSTS la IP de la maquina victima que encontramos.

![](../Imagenes/Pasted%20image%2020250112162933.png)

- Ejecutamos run.

![](../Imagenes/Pasted%20image%2020250112163018.png)

- Ya sabemos que puertos atacar.
- Vamos a ingresar por el puerto 80.
- Vamos a utilizar otro modulo.
```
use post/windows/manage/portproxy
```
- Este modulo es únicamente en WINDOWS

![](../Imagenes/Pasted%20image%2020250112163229.png)

- Lo configuramos.

![](../Imagenes/Pasted%20image%2020250112163245.png)

- Hay que llenar los ==CONNECT== y los ==LOCAL==.
- En CONNECT_ADDRESS ---> IP VICTIMA.
- CONNECT_PORT ---> El puerto que quiero atacar.
- LOCAL_ADDRESS ---> 0.0.0.0
- LOCAL_PORT ---> Puerto de donde queremos traernos el puerto que estamos atacando.

![](../Imagenes/Pasted%20image%2020250112163719.png)

- Corroboramos.

![](../Imagenes/Pasted%20image%2020250112163750.png)

- Nos faltaría ingresa la SESSION

![](../Imagenes/Pasted%20image%2020250112163829.png)

- Ahora ejecutamos run.

![](../Imagenes/Pasted%20image%2020250112163859.png)

- Ahora para poder acceder al puerto 80 de esa maquina?
```
(IP_MAQUINA WINDOWS):(IP_DONDE TRAEMOS EL PUERTO)
```


![](../Imagenes/Pasted%20image%2020250112164059.png)


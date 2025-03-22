- Encontrar equipos que estén conectados en mi red privada.


ARP-SCAN:
- Para usar esta herramienta tenemos que saber nuestra interfaz de red utilizando `ifconfig` .
- Ya sabiendo nuestra IP vamos a utilizar el siguiente comando:
```
arp-scan -I eth0 --localnet
```
![[0800.png]]
- Tenemos que la MAC es 08:00 esto es que es un sistema operativo.
- Si no tenemos la MAC vamos a usar el comando `ping` en cada una para ver si es un sistema operativo o no.
```
ping -c 1 (IP_VICTIMA)
```
![[Pasted image 20241211202408.png]]
- Como podemos ver, el ttl es 128, esto quiere decir que es un sistema operativo Windows, si fuese 64 seria Linux.

NETDISCOVER:
- Alternativa de  ARP-SCAN
- El comando seria el siguiente:
```
netdiscover -i eth0 -r (IP_ATACANTE_CON_FINAL_0 + MASCARA)
```
- El 0 es para que empiece a buscar todos los endpoint dentro de la red.
![[Pasted image 20241211203042.png]]

NMAP:
- Usamos el comando:
```
nmap -sn (IP_MAQUINA_ATACANTE_CON_FINAL_0 + MASCARA)
```
![[Pasted image 20241211203258.png]]

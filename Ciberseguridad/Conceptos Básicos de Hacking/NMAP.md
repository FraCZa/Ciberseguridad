- Usamos el comando:
```
nmap -p- --open -sS -sC -sV --min-rate 5000 -n -vvv -Pn (IP_VICTIMA) -oN Escaner
```
- En el examen se recomienda usar un min rate 2000.
- Nos entrega información detallada.
![[Pasted image 20241211204742.png]]

DETECTAR BULNERABILIDAD CON NMAP
- Usamos el siguiente comando:
```
nmap --script "vuln" -p445 (IP_QUE_QUEREMOS_VER) (IP_VICTIMA)
```
- "vuln" hace mucho ruido si se utiliza.
![[Pasted image 20241211205618.png]]
- Como podemos observar nos arroja el CVE que es la vulnerabilidad publica.

ESCANEO DE PUERTO BAJO EL PROTOCOLO UDP
- Vamos a utilizar una maquina vulnerable en la pagina `vulnyx.com`
- El comando para encontrar puertos UDP el siguiente:
```
nmap -sU --top-ports 200 --min-rate 5000 -Pn (IP_VICTIMA)
```
![[Pasted image 20241212183447.png]]


DIFERENCIA DE PROTOCOLO TCP Y UDP

TCP:
- Protocolo orientado a la conexión.
- Incluye mecanismo de control de flujo y control de congestión para evitar que los datos se pierdan o se dupliquen.
- Si un dato se pierde en la transmisión, este lo retransmite automáticamente.
- Utilizado en la navegación web (HTTP/HTTPS), transferencia de datos (FTP), correo electronico (SMTP) y mas..

UDP:
- Protocolo sin conexión que permite transmisión de datos sin establecer una conexión previa.
- No realiza control de flujo ni retransmisión de datos.
- Tiene menos sobrecarga que TCP porque no requiere mantener el estado de conexión.
- Utilizado para la transmisión de video y audio en tiempo real (VoIP), juego en línea , y servicios de streaming.
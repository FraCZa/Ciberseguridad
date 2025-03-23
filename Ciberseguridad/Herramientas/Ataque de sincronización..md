
- Es un tipo de ataque de canal lateral. Esto significa que no ataca el algoritmo criptográfico en si, sino la manera en que se implementa y ejecuta.
- En el caso de la maquina HackerNote, al ingresar un usuario correcto y una contraseña incorrecta se demora mas en decir que los datos no son correctos que ingresar un usuario incorrecto y una contraseña correcta.
	- Esto quiere decir que el código esta echo para identificar primero si el usuario es correcto y eso causa que el mensaje de error aparezca mas rápido.
		- Si el usuario no existe automáticamente el mensaje saldra mas rápido.
	- Si el usuario es correcto entonces tiene que verificar si la contraseña es correcta, por ende el mensaje se demoraría en aparecer.

- Si usamos ==Burp Suite== podemos ver que el método de el login es ==POST==.
	- POST---> Método HTTP utilizado para enviar datos al servidor.
		- Se utiliza principalmente para enviar datos desde el cliente al servidor. Esto es común en formularios web donde ingresas datos como tu nombre, dirección, etc.

![](../Imagenes/Pasted%20image%2020250130191701.png)

- Como sabemos que es ==POST== podemos hacer una solicitud ==CURL==
	- CURL(cliente URL)---> Herramienta que sirve para transmitir datos a o desde un servidor utilizando varios protocolos. Se utiliza principalmente para interactuar con servidores web.
		- Se puede utilizar para hacer solicitudes GET, ==POST==, PUT, DELETE y otros tipos de solicitudes HTTP.
		- Se puede descargar archivos desde un servidor remoto con CURL.
		- Permite subir archivos a un servidor.
- Si queremos verificar cuanto tiempo se demora en reacción con credenciales incorrecta, tenemos que crear un ==script== en Python.

![](../Imagenes/Pasted%20image%2020250130195620.png)

- ==import==: Se importa las bibliotecas `request` y `time`.
	- `request`---> Realiza solicitudes HTTP.
	- `time`---> Es para medir el tiempo de ejecución.
- ==url== : Se define la URL a la que se enviará la solicitud POST.
- ==data==: Contiene las credenciales de inicio de sesión del usuario. En este caso los datos son incorrectos.
- ==startTime==: Con `time.time()` se almacena el tiempo actual en la variable ==startTime==para medir el tiempo que tarda en completarse la solicitud.
- ==r==: Se realiza una solicitud POST a la URL definida, enviando los datos de inicio de sesión. La respuesta de la solicitud se almacena en la variable ==r==.
- ==print==: Se calcula el tiempo transcurrido desde que se almacenó `startTime` y se imprime en la consola.
- Lo ejecutamos.

![](../Imagenes/Pasted%20image%2020250130195639.png)

- Ahora vamos a hacerlo nuevamente pero con el usuario correcto.

![](../Imagenes/Pasted%20image%2020250130195750.png)

- Con esto reafirmamos lo que ya sabemos.
- Ahora vamos a modificar el ==sprint== para saber que otros usuarios podemos encontrar en la pagina:
- Lo agregamos debajo de ==URL==

![](../Imagenes/Pasted%20image%2020250130200137.png)

- ==open("usr", "r")==: Este comando abre un archivo llamado "usr" en modo lectura ("r").
- ==.readlines()== Este método lee todas las líneas del archivo y las devuelve como una lista de cadenas (strings), cada una representando una línea del archivo.
- Ahora vamos a crear un bucle que nos permitirá usar cada nombre de usuario encontrado en la pagina.

![](../Imagenes/Pasted%20image%2020250130204436.png)



172.17.0.2
Kali
Port: 22, 80.
- No encontramos nada interesante en la pagina web, asi que haremos fuzzing.

![](../Imagenes/Pasted%20image%2020250306170458.png)

- Si nos metemos al directorio /index.php , nos saldra lo siguiente.

![](../Imagenes/Pasted%20image%2020250306170528.png)

- Tenemos una posible contraseña, vamos a ver si hydra nos da algo.

![](../Imagenes/Pasted%20image%2020250306170608.png)

- Tenemos un usuario, vamos a ver si nos permite entrar al puerto 22.

![](../Imagenes/Pasted%20image%2020250306170742.png)

- Ya estamos dentro, vamos a investigar si tenemos mas usuarios dentro de esta maquina.

![](../Imagenes/Pasted%20image%2020250306170821.png)

- No tenemos mas usuarios, vamos a escalar privilegios.

![](../Imagenes/Pasted%20image%2020250306170849.png)

- Todos los usuarios de esta maquina pueden ejecutar como root el script.py.
- Vamos a ver que tiene el escript dentro.

![](../Imagenes/Pasted%20image%2020250306171017.png)

- Tenemos algo en la línea de ==if==, vamos a ver si podemos sacar provecho a eso.
- Pero básicamente nos dice que se copia el archivo script.py y se desplaza a el lugar de destino.
- Lo que podemos hacer es eliminarlo y crear un nuevo script.py con el siguiente código dentro:
```
import os

os.system("/bin/sh")
```
- Este utiliza el módulo `os` para ejecutar un comando en el sistema operativo.
- El comando `os.system` permite ejecutar un comando en la shell del sistema operativo.
- El comando `("/bin/sh")` Es la ruta del interprete shell en sistema Unix/linux.
- Ahora ejecutamos el script como se nos enseño al momento de escribir sudo -l.

![](../Imagenes/Pasted%20image%2020250306172551.png)


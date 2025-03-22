- Como saber si la maquina victima es windows:
    - Podemos usar la opción `-O` en `nmap`
    - Los puertos `139 y 445` corresponden a puertos windows

## Enum4linux

- Herramienta de enumeración utilizada para pruebas de penetración y auditoria en Windows.
- Puede descubrir recursos y directorios compartidos en la red.
- Puede recolectar detalles sobre el dominio al que pertenece el sistema.
- Puede extraer información sobre la configuración de red del sistema objetivo.
- Puede listar los usuarios y grupos presentes en el sistema operativo objetivo
- El comando es:

`enum4linux -a (IP) | tee enum4linux.log`
![[Pasted image 20250113174954.png]]

## LinPEAS (Linux Privilege Escalation Awesome Script)

- Herramienta de script de Bash.
- Identifica posibles oportunidades de escalada de privilegios en sistemas linux
- Usa colores para resaltar los puntos críticos en el informe.

## Como instalar

- `LinPEAS` funciona como script
- Vamos a copiar el código de este script de la pagina: [https://github.com/Cerbersec/scripts/blob/master/linux/linpeas.sh](https://github.com/Cerbersec/scripts/blob/master/linux/linpeas.sh)
- Creamos una carpeta donde guardaremos nuestro fichero
- Dentro nuestro fichero
![[Pasted image 20250113174224.png]]
- Pegamos el script y guardamos
![[Pasted image 20250113174251.png]]
`#Guardamos escribiendo :wq`

- Le damos permiso de ejecución (+x)
- Ejecutamos:
![[Pasted image 20250113174316.png]]
- Ejemplo de comando para usarlo:
- Primero debemos cargar nuestro linpeas a la maquina victima
![[Pasted image 20250113174357.png]]
- En la maquina victima le vamos a dar permiso para ajecutarse
    
- Ahora ejecutamos con el siguiente comando:
    
    - `./linpeash.sh | tee linlog.txt`
    
    `#Se ejecuta linpeas y se guarda en un archivo llamado "linlog.txt"`
![[Pasted image 20250113174434.png]]
## Significado de cada color

- RED/YELLOW → Vectores de escalada de privilegios.
- RED → Resalta elementos que merecen una revisión más detallada.
- Lightcyan → Usuarios que tienen una consola asociada.

`#consola asociada -> Usuario tiene una shell o intérprete de comandos. Posee /etc/passwd`

- Blue → Usuarios que no tienen una consola asociada.
- Green → Elementos comunes como usuarios, grupos, archivos con permiso SUID/SGID, puntos de montaje, scripts y tareas programadas.
- LightMangenta → Señala tu propio nombre de usuario.

==Binarios==
![[Pasted image 20250113174506.png]]
- Como podemos ver, tenemos bin/ sudo. Podemos usar `sudo -l`
- Si seguimos investigando podemos encontrar una `key`
![[Pasted image 20250113174526.png]]
- La encontramos
![[Pasted image 20250113174552.png]]
- Vemos su contenido
![[Pasted image 20250113174613.png]]
- Copiamos la key
![[Pasted image 20250113174630.png]]
- Al crear la llave y ejecutarla, si nos pide la contraseña es porque algo salió mal.
- Para eso vamos a descifrar la contraseña usando una herramienta de cracking de contraseña
- Para descargar esta herramienta clonamo el git:

`git clone <https://github.com/openwall/john.git`>

- Compilamos

`cd john/src`

`./configure && make`

- Si preferimos instalarlo desde los repositorios de tu distribución de Linux:

`sudo apt-get install john`

- Usamos el siguiente comando para codificar la `key` y pasarla a otro archivo `.txt`
![[Pasted image 20250113174651.png]]
- Para hacerle fuerza bruta usamos el comando
![[Pasted image 20250113174716.png]]
- Y entramos:
![[Pasted image 20250113174735.png]]
#-i es para usar la key

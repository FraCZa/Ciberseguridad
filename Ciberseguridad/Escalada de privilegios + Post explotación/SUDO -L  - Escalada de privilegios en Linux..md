sudo -l --> Se utiliza en sistemas Unix y Linux para listar los comandos que un usuario puede ejecutar con privilegios elevados mediante el uso del comando sudo.
- Vamos a hacer la intrusión para luego hacer la escalada de privilegios.


- Vamos a hacer el tratamiento de la ==TTY==.
- Ya listo el ==TTY== , vamos  a probar con el comando `sudo -l`.
![[Pasted image 20250110184542.png]]
- Podemos ver que podemos correr como `sudo`, ==vim==.
- Para ver como podemos escalar este binario nos metemos a la siguiente pagina web:
https://gtfobins.github.io
![[Pasted image 20250110184736.png]]
- Vamos a buscar el binario ==vim==.
![[Pasted image 20250110184825.png]]
- Entramos en la segunda opción.
- Buscamos en el apartado de sudo, ya que con este comando nos salió el binario ==vim==.
![[Pasted image 20250110184932.png]]
- Vamos a copiar la opción A
- Lo ingresamos en el panel de comando y ya escalamos como root.
![[Pasted image 20250110185105.png]]
- Puede que no funcione el comando, para esto vamos a usar la ruta absoluta:
```
sudo /usr/bin/vim -c ':!/bin/sh'
```
- Si en alguna maquina nos están pidiendo la red flag de root, para encontrarla usamos el comando:
```
cat /root/root.txt
```

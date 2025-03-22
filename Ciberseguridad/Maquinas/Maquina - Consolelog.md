172.17.0.2
kali
Port: 80, 3000, 5000.
- No encontramos nada interesante en las paginas web, asi que vamos a hacer Fuzzing.
![[Pasted image 20250306174746.png]]
- El que nos interesa es el directorio /backend.
![[Pasted image 20250306174816.png]]
- Buscamos informacion valiosa.
- En server.js encontramos una contraseña:
![[Pasted image 20250306174859.png]]
- Vamos a hacer fuerza bruta para encontrar el usuario.
![[Pasted image 20250306180452.png]]
- Encontramos nuestro usuario, vamos a ingresar por el puerto 5000 que en este caso es el ssh.
![[Pasted image 20250306180554.png]]
- Especificamos que el puerto es el 5000.
![[Pasted image 20250306180618.png]]
- Vamos a ver si tenemos mas usuarios dentro de la maquina y si también encontramos información importante.
![[Pasted image 20250306180701.png]]
- Tenemos a tester, pero aun no se si sea necesario ingresar en el.
- Vamos a ver si podemos escalar con el comando sudo.
![[Pasted image 20250306180751.png]]
- Podemos usar el binario nano para escalar.
- Sabemos que nano es una herramienta para crear y editar archivos de textos, podemos meternos al directorio /passwd para borrar la necesidad de que nos pidan password para escalar como root.
- Para esto eliminamos la X de root.
![[Pasted image 20250306181132.png]]
- Ahora solo escribimos `su root`, ya somos root.
![[Pasted image 20250306181219.png]]

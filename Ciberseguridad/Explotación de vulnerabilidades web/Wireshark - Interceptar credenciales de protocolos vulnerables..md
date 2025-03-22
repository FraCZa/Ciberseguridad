- Vamos a utilizarlo para ver tráficos de red.
- Vamos a poder ver la información que pasa por diferentes puertos.
- Abrimos ==wireshark==, lo dejamos escuchando en ==eth0==.
![[Pasted image 20241220163632.png]]
- Vamos a entrar por ftp, de la maquina metasploitable2.
![[Pasted image 20241220163943.png]]
- Si nos vamos a ==wireshark== y filtramos por ftp, nos saldra todos los datos recolectados:
![[Pasted image 20241220164106.png]]
- Como esta información no esta encriptada, con ==wireshark== podemos ver credenciales:
![[Pasted image 20241220164155.png]]
 - Esto lo podemos lograr con cualquier otro puerto.

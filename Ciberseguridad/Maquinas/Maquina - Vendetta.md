172.17.0.2
kali
Port: 22, 80, 3306
- Tenemos un puerto 3306 donde corre SQL pero antes de ver que podemos sacar de ahí, vamos a  hacer Fuzzing y revisar la pagina.

![](../Imagenes/Pasted%20image%2020250306182829.png)

- Vemos que debajo de la primera imagen, la "V" esta mas oscura, quizás sea una pista. Vamos a hacer Fuzzing.
- No encontramos nada en el fuzzing.
- Vamos a hacer fuerza bruta con la "V" en el puerto mysql, quedaria de esta manera:
```
hydra -l V -P /usr/share/wordlists/rockyou.txt mysql://172.17.0.2
```

- Buscar directorios en una pagina web.
- Vamos a utilizar la herramienta gobuster con el siguiente comando:
```
gobuster dir -u http://(IP_VICTIMA) -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt
```

![](../Imagenes/Pasted%20image%2020241214174111.png)

- También podemos buscar estaciones de archivos agregando el comando:
```
-x php,thml,js,txt
```

- Si en el examen no esta instalada la herramienta Gobuster podemos usar otra alternativa, dirb

```
dirb http://(IP_VICTIMA)
```

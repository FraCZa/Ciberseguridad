- Herramienta para analizar y extraer datos de archivos binarios.
- Si queremos sacar información de una imagen y se nos presenta una contraseña, es posible conseguirla a través de esta herramienta.
- Para extraer la información usamos el siguiente comando:
```
binwalk -e (NOMBRE_IMAGexiftool (NOMBRE_IMAGEN)
```

![](../Imagenes/Pasted%20image%2020250119175437.png)

- Si nos sale este error es porque hay muchas utilidades de terceros para la extracción, las cuales podrían no ser seguras.
- Ahí nos recomienda usar el comando ==--run-as=root==.
- Quedaría de esta forma:
```
binwalk -e --run-as=root (NOMBRE_IMAHEN)
```

![](../Imagenes/Pasted%20image%2020250119175727.png)

- Si entramos a la carpeta que extrajimos vamos a encontrar la información que tiene dentro, en este caso hay un archivo zip, para descomprimirlo vamos a usar el siguiente comando:
```
7z e (NOMBRE_ARCHIVO)
```

![](../Imagenes/Pasted%20image%2020250119180320.png)

- Pero como tiene contraseña la vamos a crackear con ==john==
- Usamos el siguiente comando:
```
zip2hohn (NOMBRE_ARCHIVO) > (NUEVO_NOMBRE.hash)
```

![](../Imagenes/Pasted%20image%2020250119181320.png)

- Ahora usamos ==john== en zip.hash

![](../Imagenes/Pasted%20image%2020250119181332.png)



==steghide== (JPG)
- Se utiliza para realizar esteganografía, que es el proceso de ocultar información dentro de archivos multimedia.
- Si lo vamos a utilizar para decodificar una imagen .jpg, el comando seria asi:
```
steghide extract -sf (NOMBRE_IMAGEN)
```

![](../Imagenes/Pasted%20image%2020250119182134.png)


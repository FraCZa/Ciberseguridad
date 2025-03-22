Hotfixes --> Actualización rápida de software diseñada para solucionar un problema específico o una vulnerabilidad de seguridad en una aplicación o sistema.

- Como enumerarlos:
- cuando hacemos una intrusión a Windows tenemos la cmd

![](../Imagenes/Pasted%20image%2020250106171537.png)

- Dentro de la cmd usamos el siguiente comando:
```
powershell
```

![](../Imagenes/Pasted%20image%2020250106171614.png)

- Ahora usamos el comando:
```
Get-HotFix
```
- Este comando nos lista los parches o los HotFix del sistema.

![](../Imagenes/Pasted%20image%2020250106171729.png)

- Para enumerarlos usamos el siguiente comando:
```
(Get-HotFix).Count
```

![](../Imagenes/Pasted%20image%2020250106171826.png)

- También los podemos enumerar con el siguiente comando:
```
wmic qfe list brief /format:table
```

![](../Imagenes/Pasted%20image%2020250106171954.png)


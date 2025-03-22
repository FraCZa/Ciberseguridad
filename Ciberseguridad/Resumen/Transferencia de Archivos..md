

1. **netcat**
    
    - **Función**: Transferencia de archivos y conexiones remotas.
        
    - **Puerto**: Varía.
        
    - **Comando**: `nc -lvp <puerto>` (escuchar), `nc <IP> <puerto>` (conectar).
        
2. **wget**
    
    - **Función**: Descargar archivos desde la web.
        
    - **Puerto**: 80/443 (HTTP/HTTPS).
        
    - **Comando**: `wget <URL>`.
        
3. **smbget**
    
    - **Función**: Descargar archivos desde recursos SMB.
        
    - **Puerto**: 445 (TCP).
        
    - **Comando**: `smbget smb://<IP>/<ruta>`.
        
4. **impacket-smbserver**
    
    - **Función**: Crear un servidor SMB compartido.
        
    - **Puerto**: 445 (TCP).
        
    - **Comando**: `impacket-smbserver <nombre> <directorio>`.
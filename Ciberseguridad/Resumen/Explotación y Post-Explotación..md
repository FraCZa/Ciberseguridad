

1. **metasploit**
    
    - **Función**: Framework para explotación de vulnerabilidades.
        
    - **Puerto**: Varía según el módulo.
        
    - **Comando**: `msfconsole`.
        
2. **msfvenom**
    
    - **Función**: Crear payloads para explotación.
        
    - **Puerto**: Varía según el payload.
        
    - **Comando**: `msfvenom -p <payload> LHOST=<IP> LPORT=<puerto> -f <formato>`.
        
3. **meterpreter**
    
    - **Función**: Sesión interactiva post-explotación.
        
    - **Puerto**: Varía según el payload.
        
    - **Comando**: Usado dentro de Metasploit.
        
4. **evil-winrm**
    
    - **Función**: Conexión a servidores Windows Remote Management.
        
    - **Puerto**: 5985 (HTTP) o 5986 (HTTPS).
        
    - **Comando**: `evil-winrm -i <IP> -u <usuario> -p <contraseña>`.
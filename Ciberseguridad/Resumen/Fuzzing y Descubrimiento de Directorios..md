1. **wfuzz**
    
    - **Función**: Fuzzing de aplicaciones web.
        
    - **Puerto**: Varía según el servicio.
        
    - **Comando**: `wfuzz -c -z file,<diccionario> <URL>`.
        
2. **dirb**
    
    - **Función**: Descubrimiento de directorios web.
        
    - **Puerto**: 80/443 (HTTP/HTTPS).
        
    - **Comando**: `dirb <URL> <diccionario>`.
        
3. **gobuster**
    
    - **Función**: Descubrimiento de directorios y subdominios.
        
    - **Puerto**: 80/443 (HTTP/HTTPS).
        
    - **Comando**: `gobuster dir -u <URL> -w <diccionario>`.
        
4. **dirsearch**
    
    - **Función**: Escaneo de directorios web.
        
    - **Puerto**: 80/443 (HTTP/HTTPS).
        
    - **Comando**: `dirsearch -u <URL> -e <extensiones>`.
        
5. **ffuf**
    
    - **Función**: Fuzzing rápido de aplicaciones web.
        
    - **Puerto**: 80/443 (HTTP/HTTPS).
        
    - **Comando**: `ffuf -w <diccionario> -u <URL>`.

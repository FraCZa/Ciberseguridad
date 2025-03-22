1. **hydra**
    
    - **Función**: Fuerza bruta a servicios de autenticación.
        
    - **Puerto**: Varía según el servicio.
        
    - **Comando**: `hydra -l <usuario> -P <diccionario> <IP> <servicio>`.
        
2. **john**
    
    - **Función**: Crackeo de contraseñas.
        
    - **Puerto**: No aplica.
        
    - **Comando**: `john --wordlist=<diccionario> <archivo_hash>`.
        
3. **hashcat**
    
    - **Función**: Crackeo de hashes usando GPU.
        
    - **Puerto**: No aplica.
        
    - **Comando**: `hashcat -m <modo> <hash> <diccionario>`.
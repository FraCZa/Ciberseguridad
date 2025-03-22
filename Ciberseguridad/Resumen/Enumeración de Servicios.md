1. **smbclient**
    
    - **Función**: Interactuar con recursos compartidos SMB.
        
    - **Puerto**: 445 (TCP).
        
    - **Comando**: `smbclient -L <IP> -U <usuario>`.
        
2. **smbmap**
    
    - **Función**: Enumerar permisos en recursos SMB.
        
    - **Puerto**: 445 (TCP).
        
    - **Comando**: `smbmap -H <IP>`.
        
3. **rpcclient**
    
    - **Función**: Interactuar con servicios RPC.
        
    - **Puerto**: 135 (TCP).
        
    - **Comando**: `rpcclient -U <usuario> <IP>`.
        
4. **onesixtyone**
    
    - **Función**: Enumerar información SNMP.
        
    - **Puerto**: 161 (UDP).
        
    - **Comando**: `onesixtyone -c <comunidad> <IP>`.
        
5. **snmpwalk**
    
    - **Función**: Recorrer información SNMP.
        
    - **Puerto**: 161 (UDP).
        
    - **Comando**: `snmpwalk -c <comunidad> -v1 <IP>`.
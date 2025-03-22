
1. **nmap**
    
    - **Función**: Escaneo de puertos y detección de servicios.
        
    - **Puerto**: Varía según el objetivo.
        
    - **Comando**: `nmap -sV -p- <IP>` (detección de vulnerabilidades: `nmap --script vuln <IP>`).
        
2. **arp-scan**
    
    - **Función**: Escaneo de dispositivos en la red local usando ARP.
        
    - **Puerto**: No aplica (capa 2).
        
    - **Comando**: `arp-scan -l`.
        
3. **ping**
    
    - **Función**: Verificar conectividad con un host.
        
    - **Puerto**: No aplica (ICMP).
        
    - **Comando**: `ping <IP>`.
        
4. **netdiscover**
    
    - **Función**: Descubrir hosts en la red usando ARP.
        
    - **Puerto**: No aplica (capa 2).
        
    - **Comando**: `netdiscover -i <interfaz>`.
        
5. **dig**
    
    - **Función**: Consultas DNS.
        
    - **Puerto**: 53 (UDP/TCP).
        
    - **Comando**: `dig @<DNS> <dominio>`.
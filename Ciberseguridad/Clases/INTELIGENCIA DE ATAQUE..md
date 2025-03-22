
# Modulo 1.

**Ataques informáticos.**

- Seguridad de la información
    - La información es el activo más preciado que posee una organización.
    - La información abarca también lo que se escribe en un papel, lo que se dice de manera oral, etc.
- Normas ISO/IEC 27001.
    - Disciplina que tiene como objetivo la confidencialidad, integridad y disponibilidad de la información.
- Defensa en profundidad.
    - Implementa varias medidas de seguridad en todo el perímetro con el objetivo de proteger un mismo activo (la información).
    - Estrategia de la seguridad de la información.
- Modelo de defensa en profundidad:
    - Políticas, procedimientos y concientización dentro de una organización.
    - Seguridad física (Control de acceso).
    - Seguridad del perímetro.
    - Seguridad de la red.
    - Seguridad del equipo terminal.
    - Seguridad de las aplicaciones de uso común.
    - Seguridad de los datos.
- Foco de las medidas.
    - Personas: Deben estar informadas acerca de las amenazas y deben estar capacitadas. Deben cumplir políticas de seguridad internas.
    - Tecnología: Estipular políticas que aseguren que las tecnologías implementadas son las correctas para la organización.
    - Operaciones: Actividades necesarias para sostener la seguridad de la organización en las tareas cotidianas.
- Personalidades de la seguridad informática.
    - Hacker: Persona experta capaz de vulnerar sistemas.
    - Crackers: Persona que viola o rompe la seguridad de un sistema
    - Newbie: Define a los principiantes.
    - Lammers: Personas que presumen tener conocimientos de ataques informáticos, pero no poseen conocimiento alguno.
    - Phreaker: Hacker orientados a los sistemas telefónicos que informáticos.
    - Script Kiddie: “Hacker” pero utilizan programas de terceros para realizar ataques sin conocer su funcionamiento. Suelen ser victimas de ataques ellos mismos.
- Pilares de la seguridad informáticas
    - CIA → Confidencialidad, integridad y disponibilidad.

**Tipos de ataques informáticos.**

- Ataques al sistema operativo
    - Es el más clásico.
    - La búsqueda de fallas se centra en el propio sistema operativo.
- Existen 3 líneas principales de ataques del tipo sistema operativo.
    - Windows:
        - Es más atacado.
        - Simple de acceder a su núcleo.
    - Linux :
        - Por tener código abierto son un punto de ataque peor que Windows.
    - MacOS:
        - Sufren ataques en menor medida por ser menos populares.

`Un error en el sistema base hace que todo el resto tiemble.`

`Ataques al sistema operativo -> Engloba librerías o bibliotecas.`

- Ataques a la aplicaciones.
    - La variedad de ataques es mucho mayor.
    - Los atacantes siempre buscan aplicaciones de uso masivo. Tienen más llegada a las personas y empresas.
    - Es indispensable evitar instalar software que no se requiera.
- Ataques a las configuraciones.
    - Pueden ser del sistema operativo o de las aplicaciones.
    - Una mala configuración puede transformarlo en totalmente inseguro y fácil de manejar por un atacante.

`#Una de las formas mas usadas y efectivas para reducir los atques que explotan estas vulnerabilidades es a traves de hardering (endurecimiento)`

- Ataques a protocolos.
    - Es menos frecuente pero más grave si contamos con errores en los protocolos.
    - Protocolo TCP/IP → Paquete de protocolo efectivo y flexible que perdura en el tiempo y continúa utilizándose.
## Evaluación de seguridad en dispositivos.

- Evaluación de vulnerabilidades
    
    - Búsqueda de debilidades en los distintos sistemas.
    - Se busca determinar las amenazas, los agentes de amenazas o las vulnerabilidades a la puede estar expuestas
    - Se refiere a todas aquellas de carácter técnico que dependen de las cualidades intrínsecas del sistema que se está evaluando.
- OVAL (Open Vulnerability and Assessment Langugage):
    - Estándar internacional de seguridad de la información abierto.
    - Su objetivo es promocionar y publicar contenido de seguridad y normalizar la transferencia de este por todo el espectro de herramientas y servicios de seguridad.
    - Etapas de un proceso de evaluación de vulnerabilidades:
        - Recabar información que se asocie a vulnerabilidades.
        - Analizar el sistema para determinar su estado.
        - Reportar, por medio de informes, los resultados de la evaluación llevada a cabo.
- Test de penetración y hacking ético: 
    - Evaluación de vulnerabilidades.
- Análisis de brecha de cumplimiento:
    - tiene como objetivo medir la distancia entre el estado actual de una organización y las regulaciones o estándares.
- Clasificación de la evaluación de seguridad informática
    - Herramientas que se utilizan para llevar adelante el proceso de evaluación de vulnerabilidades.
- En función de las herramientas:
    - Testeo manual y automatizado.
    - Escaneo de puertos, exploración y búsqueda de vulnerabilidades.
    - Existen herramientas automatizadas capaces de encontrar alguna vulnerabilidad y explotarla.
- En función del lugar desde donde se hace el análisis:
    - Se debe considerar si el testeo de vulnerabilidades se va a realizar de forma interna o externa.
    - Externa → Se realizará a distancia y de forma remota.
    - Interna → Un analista de seguridad se hará presente en la organización a fin de analizar de forma exhaustiva los sistemas desde dentro de ella.
    - Análisis interno → Evalúa todos aquellos puntos relacionados con la red interna y la información.
    - Análisis externo → Todas las pruebas se realizan de forma remota y se buscan vulnerabilidades en la frontera. (Firewalls o servicios que brinden internet o por medio de la red.)
- En función el alcance del análisis.
    
    - Test de intrusión
        - Proceso que debe llevar adelante un atacante real para robar los activos de la organización.
    - El test de intrusión tiene otras clasificaciones:
        - White box(Caja blanca)
            - Quien solicita el análisis le provee a quien lo realiza la información relativa a la organización.
            - Entrega bloques de direcciones IP, credenciales de acceso, estructura de servidores, etc.
        - Black box o blind(Caja negra)
            - Quien lleva a cabo el análisis no recibe ningún tipo de información.
            - Sima de forma más real el comportamiento que tendría un ataque.
        - Grey box (Caja gris)
            - Es una mezcla entre `white box` y `black box`
- Informe final
    
    - Realizar un informe donde se vuelque todo el trabajo realizado durante la evaluación.

## Fases de ataques informáticos.

- Recolección de información
    - Parte de la etapa de revelamiento.
    - Es una de las más importantes antes de emular un ataque.
    - Es la instancia previa a la ejecución de un ataque.
- Ingeniería social.
    - Tiene como objetivo las personas y el engaño a estas.
    - Método basado puramente en el engaño y la persuasión.
- Fuerza bruta.
    - Conseguir información mediante prueba y error.
    - Se explota con credenciales de acceso o contraseñas de software.

## Unidad 2. Anatomía de un ataque informático

## Etapa de relevamiento

- Whois
    - Revela información de carácter administrativo que se encuentre disponible de forma pública por medio de los registros de internet.
    - Podemos obtener información de dominio, nombre de la persona responsable de ese dominio, correo electrónico, numero de teléfono y direcciones IP.
- Traceroute
    - Identifica el camino que sigue un paquete de datos desde un equipo hasta el objetivo.
- Maltego
    - Recolecta datos.
    - Presenta datos.

# Modulo 3 Detección y mitigación de intrusos.

## Amenazas, vulnerabilidades y controles

- Seguridad informática como profesión
    - Tener relación con todas las áreas de una organización y con todas las personas que la componen.
    - Capacitación continua
- Metodologías de trabajo.
    - Contar con bases sólidas sobre las que podamos trabajar.
- Defensa en profundidad
    - Implementar medidas de seguridad con el objetivo de proteger un mismo activo.
    - Táctica que utiliza varias capaz y cada una de ellas provee un nivel de protección adicional a las demás para controlar las amenazas.
- Principio de KISS (Keep it simple, stupid → “Mantenlo simple, tonto”)
    - Implementación de partes sencillas, comprensibles y con errores de fácil detección y corrección.
    - Rechaza lo complicado e innecesario del desarrollo de una solución.
- Métricas de seguridad
    - Métrica con enfoque técnico:
        - Analizar en qué puntos podemos mejorar.
        - Qué vulnerabilidades debemos atacar primero.
        - Qué medidas de seguridad están teniendo éxito.
    - Métrica situación con respecto a la seguridad:
        - Qué se mejoro.
        - Qué se debe mejorar.
        - Existen nuevas problemáticas que necesitamos resolver.
- Análisis cualitativo versus análisis cuantitativo.
    - Cualitativos:
        - Utilizan una escala del 1 al 10 para reflejar la importancia que se le otorga a cada uno.
        - Se basan en la percepción de necesidad que tienen las personas sobre un activo.
    - Cuantitativos:
        - Se asignan valores monetarios a cada uno de los activos.
        - Estos análisis son más exactos y más fáciles de entender, pero requieren mas trabajo.
## Amenazas y vulnerabilidades.

- Vulnerabilidad:
    - Debilidad en algún software.
    - Ausencia o debilidad en uno o más controles.
- Amenaza:
    - Cualquier peligro potencial sobre la información o los sistemas.
    - Es alguien o algo que aprovecha una vulnerabilidad existente.
- Exposición:
    - Impacto negativo que se puede llegar a tener si una vulnerabilidad es explotada.
    - Daño probable.
- Riesgo:
    - Resultado de la vulnerabilidad, la amenaza, la exposición y la probabilidad de explotación.
- Contramedida:
    - Se utiliza para mitigar los riesgos y puede estar atada a una configuración de software.
## Implementación de controles

- Cuando tenemos identificados los riesgos, debemos elegir cómo vamos a reaccionar a cada uno de ellos.
- Mitigar:
    - Implementar medidas de seguridad para reducir o eliminar un riesgo
- Transferir:
    - Pasarle el riesgo a otra organización, se deberá contratar un seguro para el activo que queramos proteger.
- Evadir:
    - Eliminar la fuente que lo produce, dejar de usar el activo o proceso que lo produce con tal de no sufrir los riesgos que se asocian a él.
- Aceptar:
    - Utilizado cuando ya no podamos optar por ninguna otra alternativa. Debemos convivir con el riesgo porque no resulta rentable implementar medidas de seguridad.
## Políticas de seguridad y otros documentos.

- Dentro de una organización se deben tener muy clara las reglas para optar por una buena seguridad.
- Políticas:
    - Explican las bases sobre las cuales la organización realiza sus tareas y busca cumplir sus objetivos.
    - Deben estar escritas y avaladas por la alta gerencia.
    - Se debe remarcar la importancia de estas políticas y aclarar las obligaciones de cada empleado de cumplirlas
    - Existen muchas políticas siendo una de las importantes la política de seguridad de la información.
- Estándares:
    - Documentos que explican en qué forma van a ser alcanzados los objetivos propuestos por la organización de forma parcial o total.
    - Se habla de tecnologías específicas, algoritmos de encriptación, sistemas operativos, arquitectura de hardware.
- Procedimientos:
    - Derivan de los estándares y son los documentos que se encuentran en el nivel más práctico de todos.
    - Sirven como guía paso a paso que explica cómo realizar las tareas.
    - Son los documentos que más se modifican.
    - Son de gran ayuda al momento de realizar un reemplazo de software o de un empleador.
- Responsabilidades:
    - Recordar a los demás que también debe cumplir responsabilidades.
    - Estar atento aunque todo esta bien.
- Equipo de seguridad:
    - Cada organización debe contar con un equipo que esté designado a mantener la seguridad.
- Controles. Dueños, custodios y usuarios de datos:
    - Se debe asignar dueños a las diferentes informaciones, estos dueños deben ser del mismo departamento de la información que se disponga.
    - Cada dueño tendrá responsabilidades y poder sobre esa información.
## Tema 2. Dispositivos: inventarios y controles

## Inventario de dispositivos

- Es importante contar con el inventario de dispositivos que se encuentra en la red, esto para implementar de mejor forma las medidas de seguridad.
    
- Switches inteligentes:
    
    - Se puede aplicar tecnologías como port security (Seguridad portuaria, presentes en dispositivos Cisco)
    - Permite enviar una notificación por medio de trap SNMP

`#trap SNMP(Simple Network Management Protocol) -> Notificación que un dispositivo de red (Routers, switches, servidores, impresoras, etc) envía a un sistema de administración de red para alertar sobre eventos o cambios significativos en el estado del dispositivo.`

- Arpalert:
    
    - Herramienta que permite capturar el tráfico de una interfaz de red.
    - Detecta asociaciones de IP y MAC actuales.
    - Crea de forma rápida el inventario que corresponde a una red.
    - Analiza los paquetes de tipo ARP.
    
    `#ARP -> Se envían para conocer la MAC asociada a una IP.`
    
    `#MAC -> Identificador único asignado a la tarjeta red.`
    
- Scripting:
    
    - Pequeño programa creado de forma interna para realizar tareas sencillas y generar reportes de nuevos dispositivos de red.
- Rúters y switches(Interruptores):
    
    - Más utilizados en todas las organizaciones.
    - Se deben considerar aspectos de seguridad al momento de seleccionarlos, instalarlos y configurarlos.
- Port security:
    
    - Esta tecnología esta presente en varios modelos y switches y ofrece estas configuraciones:
        - Lista blanca de MAC:
            - Define qué direcciones MAC pueden conectarse y a que puerto fisico.
        - Lista negra de MAC:
            - Define qué direcciones no podrán conectarse nunca a la red.
        - Aprender MAC:
            - Configura que direcciones MAC conectadas pueden establecer conexiones y bloquear nuevos dispositivos.
        - Configuración remota:
            - Bloquea dispositivos remotos.
- DHCP snooping:
    
    - Permite a los switchs analizar los mensajes DHCP.
    - Analiza y bloquea ataques comunes.
- Cuentas de acceso centralizadas:
    
    - Centraliza la base de datos de usuarios para asignar perfiles.
- TACACS+:
    
    - Protocolo desarrollado por Cisco.
    - Provee autenticación, autorización y registro (AAA)
    - Utiliza protocolo TCP para el intercambio de tráfico.
    - El tráfico es encriptado.
- Radius:
    
    - Utiliza protocolo UDP para el intercambio de datos.
    - Unifica procesos de autenticación y autorización.
- Uso de servidores Syslog
    
    - Forma de contar con un registro de todo lo que sucede en nuestros equipos de telecomunicaciones.
    - Los parámetros se definen en un router o switch desde sus configuraciones.
- Firewalls:
    
    - Inspecciona contenidos de paquetes.
- Redes inalámbricas:
    
    - Simplifica las conexiones y aumenta el campo de conexión.
    - Si se configuran correctamente pueden alcanzar una buena seguridad.
    - La información que circule por la red sin encriptar puede ser fácilmente capturada. por esta razón se debe considerar lo siguiente:
        - Modificar los SSID(Service set identifier) que vienen por defecto.
        - No publicar el SSID en modo broadcast
        - Modificar periódicamente las claves compartidas.
        - Implementar métodos de autenticación fuerte.
        - Utilizar WPA(Wifi protected access)/WPA2 en lugar de WEP(wired equivalent privacy)
        - Implementar las últimas medidas disponibles.


==Tema 3. Detección de intrusos en un dispositivo==

- Prevención de intrusos
	- Detección y prevención de intruso permite:
		- Analizar tráfico y bloqueos de ataque de forma automática.
- Administración remota:
	- Manejo remoto.
	- Deben ser configurados y utilizados con cuidado.
	- Se puede contar con varias interfaces de administración como ==SNMP==, ==SSH==.
	- Nos permite automatizar tareas de rutina.
- CLI vs TUI vs GUI vs WUI
	- CLI -> Línea de comando.
	- TUI -> Interfaz de texto mas amigable.
	- GUI -> Accesibles por medio de un servidor web.
==Todas estas herramientas son utilizadas para gestionar dispositivos.==
- Protocolo TCP/IP
	- Principal protocolo atacado.
	- Posee los protocolos: DHCP, DNS, SSH, HTTP, FTP.
		- SMTP -> Transferencia de archivos.
		- POP3 -> 
		- IMAP -> Acceso a mensajes de internet.
		- SNMP y SSL -> Seguridad de la capa de transporte
- SSH :
	- Accede a los dispositivos a través de la red.
	- Remplazo de Telnet.
	- Copiar archivos, redirigir tráfico.
- SSL/TLS:
	- Agrega capa de seguridad a otros utilizando criptografía simétrica y asimétrica.
	- Protege protocolos HTTP y SMTP.
- SMTP, IMAP y POP3:
	- Utilizados por la arquitectura de correos electrónicos.
	- SMTP -> Transportar mensajes de correo.
	- IMAP y POP3 -> Acceder a los correos.
	- Envían la información de texto plano.
- HTTP y FTP:
	- Se utilizan para transferir archivos y documentos por medio de las redes.
	- HTTP -> Muestra páginas web.
- DHCP:
	- Permite a los clientes obtener sus parámetros de configuración de forma automática.
	- Protocolo muy inseguro.
- DNS:
	- Computadoras puedan resolver nombres de dominio a direcciones IP.
- SNMP:
	- Consultar o modificar información en dispositivos como rúters, firewalls y switches.

==Diseño de redes seguras==
- Obligados a diseñar redes seguras.

- Zonas desmilitarizadas.(DMZ)
	- Ubicar dispositivos que presten servicios públicos por medio de internet.
- Firewall:
	- Equipos ya preparados para detectar intrusiones y frenarlas.
	- Refuerza la seguridad entre LAN Y DMZ.
- Rúter:
	- Trae un firewall.
	- Posee lista de control de tráfico y accesos limitados dentro de ellos.
- VPN(Redes privadas virtuales)
	- Realiza conexiones seguras sobre medios inseguros (internet).
	- Habilita el trabajo remoto.
	- Utiliza protocolos Ipsec.
	- La única vulnerabilidad estaría en las credenciales.
- Detección de intruso:
	- Factores que observa un sistema:
		- Integridad de archivos:
			- Se verifica tamaño, permisos, hash y otros parámetros.
		- Monitoreo de registros:
			- Verificar archivos de logs.
		- Registro de Windows:
			- Verificar, claves de registros y analizar cambios realizados.
		- Puertos abiertos:
			- Definir que puertos deben estar abiertos.

==Tema 4. Penetración test.==

- Fases de un test de penetración:
	- Evaluar nivel de seguridad:
	- Test de penetración:
		- Pruebas ofensivas contra los mecanismos de defensas.
- Fase de reconocimiento:
	- Definir objetivos y se recopila información.
	- Nombres y direcciones de correos.
	- Topología de red y direcciones IP.
- Fase escaneo:
	- Buscar vectores de ataque.
	- Escaneo de puertos y servicios.
- Fase de enumeración:
	- Datos de usuarios, nombres de equipo, servicios de red.
- Fase de acceso:
	- Realizar acceso al sistema.
- Fase de mantenimiento de acceso:
	- Mantener acceso al sistema atacado.

==UNIDAD 2. ANÁLISIS DE AMENAZAS==

==Tema 1. Metodología de análisis==.

- Búsqueda de vulnerabilidades:
- Escaneo de seguridad.
- Test de intrusión.
- Evaluación del riesgo.
- Auditoría de seguridad.
- Hacking ético.
- Test de seguridad final.

- Fases que componen el OSSTMM.

- Sección A.
	- Seguridad de la información.
- Sección B.
	- Seguridad de los procesos.
- Sección C.
	- Seguridad en las tecnologías de internet.
- Sección D.
	- Seguridad en las comunicaciones.
- Sección E.
	- Seguridad inalámbrica.
- Sección F.
	- Seguridad física.


- ISSAF:
	- Marco de trabajo detallado de las prácticas y conceptos relacionados.
	- Tareas que debemos realizar al testeo de seguridad.

- OWASP:
	- Seguridad sobre aplicaciones web.
	- Hacer visible la seguridad en aplicaciones.

- Proyectos de documentación actuales.
	- Guía de desarrollo:
		- Guía detallada aplicaciones web seguras.
	- Guía de pruebas:
		- Centrada en las pruebas y listas sobre aplicaciones web.
	- Top 10:
		- Vulnerabilidades críticas de aplicaciones web.
	- Legal:
		- Contratación de servicios de software.
	- AppSec FAQ

==Tema 2. Identificación de amenazas.==

- Desastre del entorno.
- Amenazas del sistema.
- Amenazas en la red.
- Amenazas de personas.


- Desastre del entorno:
	- Es todo aquello que no es posible prever con anterioridad.
- Amenazas del sistema:
	- Malware:
		- Aplicaciones para dañar el sistema o proporcionar acceso.
	- Bugs o errores de programación: Software mal diseñado, ocasiona un agujero de seguridad.
- Amenazas en la red:
	- Se dan por medio de internet o por el uso de esta.
	- Software que se descargan de la red.
- Amenazas de personas:
	- Los peores ataques suelen venir desde dentro de una empresa.
- Insider:
	- Trabajador que busca venganza de la empresa.

==Tema 3.  Escaneo de puertos==.

- Ping sweepers:
	- Identificar hosts activos dentro de los rangos de IP. Se utiliza barrido de ping.
- Si están bloqueando el ping:
	- Usar NetScan Tools.

- Herramientas de TCP-ping:
	- Emula la función de un ping.
	- Permite determinar host activos usando protocolo TCP.
- Estados de puertos:
	- Se utiliza la herramienta NMAP.
	- Abierto:
		- Puerto disponible y escuchando.
	- Cerrado:
		- No responde a solicitudes de conexión.
	- Filtrado:
		- No se puede acceder.
		- Dispositivo filtra paquetes que impiden escanear y determinar si esta abierto o cerrado.
	- No filtrado:
		- Puerto que se encuentra accesible.
		- No se puede determinar si esta abierto o cerrado.
	- Abierto/filtrado:
		- Estado ambiguo.
		- No se puede determinar si el puerto esta abierto.
		- Puede que este abierto y no responda.
	- Cerrado/filtrado:
		- No puede concluir si el puerto esta cerrado o filtrado.

- Técnicas de Escaneo:
	- Escaneo SYN o half open (medio abierto):
		- Identifica puertos
		- Envío de solicitud de sincronismo (SYN).
	- Escaneo full o connect-scan:
		- Tipo escaneo TCP.
		- Se completa la conexión.
		- Disminuye falsos positivos, toma mas tiempo.
		- Queda registro de nuestras conexiones.
	- Escaneo UDP:
		- Envía paquete UDP.
		- Respuesta ICMP, puerto cerrado.
		- Otro tipo de error ICMP, puerto filtrado.
		- Retorna UDP, puerto abierto.
	- Escaneo ACK:
		- Comprobar si existe un firewall de por medio.
	- Escaneo NMAP:
		- Escaneo mas popular entre los profesionales de redes.



==MODULO 4: RESPUESTA, RECUPERCIÓN Y ACCIÓN LUEGO DE UN ATAQUE.

==UNIDAD 1: RESPUESTA ANTE ATAQUES INFORMÁTICOS

- Técnicas de detección de ataques:

	- Message digest (MD5SUM):
		- Algoritmo criptográfico que aplica algoritmo MD5 para calcular resúmenes y valida el contenido de los ficheros.
		- Para esto se usa un software forense FTK.
	- Tripwire:
		- Software que permite verificar la integridad de directorios y archivos.
		- Posee 4 formas de funcionamiento:
			- 1.- Generación de base de datos.
			- 2.- Verificación de integridad.
			- 3.- Actualización de base de datos.
			- 4.- Actualización interactiva de base de datos.
	- Scanners y sniffers:
		-  Otra forma de detectar Scanners y sniffers (analizador de protocolos).
		- Es posible detectar si el intruso dejó abiertos otros puertos diferentes a los que se utilizan comúnmente.
	- Escáneres de vulnerabilidades:
		-  Se utiliza como aplicaciones de seguridad para realizar auditorías.
		- Con los resultados se busca una intrusión.
	- Detección de sniffers:
		- Para detectarlos es necesarios consultar el estado de la placa de red desde la propia maquina.
		- Se hace envío de paquetes a una máquina inexistente en la dirección no está dada de alta.
	- Logs:
		- Se generan en cada una de las aplicaciones instaladas.
		- Se analiza y se evalúa las metodologías de control.
	- CronTab:
		-  Encargado de hacer rotación mensual de los logs y eliminar los del mes pasado.
	- Logs de los servidores:
		- Registro detallados de eventos que ocurren en un servidor.
	- Control de acceso a logs:
		- Personas autorizadas puedan ver y gestionar los registros de servidores.
	- Control de acceso a internet:
		- Genera registros de información del número IP de la maquina que se conecta a la red.
	- Modificación de datos:
		- Indica aquellos datos que han sido modificados.
	- Cambio de password:
		- Cuando un usuario modifica su password no se genera logs.
	- Logs de administrador:
		- Estos logs no se corroboran de forma periódica.
	- Login fallido:
		- Se genera una entrada en el log de AcuServer.
		- No especifica el motivo del fallo.
	- Bloqueo de un usuario:
		- Si se ingresa la password mal mas de 2 veces se bloquea el usuario, este no genera un registro del evento.
	- Perfil del usuario:
		- Los datos se encuentran en crudo sin analizar.
	- Reportes de correo:
		- No se generan estadísticas.
	- Estadísticas de red:
		- Este programa no brinda datos sobre el consumo del ancho de banda.


==Tema 2: Respuesta ante ataques.==

Como actuamos después de un ataque informático?
- Poner en marcha un plan de respuesta:
	- Primer paso:
		- Realizar auditoria.
		- identificar amenaza.
	- Segundo paso:
		- Comunicar y notificar el incidente detectado.
	- Tercer paso:
		- Definir comunicación externa.
		- Como enfrentar crisis publicas.
	- Cuarto paso:
		- Definir metodología y tecnología que se va a emplear.

- Departamento de tecnología/sistemas:
	- Equipo que hace frente al ataque o amenazas.
- Departamento legal:
	- Notifica quien hizo el robo o daño de datos y los usuarios afectados.
- Equipo de gestión de crisis:
	- Inician las acciones necesarias para mitigar el daño.

Como resolver un problema con un malware.
- Primer escenario:
	- Realizar análisis sobre los sistemas.
- Segundo escenario:
	- Posible solución para mitigar la crisis.
	- Restablecer los sistemas de la organización.


- Estafa del CEO:
	- Variante del phishing.
	- El estafador envía un coreo haciéndose pasar por su CEO.
- Clone phishing:
	- Reemplazar todo el contenido de un correo legítimo por mensajes y enlaces maliciosos.
- Suplantación de dominio:
	- Falsificar dominio de una organización o empresa.
- Phishing HTTPS:
	- Enlace que parece legitimo, pero, en realidad, es malicioso.
- Smishing:
	- Es el phishing a través de sms.
- Spear phishing:
	- Correos electrónicos destinados a personas especificas.
	- Mensajes personalizados.
- Vishing:
	- Llamada por teléfono al usuario para obtener información personal o financiera.
- Watering hole phishing:
	- Infecta los sitios web.
- Whaling:
	- Los atacantes se concentran en los ejecutivos de alto nivel como los CEO, CFO y COO.

==UNIDAD 2: RECUPERACIÓN Y SEGURIDAD LUEGO DE UNA INTRUSIÓN==



- Consecuencias de un ataque cibernético
	- Daños triviales:
		- Virus fáciles de remover y eliminar.
	- Daños menores:
		- El virus borra todo.
	- Daños moderados:
		- El virus formateo el disco duro y mezcla los componentes FAT.
		- Sobreescritura del disco duro.
	- Daños mayores:
		- No se pueden recuperar los archivos.
	- Daños ilimitados:
		- Obtiene claves del administrador del sistema.
		- Creación de nuevo usuario con privilegio al máximo.

- Algunos ataques:
	- Ataque de denegación de servicio (DoS):
		- Ataque hacia un sistema operativo o una red de una organización que los vuelve inaccesible a los usuarios válidos.
	- Man in the middle(MitM): Roba información encriptada estando al medio de 2 puntos de una red.
	- Ataques de replay:
		- Se dan sobre una red, la transmisión de datos válido pasa a ser maliciosa.
	- Ataques de día cero:
		- Vulnerabilidades que se encuentran antes de ser parchados.
		- Se encuentran cuando un software esta recién creado.

==Tema 2: Recuperación luego de un ataque.==

Pasos que deben cumplirse.
- Aislar y apagar los sistemas de una organización:
- Plan de continuidad empresarial en la organización:
	- Manual que detalla como proceder y ayudar a la organización en todas sus áreas.
- Reportar el ataque:
	- Informar a los clientes.
- Reinstalar desde el back-up:
	- Poseer copias de seguridad.
- Reparar, parchear y monitorear.

- Corregir puntos de entradas comunes:
	- Analizar los puntos de entrada comunes para estos tipos de ataques.
- Prevención y próximos pasos:
	- No escatimar en gastos en seguridad informática.
- Plan de recuperación de desastre:
	- Analizar las necesidades de cada organización:
		- Especifico para cada organización.
	- Realizar una evaluación de riesgo:
	- Protocolo de recuperación y continuidad operativa:
		- Establecer protocolo, buscar estrategias y respuestas ante diferentes escenarios.
	- Capacitar al equipo y probar los planes.
	- Actualizar, mantener y mejorar plan de recuperación ante desastres.
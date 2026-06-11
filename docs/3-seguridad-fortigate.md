# 3. Políticas de Seguridad y NAT (Zero Trust)

La arquitectura de seguridad perimetral se ha diseñado bajo el principio de "Confianza Cero" (Zero Trust), delegando el control de accesos, el aislamiento y la traducción de red al clúster de firewalls FortiGate.

## 3.1. Aislamiento Multinacional (Inter-Company Isolation)

Para aislar a las 4 empresas que comparten la infraestructura de transporte SD-WAN, se descarta el uso de complejas listas de control de acceso (ACLs) cruzadas. 
* Se aprovecha la política de **Denegación Implícita (Implicit Deny)** nativa del motor del firewall. 
* Los túneles VPN de cada corporación convergen en el FortiGate del CPD Central como zonas lógicas totalmente independientes. 
* Al no existir políticas de enrutamiento cruzado explícitamente permitidas, el tráfico entre la Empresa A y la Empresa B es descartado en el núcleo del firewall. Una infección en una sede no puede propagarse lateralmente a otra empresa.

## 3.2. Traducción de Direcciones de Red (NAT Centralizado)

Al utilizar un enrutamiento de túnel forzado, los firewalls de las sedes locales quedan liberados de realizar traducciones de red. Todo el NAT se ejecuta en el equipo perimetral del CPD Central, proporcionando un punto único de auditoría.

* **Traducción de Origen (SNAT / PAT):** El tráfico de navegación procedente de las redes privadas corporativas (`10.0.0.0/16`) se enmascara utilizando *Port Address Translation* bajo la única IP pública principal de la interfaz WAN (`82.144.15.2`). Esto optimiza el uso de IPs públicas y oculta la topología interna frente a Internet.
* **Traducción de Destino (DNAT / VIPs):** Para exponer servicios de forma segura, se configuran Objetos Virtual IP (VIP). Por ejemplo, las peticiones externas hacia la IP pública secundaria `82.144.15.3` en el puerto 443 son redirigidas quirúrgicamente hacia la IP privada del servidor web (`172.16.50.10`).

## 3.3. Jaula de Seguridad en la DMZ

La Zona Desmilitarizada asume la premisa de que sus servidores (expuestos a Internet) son susceptibles de ser comprometidos. Para evitar vulneraciones hacia la red core, se aplica un flujo de tráfico estrictamente unidireccional:

1. **LAN hacia DMZ (Permitido):** Los administradores pueden acceder desde las VLANs internas de gestión hacia la DMZ para labores de mantenimiento (SSH, RDP, subida de archivos).
2. **DMZ hacia LAN (Bloqueo y Registro):** Se configura una regla explícita de `DENY` con el registro de tráfico activado (`logtraffic all`). Si un servidor web comprometido intenta iniciar un escaneo o conexión hacia las redes corporativas internas, el paquete es destruido de inmediato y se dispara una alerta de seguridad en los registros (logs) del sistema.

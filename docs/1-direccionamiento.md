# 1. Topología Física y Direccionamiento (Los 3 Mundos)

En esta sección se detalla la estrategia de direccionamiento IP diseñada para separar lógicamente los diferentes entornos de la corporación. El objetivo principal es garantizar la escalabilidad a largo plazo y aplicar principios de seguridad mediante la segmentación desde la capa de red.

## 1.1. Direccionamiento WAN Perimetral (Salida a Internet)

Para la conexión externa del CPD Central, se solicitó al proveedor de servicios (ISP) un bloque estático `/29` en lugar del tradicional `/30`. 

**Justificación técnica:** Una máscara `/30` limita la conexión a una única IP pública útil en el Firewall, restringiendo la escalabilidad. El bloque `/29` proporciona 6 IPs públicas útiles. Esto permite utilizar una IP para el NAT de salida (SNAT) de toda la corporación, y reservar las restantes como Virtual IPs (VIPs) para exponer servicios de la DMZ de forma independiente.

| Ubicación | Enlace ISP | Subred Pública | Máscara | IP Router ISP | IP Interfaz WAN (FortiGate) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **CPD Central** | Principal (10G) | `82.144.15.0` | `/29` (255.255.255.248)| `82.144.15.1` | **`82.144.15.2`** |

---

## 1.2. Segmentación de la Infraestructura de Servidores

Para evitar movimientos laterales en caso de un ataque, los servidores se han dividido en tres "mundos" totalmente aislados, tanto a nivel físico (distintos puertos/switches) como a nivel lógico (distintas familias de IPs).

### Mundo 1: Servidores Internos (La "Caja Fuerte")
Son los servidores críticos que componen el Software Base de la infraestructura (Controladores de Dominio, DNS). No son simples aplicaciones, sino el cimiento operativo de la red. 
* **Conexión:** Directa al Switch Core L3 (Cisco Catalyst 9500).
* **Direccionamiento:** Se utiliza el primer bloque libre tras las subredes de las empresas (`10.0.128.0/24`), manteniéndolos ocultos de Internet.

| Nombre del Host | Rol / Servicio crítico | Dirección IP | Gateway (Switch Core) |
| :--- | :--- | :--- | :--- |
| **SRV-DC-01** | Active Directory (Controlador Dominio) | `10.0.128.10` | `10.0.128.1` |
| **SRV-DNS-01** | Servidor DNS Corporativo Primario | `10.0.128.11` | `10.0.128.1` |
| **SRV-DB-01** | Base de Datos Interna (Recursos Humanos) | `10.0.128.30` | `10.0.128.1` |

### Mundo 2: Zona Desmilitarizada - DMZ (El "Escaparate")
Servidores que requieren exposición directa a Internet (Ej. servidores web). Se asume que son vulnerables, por lo que operan en un entorno de "Confianza Cero".
* **Conexión:** Físicamente aislados del Switch Core. Se conectan a un switch secundario que cuelga directamente de un puerto dedicado del FortiGate.
* **Direccionamiento:** Para evidenciar lógicamente esta separación, se utiliza un direccionamiento de Clase B (`172.16.x.x`), rompiendo con el esquema de Clase A del resto de la empresa.

| Nombre del Host | Rol / Servicio | Dirección IP | Gateway (FortiGate DMZ) |
| :--- | :--- | :--- | :--- |
| **SRV-WEB-PUB-01** | Servidor Web Corporativo (Expuesto) | `172.16.50.10` | `172.16.50.1` |
| **SRV-PROXY-EXT** | Proxy Inverso | `172.16.50.12` | `172.16.50.1` |

### Mundo 3: Entorno Cloud (El "Almacén Externo")
Espacio reservado para la expansión de la infraestructura hacia la nube pública (AWS).
* **Conexión:** Accesible de forma exclusiva a través de túneles VPN Site-to-Site gestionados por el FortiGate.
* **Direccionamiento:** Se reserva el bloque gigante **`10.1.0.0/16`** en exclusiva. De esta forma, el crecimiento futuro en la nube nunca generará conflictos de enrutamiento con los bloques `/19` físicos de las filiales.

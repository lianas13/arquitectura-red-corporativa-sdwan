# Anexo B: Tablas de Enrutamiento (Routing Tables)

Desglose de las tablas de enrutamiento estáticas y dinámicas (OSPF/BGP) presentes en los conmutadores de capa 3 y pasarelas de la infraestructura.

## Empresa A 

### Sede Principal (Switch Core L3)
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.0.0` | `/20` | `0.0.0.0` (Local) | Varias (VLANs) | Directa (C) |
| `10.0.16.0` | `/25` | IP Enlace D2 | Gigabit0/1 | OSPF (O) |
| `10.0.16.128` | `/28` | IP Enlace D3 | Gigabit0/2 | OSPF (O) |
| `10.0.16.144` | `/28` | IP Enlace D4 | Gigabit0/3 | OSPF (O) |
| `10.0.32.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `10.0.64.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `10.0.96.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `0.0.0.0` (Defecto)| `/0` | IP del FortiGate Local | Gigabit0/0 | Estática (S*) |

### Delegación 1 (Router/Switch L3)
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.16.0` | `/25` | `0.0.0.0` (Local) | Varias (VLANs) | Directa (C) |
| `0.0.0.0` | `/0` | IP Router Sede Principal | Gigabit0/0 | OSPF (O*E2) |

### [cite_start]Delegación 2 (Router/Switch L3) [cite: 53]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.16.128` | `/28` | `0.0.0.0` (Local) | Varias (VLANs) | [cite_start]Directa (C) | [cite: 54]
| `0.0.0.0` | `/0` | IP Router Sede Principal | Gigabit0/0 | [cite_start]OSPF (O*E2) | [cite: 54]

### [cite_start]Delegación 3 (Router/Switch L3) [cite: 55]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.16.144` | `/28` | `0.0.0.0` (Local) | Varias (VLANs) | [cite_start]Directa (C) | [cite: 56]
| `0.0.0.0` | `/0` | IP Router Sede Principal | Gigabit0/0 | [cite_start]OSPF (O*E2) | [cite: 56]

---

## Empresa B

### [cite_start]Sede Principal (Switch Core L3) [cite: 59, 60]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.32.0` | `/20` | `0.0.0.0` (Local) | Varias (VLANs) | Directa (C) |
| `10.0.48.0` | `/25` | IP Enlace D2-B | Gigabit0/1 | OSPF (O) |
| `10.0.48.128` | `/28` | IP Enlace D3-B | Gigabit0/2 | OSPF (O) |
| `10.0.48.144` | `/28` | IP Enlace D4-B | Gigabit0/3 | OSPF (O) |
| `10.0.0.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `10.0.64.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `10.0.96.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `0.0.0.0` | `/0` | IP del Proveedor (ISP) | Gigabit0/0 | Estática (S*) |

### [cite_start]Delegación 1 (Router/Switch L3) [cite: 62]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.48.0` | `/25` | `0.0.0.0` (Local) | Varias (VLANs) | Directa (C) |
| `0.0.0.0` | `/0` | IP Router Sede Principal B | Gigabit0/0 | OSPF (O*E2) |

### [cite_start]Delegación 2 (Router/Switch L3) [cite: 63]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.48.128` | `/28` | `0.0.0.0` (Local) | Varias (VLANs) | [cite_start]Directa (C) | [cite: 64]
| `0.0.0.0` | `/0` | IP Router Sede Principal B | Gigabit0/0 | [cite_start]OSPF (O*E2) | [cite: 65]

### [cite_start]Delegación 3 (Router/Switch L3) [cite: 66]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.48.144` | `/28` | `0.0.0.0` (Local) | Varias (VLANs) | [cite_start]Directa (C) | [cite: 67]
| `0.0.0.0` | `/0` | IP Router Sede Principal B | Gigabit0/0 | [cite_start]OSPF (O*E2) | [cite: 67]

---

## Empresa C

### Sede Principal (Switch Core L3) [cite: 70, 71]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.64.0` | `/20` | `0.0.0.0` (Local) | Varias (VLANs) | Directa (C) |
| `10.0.80.0` | `/25` | IP Enlace D2 | Gigabit0/1 | OSPF (O) |
| `10.0.80.128` | `/28` | IP Enlace D3 | Gigabit0/2 | OSPF (O) |
| `10.0.80.144` | `/28` | IP Enlace D4 | Gigabit0/3 | OSPF (O) |
| `10.0.0.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `10.0.32.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `10.0.96.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `0.0.0.0` | `/0` | IP del Proveedor (ISP) | Gigabit0/0 | Estática (S*) |

### [cite_start]Delegación 1 (Router/Switch L3) [cite: 73]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.80.0` | `/25` | `0.0.0.0` (Local) | Varias (VLANs) | Directa (C) |
| `0.0.0.0` | `/0` | IP Router Sede Principal C | Gigabit0/0 | OSPF (O*E2) |

### [cite_start]Delegación 2 (Router/Switch L3) [cite: 74]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.80.128` | `/28` | `0.0.0.0` (Local) | Varias (VLANs) | [cite_start]Directa (C) | [cite: 75]
| `0.0.0.0` | `/0` | IP Router Sede Principal C | Gigabit0/0 | [cite_start]OSPF (O*E2) | [cite: 75]

### [cite_start]Delegación 3 (Router/Switch L3) [cite: 76]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.80.144` | `/28` | `0.0.0.0` (Local) | Varias (VLANs) | [cite_start]Directa (C) | [cite: 77]
| `0.0.0.0` | `/0` | IP Router Sede Principal C | Gigabit0/0 | [cite_start]OSPF (O*E2) | [cite: 77]

---

## Empresa D

### [cite_start]Sede Principal (Switch Core L3) [cite: 80, 81]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.96.0` | `/20` | `0.0.0.0` (Local) | Varias (VLANs) | Directa (C) |
| `10.0.112.0` | `/25` | IP Enlace D2-D | Gigabit0/1 | OSPF (O) |
| `10.0.112.128` | `/28` | IP Enlace D3-D | Gigabit0/2 | OSPF (O) |
| `10.0.112.144` | `/28` | IP Enlace D4-D | Gigabit0/3 | OSPF (O) |
| `10.0.0.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `10.0.32.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `10.0.64.0` | `/19` | IP CPD Central | Túnel SD-WAN | BGP (B) |
| `0.0.0.0` | `/0` | IP del Proveedor (ISP) | Gigabit0/0 | Estática (S*) |

### Delegación 1 (Router/Switch L3) [cite: 83]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.112.0` | `/25` | `0.0.0.0` (Local) | Varias (VLANs) | Directa (C) |
| `0.0.0.0` | `/0` | IP Router Sede Principal D | Gigabit0/0 | OSPF (O*E2) |

### [cite_start]Delegación 2 (Router/Switch L3) [cite: 84]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.112.128` | `/28` | `0.0.0.0` (Local) | Varias (VLANs) | [cite_start]Directa (C) | [cite: 85]
| `0.0.0.0` | `/0` | IP Router Sede Principal D | Gigabit0/0 | [cite_start]OSPF (O*E2) | [cite: 85]

### [cite_start]Delegación 3 (Router/Switch L3) [cite: 86]
| Red de Destino | Máscara | Próximo Salto (Next Hop) | Interfaz de Salida | Origen / Protocolo |
| :--- | :---: | :--- | :--- | :--- |
| `10.0.112.144` | `/28` | `0.0.0.0` (Local) | Varias (VLANs) | [cite_start]Directa (C) | [cite: 87]
| `0.0.0.0` | `/0` | IP Router Sede Principal D | Gigabit0/0 | [cite_start]OSPF (O*E2) | [cite: 87]

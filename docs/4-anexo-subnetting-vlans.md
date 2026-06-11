# Anexo A: Tablas de Direccionamiento IP y Subnetting

Este anexo detalla la segmentación de red a nivel de VLAN para cada una de las sedes y delegaciones, garantizando el aprovechamiento del espacio IP y el aislamiento por departamentos.

## Empresa A (Bloque Maestro: 10.0.0.0/19)

### Sede Principal Empresa A
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.0.0` | `/21` | 2.046 | `10.0.0.1 - 10.0.7.254` | `10.0.7.255` |
| Informática | 20 | `10.0.8.0` | `/23` | 510 | `10.0.8.1 - 10.0.9.254` | `10.0.9.255` |
| Administración| 30 | `10.0.10.0` | `/24` | 254 | `10.0.10.1 - 10.0.10.254` | `10.0.10.255` |
| Dirección | 10 | `10.0.11.0` | `/25` | 126 | `10.0.11.1 - 10.0.11.126` | `10.0.11.127` |
*(Nota: Espacio reservado para crecimiento futuro desde la 10.0.11.128 hasta la 10.0.15.255).*

### Delegación 1 (Empresa A)
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.16.0` | `/26` | 62 | `10.0.16.1 - 10.0.16.62` | `10.0.16.63` |
| Informática | 20 | `10.0.16.64` | `/27` | 30 | `10.0.16.65 - 10.0.16.94` | `10.0.16.95` |
| Administración| 30 | `10.0.16.96` | `/28` | 14 | `10.0.16.97 - 10.0.16.110` | `10.0.16.111` |
| Dirección | 10 | `10.0.16.112` | `/28` | 14 | `10.0.16.113 - 10.0.16.126` | `10.0.16.127` |

### [cite_start]Delegación 2 (Empresa A) [cite: 93]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.16.128` | `/30` | 2 | `10.0.16.129 - 10.0.16.130` | [cite_start]`10.0.16.131` | [cite: 94]
| Informática | 20 | `10.0.16.132` | `/30` | 2 | `10.0.16.133 - 10.0.16.134` | [cite_start]`10.0.16.135` | [cite: 94]
| Administración| 30 | `10.0.16.136` | `/30` | 2 | `10.0.16.137 - 10.0.16.138` | [cite_start]`10.0.16.139` | [cite: 94]
| Dirección | 10 | `10.0.16.140` | `/30` | 2 | `10.0.16.141 - 10.0.16.142` | [cite_start]`10.0.16.143` | [cite: 94]

### [cite_start]Delegación 3 (Empresa A) [cite: 95]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.16.144` | `/30` | 2 | `10.0.16.145 - 10.0.16.146` | [cite_start]`10.0.16.147` | [cite: 96]
| Informática | 20 | `10.0.16.148` | `/30` | 2 | `10.0.16.149 - 10.0.16.150` | [cite_start]`10.0.16.151` | [cite: 96]
| Administración| 30 | `10.0.16.152` | `/30` | 2 | `10.0.16.153 - 10.0.16.154` | [cite_start]`10.0.16.155` | [cite: 96]
| Dirección | 10 | `10.0.16.156` | `/30` | 2 | `10.0.16.157 - 10.0.16.158` | [cite_start]`10.0.16.159` | [cite: 96]

---

## Empresa B (Bloque Maestro: 10.0.32.0/19)

### [cite_start]Sede Principal Empresa B [cite: 99]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.32.0` | `/21` | 2.046 | `10.0.32.1 - 10.0.39.254` | `10.0.39.255` |
| Informática | 20 | `10.0.40.0` | `/23` | 510 | `10.0.40.1 - 10.0.41.254` | `10.0.41.255` |
| Administración| 30 | `10.0.42.0` | `/24` | 254 | `10.0.42.1 - 10.0.42.254` | `10.0.42.255` |
| Dirección | 10 | `10.0.43.0` | `/25` | 126 | `10.0.43.1 - 10.0.43.126` | `10.0.43.127` |

### [cite_start]Delegación 1 (Empresa B) [cite: 101]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.48.0` | `/26` | 62 | `10.0.48.1 - 10.0.48.62` | `10.0.48.63` |
| Informática | 20 | `10.0.48.64` | `/27` | 30 | `10.0.48.65 - 10.0.48.94` | `10.0.48.95` |
| Administración| 30 | `10.0.48.96` | `/28` | 14 | `10.0.48.97 - 10.0.48.110` | `10.0.48.111` |
| Dirección | 10 | `10.0.48.112` | `/28` | 14 | `10.0.48.113 - 10.0.48.127` | `10.0.48.127` |

### [cite_start]Delegación 2 (Empresa B) [cite: 102]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.48.128` | `/30` | 2 | `10.0.48.129 - 10.0.48.130` | [cite_start]`10.0.48.131` | [cite: 103]
| Informática | 20 | `10.0.48.132` | `/30` | 2 | `10.0.48.133 - 10.0.48.134` | [cite_start]`10.0.48.135` | [cite: 103]
| Administración| 30 | `10.0.48.136` | `/30` | 2 | `10.0.48.137 - 10.0.48.138` | [cite_start]`10.0.48.139` | [cite: 103]
| Dirección | 10 | `10.0.48.140` | `/30` | 2 | `10.0.48.141 - 10.0.48.142` | [cite_start]`10.0.48.143` | [cite: 103]

### [cite_start]Delegación 3 (Empresa B) [cite: 104]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.48.144` | `/30` | 2 | `10.0.48.145 - 10.0.48.146` | [cite_start]`10.0.48.147` | [cite: 105]
| Informática | 20 | `10.0.48.148` | `/30` | 2 | `10.0.48.149 - 10.0.48.150` | [cite_start]`10.0.48.151` | [cite: 105]
| Administración| 30 | `10.0.48.152` | `/30` | 2 | `10.0.48.153 - 10.0.48.154` | [cite_start]`10.0.48.155` | [cite: 105]
| Dirección | 10 | `10.0.48.156` | `/30` | 2 | `10.0.48.157 - 10.0.48.158` | [cite_start]`10.0.48.159` | [cite: 105]

---

## Empresa C (Bloque Maestro: 10.0.64.0/19)

### [cite_start]Sede Principal Empresa C [cite: 108]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.64.0` | `/21` | 2.046 | `10.0.64.1 - 10.0.71.254` | `10.0.71.255` |
| Informática | 20 | `10.0.72.0` | `/23` | 510 | `10.0.72.1 - 10.0.73.254` | `10.0.73.255` |
| Administración| 30 | `10.0.74.0` | `/24` | 254 | `10.0.74.1 - 10.0.74.254` | `10.0.74.255` |
| Dirección | 10 | `10.0.75.0` | `/25` | 126 | `10.0.75.1 - 10.0.75.126` | `10.0.75.127` |

### [cite_start]Delegación 1 (Empresa C) [cite: 110]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.80.0` | `/26` | 62 | `10.0.80.1 - 10.0.80.62` | `10.0.80.63` |
| Informática | 20 | `10.0.80.64` | `/27` | 30 | `10.0.80.65 - 10.0.80.94` | `10.0.80.95` |
| Administración| 30 | `10.0.80.96` | `/28` | 14 | `10.0.80.97 - 10.0.80.110` | `10.0.80.111` |
| Dirección | 10 | `10.0.80.112` | `/28` | 14 | `10.0.80.113 - 10.0.80.126` | `10.0.80.127` |

### [cite_start]Delegación 2 (Empresa C) [cite: 111]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.80.128` | `/30` | 2 | `10.0.80.129 - 10.0.80.130` | [cite_start]`10.0.80.131` | [cite: 112]
| Informática | 20 | `10.0.80.132` | `/30` | 2 | `10.0.80.133 - 10.0.80.134` | [cite_start]`10.0.80.135` | [cite: 112]
| Administración| 30 | `10.0.80.136` | `/30` | 2 | `10.0.80.137 - 10.0.80.138` | [cite_start]`10.0.80.139` | [cite: 112]
| Dirección | 10 | `10.0.80.140` | `/30` | 2 | `10.0.80.141 - 10.0.80.142` | [cite_start]`10.0.80.143` | [cite: 112]

### [cite_start]Delegación 3 (Empresa C) [cite: 113]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.80.144` | `/30` | 2 | `10.0.80.145 - 10.0.80.146` | [cite_start]`10.0.80.147` | [cite: 114]
| Informática | 20 | `10.0.80.148` | `/30` | 2 | `10.0.80.149 - 10.0.80.150` | [cite_start]`10.0.80.151` | [cite: 114]
| Administración| 30 | `10.0.80.152` | `/30` | 2 | `10.0.80.153 - 10.0.80.154` | [cite_start]`10.0.80.155` | [cite: 114]
| Dirección | 10 | `10.0.80.156` | `/30` | 2 | `10.0.80.157 - 10.0.80.158` | [cite_start]`10.0.80.159` | [cite: 114]

---

## Empresa D (Bloque Maestro: 10.0.96.0/19)

### [cite_start]Sede Principal Empresa D [cite: 117]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.96.0` | `/21` | 2.046 | `10.0.96.1 - 10.0.103.254` | `10.0.103.255` |
| Informática | 20 | `10.0.104.0` | `/23` | 510 | `10.0.104.1 - 10.0.105.254` | `10.0.105.255` |
| Administración| 30 | `10.0.106.0` | `/24` | 254 | `10.0.106.1 - 10.0.106.254` | `10.0.106.255` |
| Dirección | 10 | `10.0.107.0` | `/25` | 126 | `10.0.107.1 - 10.0.107.126` | `10.0.107.127` |

### [cite_start]Delegación 1 (Empresa D) [cite: 119]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.112.0` | `/26` | 62 | `10.0.112.1 - 10.0.112.62` | `10.0.112.63` |
| Informática | 20 | `10.0.112.64` | `/27` | 30 | `10.0.112.65 - 10.0.112.94` | `10.0.112.95` |
| Administración| 30 | `10.0.112.96` | `/28` | 14 | `10.0.112.97 - 10.0.112.110` | `10.0.112.111` |
| Dirección | 10 | `10.0.112.112` | `/28` | 14 | `10.0.112.113 - 10.0.112.126` | `10.0.112.127` |

### [cite_start]Delegación 2 (Empresa D) [cite: 120]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.112.128` | `/30` | 2 | `10.0.112.129 - 10.0.112.130` | [cite_start]`10.0.112.131` | [cite: 121]
| Informática | 20 | `10.0.112.132` | `/30` | 2 | `10.0.112.133 - 10.0.112.134` | [cite_start]`10.0.112.135` | [cite: 121]
| Administración| 30 | `10.0.112.136` | `/30` | 2 | `10.0.112.137 - 10.0.112.138` | [cite_start]`10.0.112.139` | [cite: 121]
| Dirección | 10 | `10.0.112.140` | `/30` | 2 | `10.0.112.141 - 10.0.112.142` | [cite_start]`10.0.112.143` | [cite: 121]

### [cite_start]Delegación 3 (Empresa D) [cite: 122]
| Departamento | VLAN | Red Asignada | Máscara | IPs Útiles | Rango de IPs | Broadcast |
| :--- | :---: | :--- | :---: | :---: | :--- | :--- |
| Usuarios | 40 | `10.0.112.144` | `/30` | 2 | `10.0.112.145 - 10.0.112.146` | [cite_start]`10.0.112.147` | [cite: 123]
| Informática | 20 | `10.0.112.148` | `/30` | 2 | `10.0.112.149 - 10.0.112.150` | [cite_start]`10.0.112.151` | [cite: 123]
| Administración| 30 | `10.0.112.152` | `/30` | 2 | `10.0.112.153 - 10.0.112.154` | [cite_start]`10.0.112.155` | [cite: 123]
| Dirección | 10 | `10.0.112.156` | `/30` | 2 | `10.0.112.157 - 10.0.112.158` | [cite_start]`10.0.112.159` | [cite: 123]

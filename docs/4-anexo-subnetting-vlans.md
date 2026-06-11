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

# 2. Enrutamiento Dinámico (OSPF & BGP)

El núcleo de las comunicaciones de este proyecto se basa en la separación estricta de dos protocolos de enrutamiento: OSPF para la convergencia LAN rápida dentro de cada edificio, y BGP para la interconexión escalable a través de la WAN corporativa.

## 2.1. Enrutamiento Interno LAN (Single-Area OSPF)

Cada empresa gestiona su enrutamiento interno utilizando OSPFv2 confinado al Área 0. Se ha implementado un diseño de OSPF "paranoico" y securizado para evitar manipulaciones de la tabla de enrutamiento desde los puertos de acceso de los usuarios.

* **Máscaras Wildcard:** Para mantener las configuraciones eficientes, se utiliza la máscara invertida del bloque maestro corporativo. Por ejemplo, en la Empresa A, el comando `network 10.0.0.0 0.0.31.255 area 0` inyecta automáticamente todas sus redes en el proceso de enrutamiento sin necesidad de declarar VLAN por VLAN.
* **Interfaces Pasivas:** Se silencia el protocolo OSPF en todas las VLANs de acceso (`passive-interface default`). De esta forma, las bocas de red de la oficina no envían ni escuchan mensajes de enrutamiento, previniendo inyecciones de rutas falsas.
* **Vecindades Estáticas (Unicast):** Se desactiva el descubrimiento automático por Multicast entre el Switch Core L3 y el Firewall local. La relación de vecindad se fuerza de manera explícita indicando la IP exacta del dispositivo vecino.

## 2.2. Enrutamiento Exterior WAN (eBGP y Sumarización)

Para interconectar el Centro de Procesamiento de Datos (CPD) con las filiales, se descarta extender OSPF sobre la SD-WAN para evitar sobrecargas por recálculo masivo en caso de caídas de enlaces locales (flapping). En su lugar, cada sede opera como un Sistema Autónomo (AS) privado mediante **eBGP**.

* **Peering sobre Overlay:** Las sesiones BGP (TCP puerto 179) no transitan por el enrutamiento público de los ISPs. El Peering se establece de forma encriptada, utilizando exclusivamente las Interfaces Virtuales creadas dentro de los túneles IPsec (red de tránsito `192.168.254.0/24`).
* **Sumarización Estricta (La clave del rendimiento):** Las sedes nunca anuncian sus subredes internas hacia la WAN. El FortiGate de cada empresa agrupa matemáticamente sus redes y anuncia **únicamente un bloque maestro `/19`** (ej. la Empresa A solo propaga `10.0.0.0/19`). 
  * *Beneficio:* Las tablas de enrutamiento del firewall central se mantienen ultraligeras y el backbone corporativo permanece estable frente a cortes internos en las sucursales.

## 2.3. Forced Tunneling (Salida Centralizada a Internet)

Ninguna sede tiene salida a Internet directa. El diseño fuerza todo el tráfico externo hacia el firewall perimetral del CPD Central para centralizar la auditoría.

1. El **Switch Core local** absorbe el tráfico de los usuarios y envía las peticiones externas hacia su FortiGate local mediante una ruta por defecto estática (`0.0.0.0/0`).
2. El **FortiGate de la filial** enruta todo este tráfico hacia el interior del túnel IPsec SD-WAN.
3. El **FortiGate 600F del CPD** recibe el tráfico encapsulado, lo desencripta, aplica las políticas NGFW (Antivirus, Filtrado Web, IPS) y le da salida a la red pública.

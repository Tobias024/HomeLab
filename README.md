# HomeLab

# Descripción

Esta documentación muestra el paso a paso de distintas configuraciones simulando una red empresarial con el uso de máquinas virtuales. Muestra estrategias y el uso de herramientas con las que se enfrentaron distintos retos.  

# Objetivo

Poner en práctica conocimiento teórico, aplicando el uso de herramientas tanto para Seguridad como para Infraestructura y redes.
La documentación va a estar dividida según casos de pruebas separando segun su fin:

- Foco en Seguridad: Acá van a ser testeadas las configuraciones de DNS, AD, DHCP, Siem, ataques y logs

- Foco en Infraestructura: Este en cambió tiene foco en la disponibilidad, el rendimiento, la seguridad como infraestructura y la identidad.


# Topología

Esta parte explica como se estructuró la red, que herramientas se usaron, como y por qué. La descripción del paso a paso está linkeado en cada titulo.
![Topografia](https://github.com/user-attachments/assets/ae4a7369-de41-4b1d-9954-ab4f8237cf3e)



## La red consta de:

[Firewall (PFsense)](docs/Firewall-PFsense/README.md)

### VLAN 10 — Management
- [Windows Server — AD, DNS, DHCP](docs/Windows-Server-AD-DNS-DHCP/README.md)

### VLAN 20 — Security
- [Servidor de Seguridad con Wazuh Manager](docs/Wazuh-Security-Server/README.md)

### VLAN 30 — Dev / CI-CD
- [W11 Dev Host](docs/W11DEV/README.md)
- [Servidor CI/CD — Gitea + Jenkins](docs/Servidor-CICD/README.md)

### VLAN 40 — DMZ
- [Servidor DMZ — Kong API Gateway](docs/Servidor-DMZ/README.md)

### VLAN 50 — Producción
- [Servidor Linux de Producción — Apps, Keycloak, Traefik](docs/Servidor-Linux-Produccion/README.md)

### VLAN 60 — Attack Lab
- Terminal Sec Host
- Terminal atacante con Kali


# VirtualBox

Contamos con 8 nucleos (16 buses) y 48 gb de Ram para distribuir entre las maquinas.

1. Instalar [VirtualBox](https://www.virtualbox.org/).
2. Crear una red para el proyecto:
    - Acceder a las redes y en la parte de "Nat networks" crear una nueva y modificar el nombre y rango IP.
        
        <img width="806" height="676" alt="image" src="https://github.com/user-attachments/assets/f1eb3ae0-bdf8-4851-8f52-c30111bd76cc" />

3. Configurar las Distintas MV (*Links en "[Topología](#topología)"*)

## VLANs
Vamos a contar con 3 VLANs por "cables fisicos" distribuidos para el Servidor de produccion (DMZ), servidores de gestion y Hosts. En una situacion real probablemente tendríamos muchas mas VLANs creadas para aislar los distintos sectores de la empresa para que en caso de que uno se vea comprometido no afecte al resto, siendo una barrera más de seguridad.
Dentro de la configuracion Red de la VM de pfsense prendemos los adaptadores y configuramos:
  - Adaptador 1: Puente (Bridge) o NAT (Tu salida a Internet/WAN).
  - Adaptador 2: Red Interna -> Nombre: VLAN_10_MGMT (Donde está el AD y Wazuh).
  - Adaptador 3: Red Interna -> Nombre: VLAN_20_DEV (Para el Windows 11).
  - Adaptador 4: Red Interna -> Nombre: VLAN_30_DMZ (Para el Server de Producción).
    <img width="777" height="389" alt="image" src="https://github.com/user-attachments/assets/e4646269-5eca-429c-9c90-63702a307422" />
El resto de las configuraciones de PFsense lo vamos a seguir en [Firewall (PFsense)](docs/Firewall-PFsense/README.md)

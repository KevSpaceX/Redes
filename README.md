# RedesParcial CiscoPt
enable
configure terminal
hostname Router1

interface gig0/0
ip address 192.10.1.1 255.255.255.0
no shutdown
exit

interface gig0/1
ip address 192.10.2.1 255.255.255.0
no shutdown
exit

interface serial0/0/0
ip address 192.10.2.2 255.255.255.252
no shutdown
exit

router rip
version 2
network 192.10.1.0
network 192.10.2.0
exit

write memory

Router2_config.txt

enable
configure terminal
hostname Router2

interface gig0/0
ip address 192.10.3.1 255.255.255.0
no shutdown
exit

interface gig0/1
ip address 192.10.4.1 255.255.255.0
no shutdown
exit

interface serial0/0/1
ip address 192.10.3.2 255.255.255.252
no shutdown
exit

router rip
version 2
network 192.10.3.0
network 192.10.4.0
exit

write memory

Switch0_config.txt

enable
configure terminal
hostname Switch0

vlan 10
name Ventas
exit

vlan 20
name IT
exit

interface range fa0/1 - 10
switchport mode access
switchport access vlan 10
exit

interface range fa0/11 - 20
switchport mode access
switchport access vlan 20
exit

interface fa0/24
switchport mode trunk
exit

write memory

README.md

# Configuración de Red en Cisco Packet Tracer

Este repositorio contiene la configuración de una red simulada en Cisco Packet Tracer. La red utiliza múltiples routers, switches, PCs, y servidores organizados en diferentes subredes y VLANs. Además, se ha configurado el protocolo RIP para el enrutamiento dinámico entre routers.

## Subredes y Direcciones IP

| Subred          | Dirección IP       | Máscara           |
|-----------------|--------------------|-------------------|
| Subred 1        | 192.10.1.0         | 255.255.255.0    |
| Subred 2        | 192.10.2.0         | 255.255.255.0    |
| Subred 3        | 192.10.3.0         | 255.255.255.0    |
| Subred 4        | 192.10.4.0         | 255.255.255.0    |
| Subred de enlace| 192.10.2.2/30      | 255.255.255.252  |

## Dispositivos y Configuraciones

- **Router1**: Configuración de interfaces para las subredes 192.10.1.0 y 192.10.2.0, enrutamiento dinámico RIP.
- **Router2**: Configuración de interfaces para las subredes 192.10.3.0 y 192.10.4.0, enrutamiento dinámico RIP.
- **Switch0**: Configuración de VLANs (Ventas e IT), asignación de puertos a VLANs y puerto troncal para conexión con Router1.

## Archivos de Configuración

- `Router1_config.txt`: Contiene la configuración de interfaces, RIP y asignación de direcciones IP para Router1.
- `Router2_config.txt`: Contiene la configuración de interfaces, RIP y asignación de direcciones IP para Router2.
- `Switch0_config.txt`: Configuración de VLANs y puertos en Switch0.

## Instrucciones para Clonar el Repositorio

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tuusuario/RedUniversitaria_Configuracion.git


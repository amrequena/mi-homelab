# Configuración del DHCP usando PowerShell

## Requisitos 
1. Ser administrador
2. Tener DHCP instalado en el servidor
3. Disponer de un cliente dentro del dominio. 
```powershell
Get-Service DHCPServer
```
4. Usar el servidor autorizado.
``` powershell
Get-DhcpServerInDC
```
## Configuración
### Crear el ámbito principal
```powershell
Add-DhcpServerV4Scope -Name "Red Homelab" -StartRange 192.168.1.100 -EndRange 192.168.1.200 -SubnetMask 255.255.255.0
```
### Configurar la puerta de enlace de los clientes
```powershell
Get-Service DHCPServer
```
### Crear el ámbito principal
```powershell
Get-Service DHCPServer
```

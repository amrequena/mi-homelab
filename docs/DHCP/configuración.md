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
### Verificar el ámbito creado
```powershell
Get-DhcpServerV4Scope
```
### Configurar la puerta de enlace del ámbito
```powershell
Set-DhcpServerV4OptionValue -ScopeId 192.168.1.0 -Router 192.168.1.1
```
### Configurar el servidor DNS
```powershell
Set-DhcpServerV4OptionValue -ScopeId 192.168.1.0 -DnsServer 192.168.1.10
```
### Configurar el dominio
```powershell
Set-DhcpServerV4OptionValue -ScopeId 192.168.1.0 -DnsDomain "homelab.com"
```
### Verificar la configuración completa
```powershell
Get-DhcpServerV4OptionValue -ScopeId 192.168.1.0
```
### Crear una reserva para impresoras
```powershell
Add-DhcpServerV4Reservation -ScopeId 192.168.1.0 -IPAddress 192.168.1.50 -ClientId "AA-BB-CC-DD-EE-FF" -Name "ImpresoraHP"
```


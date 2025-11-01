# Configuración de DHCP en Windows Server con PowerShell
## Requisitos
1. Ser administrador.
2. Tener IP estática.
```powershell
New-NetIPAddress -IPAddress "192.168.1.10" -PrefixLength 24 -InterfaceAlias "Ethernet" -DefaultGateway "192.168.1.1"
## Comprobar la configuración
Get-NetIPConfiguration
````
## Instalación 
### Instalación del servicio
```powershell
Install-WindowsFeauture DHCP -IncludeManagementTools
``` 
### Comprobación del servicio
```powershell
Get-Service DHCPServer
```
### Autorizar servidor DHCP en AD
```powershell
Add-DhcpServerInDC -DnsName "DC1"
```
### Verificar que está autorizado
```powershell
Get-DhcpServerInDC
```

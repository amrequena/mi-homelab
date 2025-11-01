# Configuración de DHCP en Windows Server con PowerShell

## Requisitos
1. Tener IP estática
```powershell
New-NetIPAddress -IPAddress "192.168.1.10" -PrefixLength 24 -InterfaceAlias "Ethernet" -DefaultGateway "192.168.1.1"
````
3. Ser administrador

## Instalación 

### Instalación del servicio
```powershell
Install-WindowsFeauture DHCP -IncludeManagementTools
``` 
### Comprobación del servicio
```powershell
Get-Service DHCPServer
```



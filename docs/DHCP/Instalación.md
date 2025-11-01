# Configuración de DHCP en Windows Server con PowerShell

## Requisitos
1. Tener IP estática
2. Ser administrador

## Instalación 

### Instalación del servicio
```powershell
Install-WindowsFeauture DHCP -IncludeManagementTools
``` 
### Comprobación del servicio
```powershell
Get-Service DHCPServer
```



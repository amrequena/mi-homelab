# Configuración de Controlador de dominio con PowerShell

## Método
Usamos PowerShell para promover Windows Server porque:
- Asegura consistencia.
- Permite automatización.
- Proporciona documentación completa.
- Escala fácilmente.

## Inventario
- VirtualBox
- Red NAT
- Windows Server 22

## Requisitos previos

### Configurar red
Debemos configurar una IP estática. 
```powershell
New-NetIPAddress -IPAddress "10.0.2.10" -PrefixLength 24 -InterfaceAlias "Ethernet" -DefaultGateway "10.0.2.2"
````
Configurar DNS (apuntar a sí mismo)
```powershell
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses "10.0.2.10"
````
Ver IP configurada
```powershell
Get-NetIPConfiguration
```

## Promover el servidor a controlador de dominio
Instalar características de Active Directory
```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
```
Promover servidor a controlador de dominio
```powershell
Install-ADDSDomainController -DomainName "tu-dominio.com" -InstallDns
```
Comprobar que está en el dominio
```powershell
Get-CimInstance Win32_ComputerSystem | Select-Object Name, Domain, PartOfDomain
```


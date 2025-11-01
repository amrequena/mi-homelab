# Configuración de Controlador de dominio con PowerShell

## Método

Usamos PowerShell para promover Windows Server porque:
- Asegura consistencia.
- Permite automatización.
- Proporciona documentación completa.
- Escala fácilmente.

## Requisitos previos

### Configurar red
Debemos configurar una IP estática. 
```powershell
New-NetIPAddress -IPAddress "192.168.1.10" -PrefixLength 24 -InterfaceAlias "Ethernet" -DefaultGateway "192.168.1.1"
````
Configurar DNS (apuntar a sí mismo)
```powershell
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses "192.168.1.10"
````
Ver IP configurada
```powershell
Get-NetIPConfiguration
```

## Instalación
Instalar características de Active Directory
```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
```

## Configuración
Crear el bosque/dominio
```powershell
Install-ADDSForest 
    -DomainName "homelab.com" 
    -DomainNetbiosName "HOMELAB" 
    -InstallDns 
    -SafeModeAdministratorPassword (ConvertTo-SecureString "TuPassword123!" -AsPlainText -Force) 
    -Force
```
Comprobar que es controlador de dominio
```powershell
Get-ADDomainController
```
Verificar información del dominio
```powershell
Get-ADDomain
```





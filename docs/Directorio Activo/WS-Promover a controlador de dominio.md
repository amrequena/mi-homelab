# Configuración de Controlador de dominio con PowerShell

## Requisitos previos.
1. Ser administrador
2. Tener una IP estática
```powershell
New-NetIPAddress -IPAddress "192.168.1.10" -PrefixLength 24 -InterfaceAlias "Ethernet" -DefaultGateway "192.168.1.1"
````
   2.1. Ver IP configurada
```powershell
Get-NetIPConfiguration
```
3. Configurar el DNS
Configurar DNS (apuntar a sí mismo)
```powershell
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses "192.168.1.10"
````
   3.1. Ver IP configurada
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





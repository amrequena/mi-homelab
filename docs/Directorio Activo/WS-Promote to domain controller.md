# Configuración de Controlador de dominio con PowerShell

## Método
Usamos PowerShell para promover Windows Server porque:
- Asegura consistencia.
- Permite automatización.
- Proporciona documentación completa.
- Escala fácilmente.

## Inventario
- Windows Server 22

## Requisitos previos

### Configurar red
Debemos configurar una IP estática. 

```powershell
# Configurar IP
New-NetIPAddress -IPAddress "192.168.1.10" -PrefixLength 24 -DefaultGateway "192.168.1.1" -InterfaceAlias "Ethernet"

# Configurar DNS (apuntar a sí mismo)
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses "192.168.1.10"

# Ver IP configurada
Get-NetIPAddress

# Ver DNS configurado
Get-DnsClientServerAddress

# Ver configuración completa
ipconfig /all
```

## Promover el servidor a controlador de dominio

```powershell
# Instalar características de Active Directory
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools

# Promover servidor a controlador de dominio
Install-ADDSDomainController -DomainName "tu-dominio.com" -InstallDns
```



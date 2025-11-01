Configuración de servidor DHCP con PowerShell
Método
Usamos PowerShell para promover Windows Server porque:

Asegura consistencia.
Permite automatización.
Proporciona documentación completa.
Escala fácilmente.

Requisitos previos
Configurar red
Debemos configurar una IP estática.

New-NetIPAddress -IPAddress "192.168.1.10" -PrefixLength 24 -InterfaceAlias "Ethernet" -DefaultGateway "192.168.1.1"
Configurar DNS (apuntar a sí mismo)

Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses "192.168.1.10"
Ver IP configurada

Get-NetIPConfiguration
Promover el servidor a controlador de dominio
Instalar características de Active Directory

Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
Crear el bosque/dominio

Install-ADDSForest 
    -DomainName "homelab.com" 
    -DomainNetbiosName "HOMELAB" 
    -InstallDns 
    -SafeModeAdministratorPassword (ConvertTo-SecureString "TuPassword123!" -AsPlainText -Force) 
    -Force
Comprobar que es controlador de dominio

Get-ADDomainController
Verificar información del dominio

Get-ADDomain

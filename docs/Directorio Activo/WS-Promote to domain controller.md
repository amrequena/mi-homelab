# Configuración de Controlador de Dominio con PowerShell

## Método
Usamos PowerShell para promover Windows Server porque:
- Asegura consistencia.
- Permite automatización.
- Proporciona documentación completa.
- Escala fácilmente.

## Comandos PowerShell

```powershell
# Instalar características de Active Directory
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools

# Promover servidor a controlador de dominio
Install-ADDSDomainController -DomainName "tu-dominio.com" -InstallDns
```

## Configuración
- Dominio: Controlador de dominio remoto
- Constantes: Active Directory
- Herramientas: PowerShell

# Comandos básicos de Powershell
## Comandos de administración 
### Ver el hostname
```powershell
hostname
```
### Cambiar hostname 
```powershell
Rename-Computer -NewName "NUEVO-NOMBRE"
```
### Cambiar hostname y reiniciar
```powershell
Rename-Computer -NewName "NUEVO-NOMBRE" -Restart 
```
## Comandos de red
### Ver IP
```powershell
Get-NetIPConfiguration
```
### Probar si tienes internet
```powershell
Test-Connection google.com
```
### Diagnosticar DNS
```powershell
Resolve-DnsName google.com
```
### Ver adaptadores de red
```powershell
Get-NetAdapter
```
### Cambiar IP estática
```powershell
New-NetIPAddress -IPAddress "192.168.1.10" -PrefixLength 24 -InterfaceAlias "Ethernet"
```
### Ver conexiones activas
```powershell
Get-NetTCPConnection
```



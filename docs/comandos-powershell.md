# Comandos Powershell

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
### Ver adaptadores de red
```powershell
Get-NetAdapter
```

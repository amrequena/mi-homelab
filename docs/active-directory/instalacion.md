# 🖥️ Instalación de Windows Server en Home Lab

## Objetivo
Instalar y configurar Windows Server 2022 como controlador de dominio para prácticas de Azure Hybrid.

## Especificaciones Técnicas
- **Hypervisor:** Hyper-V
- **RAM asignada:** 4GB  
- **Almacenamiento:** 50GB
- **Sistema:** Windows Server 2022 Standard

## Proceso de Instalación

### 1. Descarga del SO
- Descargado desde Microsoft Imagine/Student
- ISO: `Windows_Server_2022.iso`

### 2. Configuración de la VM
```powershell
# Crear VM básica en Hyper-V
New-VM -Name "DC-HomeLab" -MemoryStartupBytes 4GB -Path "C:\VMs\"

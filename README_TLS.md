# Cliente Tauri - Guardias Web

## Configuración TLS 1.2 para Windows 7

Este cliente Tauri incluye los archivos necesarios para habilitar TLS 1.2 en Windows 7.

### Archivos incluidos en el instalador

1. **`habilitarTLS-W7.reg`**: Archivo de registro que habilita TLS 1.2
2. **`aplicar-tls.cmd`**: Script para aplicar la configuración de forma sencilla

### Proceso de instalación y configuración

#### 1. Instalación normal
Ejecutar el instalador: `GuardiasWeb_0.1.0_x64-setup.exe`

#### 2. Aplicar configuración TLS (POST-INSTALACIÓN)
**Importante**: Después de instalar la aplicación, ejecutar como **Administrador**:
```
[Directorio de instalación]\aplicar-tls.cmd
```

Por ejemplo:
```
C:\Program Files\GuardiasWeb\aplicar-tls.cmd
```

### Construcción

Para construir el cliente:

```cmd
build.cmd
```

Este script:
- Verifica que los archivos TLS estén presentes
- Construye la aplicación Tauri
- Incluye automáticamente los archivos TLS en el instalador
- Muestra instrucciones post-instalación

### Configuración TLS incluida

El archivo `habilitarTLS-W7.reg` habilita TLS 1.2 en Windows 7 configurando:

```
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client]
"DisabledByDefault"=dword:00000000
"Enabled"=dword:00000001
```

### Requisitos

- **Para construcción**: Rust y Tauri CLI
- **Para instalación**: Windows 7 SP1 o superior
- **Para configuración TLS**: Privilegios de administrador

### Notas importantes

- ⚠️ **La configuración TLS debe aplicarse DESPUÉS de la instalación**
- ⚠️ **Se requieren privilegios de administrador** para aplicar la configuración
- ✅ La configuración TLS se aplica a nivel del sistema (beneficia a todas las aplicaciones)
- ✅ Si falla la configuración TLS, la aplicación seguirá funcionando (solo afectará la conectividad HTTPS en Windows 7)

### Resolución de problemas

**Si la aplicación no puede conectarse en Windows 7:**
1. Verificar que se ejecutó `aplicar-tls.cmd` como administrador
2. Reiniciar la aplicación después de aplicar la configuración TLS
3. En casos extremos, reiniciar Windows

# **Tema 5: Linux - Gestión de Usuarios y Grupos. Gestión de Procesos**
###### 20/02/25
## **1. Usuarios y Grupos**

En Linux, los usuarios y grupos son fundamentales para la administración del sistema. Cada usuario posee un **UID (User ID)** único, y cada grupo tiene un **GID (Group ID)**. El sistema de permisos en Linux se basa en la pertenencia a grupos y en la asignación de privilegios a archivos y directorios.

Cada usuario en Linux pertenece a un **grupo primario o principal** (identificado con su UID) y puede estar en **grupos secundarios** para tener acceso a archivos compartidos o privilegios específicos.

- **UID (User ID)**: Número único que identifica a cada usuario.
- **GID (Group ID)**: Número único que identifica a cada grupo.
- **Grupo Primario**: Es el grupo principal del usuario y se asigna automáticamente al crear el usuario.
- **Grupos Secundarios**: Son grupos adicionales a los que puede pertenecer un usuario, otorgándole permisos adicionales.

---

## **1.1. Tipos de Usuarios**

### **1.1.1. Usuario Root**
El **usuario root** (UID=0) es el administrador del sistema con permisos totales. Puede realizar cualquier cambio, incluyendo modificar archivos críticos, instalar software y administrar usuarios. Se recomienda usarlo solo cuando sea necesario, para evitar riesgos de seguridad.

### **1.1.2. Usuarios del Sistema**
Los **usuarios del sistema** son creados automáticamente por el sistema operativo y los servicios instalados. Se asignan **UIDs del 1 al 999** en muchas distribuciones de Linux. Un usuario especial es `nobody`, que tiene el UID **65534**, utilizado para procesos que requieren acceso mínimo a recursos.

Ejemplo de usuarios del sistema:
- `daemon` (UID=1) → Ejecuta procesos del sistema.
- `syslog` (UID=104) → Maneja registros del sistema.
- `nobody` (UID=65534) → Usuario con permisos mínimos.

Estos usuarios normalmente no tienen acceso de inicio de sesión.

### **1.1.3. Usuarios Normales**
Los **usuarios normales** son aquellos creados manualmente o durante la instalación del sistema. Su UID se asigna a partir de **1000 en adelante** (en la mayoría de distribuciones). Estos usuarios trabajan en su directorio personal dentro de `/home/usuario/` y tienen permisos restringidos.

#### **Permisos de los Usuarios Normales**
- Pueden acceder y modificar sus propios archivos.
- No pueden modificar archivos de otros usuarios ni del sistema.
- Pueden acceder a archivos de otros usuarios si tienen permisos adecuados.
- No pueden instalar software ni modificar configuraciones críticas, salvo que tengan privilegios de administrador (sudo).

Cuando un usuario se convierte en administrador mediante `sudo`, puede ejecutar comandos con privilegios de root temporalmente.

```bash
sudo apt update  # Ejecuta la actualización del sistema como root```

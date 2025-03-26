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
sudo apt update  # Ejecuta la actualización del sistema como root
```

## **5.1.2 Ficheros de Configuración**

###### 21/02/25

Los archivos de configuración en Linux almacenan información esencial sobre los usuarios, grupos y políticas del sistema. Estos archivos se encuentran en el directorio `/etc/` y son utilizados por herramientas de gestión de usuarios y autenticación.

A continuación, se detallan los archivos más importantes:

### **📂 /etc/passwd**
Este archivo contiene la información básica de los usuarios del sistema. Cada línea representa un usuario y tiene la siguiente estructura:

```
usuario:x:UID:GID:comentario:directorio_home:shell
```

| Campo | Descripción |
|--------|--------------------------------------------|
| **usuario** | Nombre del usuario. |
| **x** | Indica que la contraseña está en `/etc/shadow`. |
| **UID** | Identificador único del usuario. |
| **GID** | Identificador del grupo principal del usuario. |
| **comentario** | Información opcional sobre el usuario. |
| **directorio_home** | Directorio de trabajo del usuario (Ej: `/home/usuario`). |
| **shell** | Intérprete de comandos asignado (Ej: `/bin/bash`). |

Ejemplo de línea en `/etc/passwd`:
```
yara:x:1001:1001:Usuario Yara:/home/yara:/bin/bash
```

---

### **📂 /etc/shadow**
Contiene las contraseñas cifradas de los usuarios y otros parámetros relacionados con la autenticación.

```
usuario:$6$hashcifrado:fecha_ultima_cambio:min:max:aviso:inactividad:expiracion:reserva
```

| Campo | Descripción |
|--------|--------------------------------------------|
| **usuario** | Nombre del usuario. |
| **$6$hashcifrado** | Contraseña encriptada en SHA-512. |
| **fecha_ultima_cambio** | Días desde 01/01/1970 del último cambio de contraseña. |
| **min** | Mínimos días antes de cambiar la contraseña. |
| **max** | Máximos días antes de forzar cambio de contraseña. |
| **aviso** | Días antes de la expiración para avisar al usuario. |
| **inactividad** | Días tras expiración en que se desactiva la cuenta. |
| **expiracion** | Fecha en que la cuenta expira. |
| **reserva** | Reservado para uso futuro. |

Ejemplo:
```
yara:$6$Jfnc72hjsdP$7c0987ghlsdf789:19000:7:90:7:30:20000:
```

---

### **📂 /etc/group**
Este archivo lista los grupos del sistema. Su estructura es:

```
nombre_grupo:x:GID:usuarios_miembros
```

Ejemplo:
```
sudo:x:27:yara,pedro
```
Aquí, `sudo` es un grupo con `GID 27`, y los usuarios `yara` y `pedro` son miembros.

---

### **📂 /etc/gshadow**
Similar a `/etc/group`, pero contiene contraseñas cifradas para grupos.

Ejemplo:
```
sudo:!::
```

---

### **📂 /etc/default/useradd**
Contiene valores predeterminados para la creación de nuevos usuarios.

Ejemplo de configuración:
```
GROUP=100
HOME=/home
INACTIVE=-1
SHELL=/bin/bash
SKEL=/etc/skel
```

---

### **📂 /etc/adduser.conf**
Configura opciones avanzadas para `adduser`.

Ejemplo:
```
DSHELL=/bin/bash
DHOME=/home
FIRST_UID=1000
LAST_UID=60000
FIRST_GID=1000
LAST_GID=60000
```

---

### **📂 /etc/deluser.conf**
Contiene opciones para eliminar usuarios.

Ejemplo:
```
REMOVE_HOME = 0
REMOVE_ALL_FILES = 0
BACKUP = 0
```

Si `REMOVE_HOME = 1`, se eliminará el directorio `/home/usuario` al borrar un usuario.

---

### **📂 /etc/login.defs**
Define políticas de seguridad en el login.

Ejemplo:
```
PASS_MAX_DAYS 90
PASS_MIN_DAYS 7
PASS_WARN_AGE 7
UID_MIN 1000
UID_MAX 60000
GID_MIN 1000
GID_MAX 60000
```
- `PASS_MAX_DAYS 90`: La contraseña debe cambiarse cada 90 días.
- `PASS_WARN_AGE 7`: Se avisa con 7 días de anticipación.

---

### **📂 /etc/shells**
Lista los shells disponibles en el sistema.

Ejemplo:
```
/bin/sh
/bin/bash
/usr/bin/zsh
```

Si un usuario tiene `/usr/sbin/nologin` como shell, significa que **no puede iniciar sesión**.

Aquí tienes la sección en **Markdown** con la información sobre **`/etc/skel`** para que la añadas al cuaderno:

---

## **📂 Directorios de Configuración: `/etc/skel`**

El directorio `/etc/skel` es utilizado como una plantilla para la creación de nuevos usuarios en el sistema. Cuando se añade un nuevo usuario con `useradd`, su directorio **`/home/usuario`** se genera copiando el contenido de `/etc/skel`.

### **📌 Función de `/etc/skel`**
- Al crear un nuevo usuario, se copian automáticamente los archivos y carpetas de `/etc/skel` a su directorio personal.
- Se pueden incluir archivos de configuración predeterminados como `.bashrc`, `.profile` o `.vimrc` para establecer configuraciones iniciales.

### **📂 Contenido habitual de `/etc/skel`**
Por defecto, `/etc/skel` puede contener archivos como:

```
/etc/skel/
├── .bashrc
├── .profile
├── .bash_logout
```

- **`.bashrc`** → Configuración del shell Bash para cada usuario.
- **`.profile`** → Configuración del entorno de usuario.
- **`.bash_logout`** → Comandos ejecutados al cerrar sesión.

### **📌 Personalización de `/etc/skel`**
El administrador puede agregar o modificar archivos en `/etc/skel` para que todos los nuevos usuarios los reciban automáticamente.

Ejemplo: Si queremos que cada usuario nuevo tenga un directorio `Documentos`, podemos hacer:

```bash
mkdir /etc/skel/Documentos
```

Ahora, cualquier usuario nuevo tendrá automáticamente una carpeta `~/Documentos`.

### **📌 Consideraciones**
- **No afecta a usuarios ya creados**, solo a nuevos usuarios.
- **Debe ser accesible solo para root** para evitar modificaciones no autorizadas.


---


## **6.1 Variables**

###### 26/03/25
Las **variables** en Linux representan espacios en la memoria que almacenan información. Pueden contener valores o estar vacías. Su valor puede cambiar durante la ejecución del sistema o de scripts.

Existen **dos tipos principales** de variables en Linux:

---

### 🔹 **Variables Locales**

- Solo son visibles dentro de la **shell actual**.
- Se crean simplemente al asignarles un valor.
- Se accede a ellas anteponiendo el símbolo `$`.

#### ✅ **Ejemplo:**
```bash
fruta_favorita="manzana"
echo "Tu fruta favorita es $fruta_favorita"
```

---

### 🔹 **Variables del Entorno**

- Son accesibles desde **todas las shells y procesos** derivados.
- Se suelen escribir en **mayúsculas** por convención.
- Se declaran con `export` o se definen en archivos como:
  - `/etc/environment`
  - `/etc/default/locale`
  - `/etc/profile`

#### ✅ Para que los cambios tengan efecto:
- Hay que **reiniciar la shell** o **reiniciar el entorno**.

---

### 🔹 **Variables de Entorno Comunes**

| Variable   | Descripción                                                                 |
|------------|------------------------------------------------------------------------------|
| `HOME`     | Ruta al directorio personal del usuario.                                    |
| `USER`     | Nombre del usuario actual.                                                  |
| `SHELL`    | Ruta al intérprete de comandos (por ejemplo: `/bin/bash`).                  |
| `HOSTNAME` | Nombre del sistema/equipo.                                                  |
| `TERM`     | Tipo de terminal utilizado.                                                 |
| `LOGNAME`  | Usuario que inició sesión.                                                  |
| `PATH`     | Directorios en los que el sistema busca ejecutables.                        |
| `PWD`      | Directorio de trabajo actual.                                               |
| `OLDPWD`   | Último directorio visitado (útil para `cd -`).                              |

---

### 🧠 **PS1 y PS2: Prompts del Shell**

- **`PS1` (Prompt String 1)**:  
  Define el **formato del prompt principal** (lo que ves al abrir la terminal).  
  Puedes personalizarlo con variables como `\u` (usuario), `\h` (host), `\w` (directorio actual).

  #### ✅ Ejemplo:
  ```bash
  PS1="\u@\h:\w$ "
  ```
  Esto mostraría: `usuario@equipo:/ruta/actual$`

- **`PS2` (Prompt String 2)**:  
  Aparece cuando un comando no ha terminado (por ejemplo, una comilla sin cerrar).

  #### ✅ Ejemplo:
  ```bash
  echo "Hola
  > mundo"
  ```

  El símbolo `>` es el prompt PS2, indicando que espera que completes el comando.

---

### 🗂️ **Archivo `.bashrc`**

- Archivo de configuración **personal** que se ejecuta al iniciar sesión.
- Permite **definir variables locales permanentes** para el usuario.
- Se encuentra en el **directorio personal del usuario** (`~/.bashrc`).

#### ✅ Ejemplo:
```bash
export EDITOR=nano
```

Esto hará que el sistema use `nano` como editor de texto predeterminado para ese usuario.
### **📌 Conclusión**
Estos archivos son esenciales para la gestión de usuarios y seguridad en Linux. Manipularlos incorrectamente puede comprometer el sistema, por lo que deben modificarse con herramientas como `usermod`, `passwd` y `groupmod` en lugar de editarlos manualmente.

Perfecto, aquí tienes una explicación extendida para las opciones más relevantes de `env` y `echo`, en formato Markdown para tu cuaderno:

## 🛠️ Comandos básicos relacionados con variables

### **`set`**
Muestra todas las variables **(locales y del entorno)** definidas en la shell actual.

```bash
set
```

---

### **`env`**
Muestra únicamente las variables de **entorno**. También permite ejecutar comandos con un entorno modificado.

- **`-u`**: Elimina una variable del entorno antes de ejecutar el comando.
  
```bash
env -u USER env     # Ejecuta env sin la variable USER
```

---

### **`export`**
Convierte una variable **local en variable de entorno**, o crea una nueva variable de entorno.

```bash
export NOMBRE=valor
```

---

### **`unset`**
Elimina una variable del entorno o de la shell. Si era de entorno, deja de heredarse.

```bash
unset NOMBRE
```

---

### **`echo`**
Muestra texto o el valor de variables.

```bash
echo $NOMBRE
```

#### Opciones comunes:
- `-n`: No imprime salto de línea al final.
- `-e`: Habilita la interpretación de caracteres especiales (por defecto se ignoran).

#### Caracteres especiales con `-e`:
- `\n`: Salto de línea.
- `\t`: Tabulación.
- `\c`: Finaliza la línea (descarta lo que viene después).

```bash
echo -e "Hola\tmundo\nEsto es un salto de línea"
echo -e "Esto se detiene aquí\cNO SE IMPRIME"
```

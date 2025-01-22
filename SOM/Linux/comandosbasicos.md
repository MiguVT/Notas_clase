# Comandos Básicos de Linux

Esta sección cubre algunos de los comandos más útiles en Linux para interactuar con el sistema y obtener información sobre él.

---

### `date`
Muestra la fecha y hora del sistema. También te ofrece la opción de cambiarlas.

**Ejemplo:**
```bash
date
```

---

### `cal [-3my] [[mes] año]`
Muestra el calendario del mes y año que se le indique.

**Opciones:**
- `-3`: Muestra el mes actual, el anterior y el próximo.
- `-m`: Muestra el lunes como primer día de la semana.
- `-y`: Muestra el calendario de todo el año actual.

**Argumentos:**
- `mes`: Mes que deseas mostrar. Si no se especifica, se muestra el mes actual.
- `año`: Año que deseas mostrar. Si no se especifica, se usa el año actual.

**Ejemplo:**
```bash
cal -3 2025
```

---

### `who`
Muestra los usuarios conectados al sistema.

**Opciones:**
- `-a`/`--all`: Muestra información adicional sobre los usuarios conectados (como el inicio de sesión, la terminal y el tiempo de actividad).

**Ejemplo:**
```bash
who
```

---

### `whoami`
Muestra el nombre del usuario actual, útil para saber si estás conectado como root o no.

**Ejemplo:**
```bash
whoami
```

---

### `man [comando]` / `info [comando]`
Muestra la ayuda detallada de un comando específico. Algunos comandos también ofrecen la opción `-h` o `--help` para mostrar una ayuda más breve.

**Ejemplo:**
```bash
man ls
info ls
```

---

### `clear`
Borra la pantalla de la terminal.

**Ejemplo:**
```bash
clear
```

**Nota:** Personalmente, suelo crear un alias para que también funcione como `cls` al estilo de Windows.

---

### `whereis [comando]`
Ubica el binario, el código fuente y las páginas de manual de un comando.

**Ejemplo:**
```bash
whereis ls
```

**Resultado:**
Muestra las rutas de las ubicaciones del comando, como la carpeta del binario y las páginas de manual.

---

### `alias [nombre] = "[comando]"` 
Crea un alias para un comando. Esto permite usar comandos más cortos o personalizados.

**Ejemplo:**
```bash
alias cls="clear"
alias ll="ls -la"
```

**Nota:** Puedes ver todos los alias definidos con el comando `alias` sin argumentos.

---

### `unalias [alias]` 
Elimina un alias.

**Ejemplo:**
```bash
unalias cls
unalias ll
```

**Opciones:**
- `-a`: Elimina todos los alias existentes.


---

### `uname [opciones]` 
Muestra info del sistema operativo y el equipo.

**Ejemplo:**
```bash
uname (-s)
```

**Opciones:**
- `-s`: Opcion predeterminada si no se especifica ninguna, muestra el nombre del nucleo.

---

# Actividades pag 106
Esta sección cubre las "Actividades de aplicación" de la pag 106.

- 3.12 `cal -m feb 2007`
- 3.13 `date`
- 3.14 `clear` (o `cls` si tienes el alias como en mi caso)
- 3.15 `history`
- 3.16 `neofetch` (hay otras opciones, pero es la que personalmente yo uso, se puede hacer manual con `uname -r`, `cat /proc/version`, entre otras, el que esta documentado en el libro es `uname -a`)
- 3.17 `info wh`
- 3.18 `alias meses="clear; cal -3; whoami"`
- 3.19 `alias conectados="clear; date; who"`
- 3.20 `alias`
- 3.21 `unalias -a` (En el caso de tener otros alias, podriamos usar `unalias conectados meses`)

---

Aquí está la versión mejorada de la sección sobre gestión de archivos y directorios, incluyendo la diferencia entre enlaces simbólicos y enlaces directos en formato de tabla:

---

# Gestión de Archivos

Un archivo o fichero es un conjunto de información relativa a un mismo concepto que se almacena bajo un nombre que lo identifica. Este nombre puede tener entre 1 y 255 caracteres, formados por cualquier carácter excepto `/`, que se utiliza para el directorio raíz y como separador en las rutas.

### **¿Qué es un i-nodo?**
Un i-nodo (inode) es una entrada en una tabla especial del sistema de archivos que almacena información sobre cada archivo. Esta tabla se llama **tabla de i-nodos** y se crea al arrancar el sistema operativo.

El sistema operativo identifica cada archivo no solo por su nombre, sino también por su **número de i-nodo**, que es único dentro de todo el sistema de archivos.

#### Información almacenada en un i-nodo:
- **Número de i-nodo**: Identificador único del archivo.
- **Tipo de archivo**: Indica si es un archivo regular, un directorio, un enlace, etc.
- **Propietario y grupo**: Información del usuario y grupo propietario.
- **Permisos**: Definen quién puede leer, escribir o ejecutar el archivo.
- **Fechas importantes**:
  - **Creación**: Momento en que se creó el archivo.
  - **Último acceso**: Fecha y hora de la última lectura.
  - **Modificación**: Momento en que se modificaron los datos.
- **Número de enlaces**: Cantidad de nombres o rutas que apuntan al mismo archivo.
- **Tamaño**: Tamaño del archivo en bytes.
- **Bloques asignados**: Información sobre los bloques físicos en el disco donde se almacenan los datos.

Cuando se realiza cualquier cambio en un atributo del archivo, se actualiza automáticamente la entrada correspondiente en la tabla de i-nodos. En el disco, se mantiene una copia de esta tabla que se sincroniza regularmente. Los archivos no utilizados en ese momento tienen su i-nodo guardado únicamente en el disco.

### **Tipos de archivos en Linux**
Un archivo puede variar según su función o el tipo de información que contenga:
1. Archivos regulares.
2. Directorios.
3. Enlaces (simbólicos o directos).
4. Archivos especiales (de dispositivos, pipes, sockets, etc.).

---

### **Diferencia entre Enlaces Simbólicos y Enlaces Directos**

En Linux, los enlaces permiten acceder a un archivo o directorio desde diferentes ubicaciones. Hay dos tipos principales de enlaces:

| **Aspecto**             | **Enlace Simbólico (Soft Link)**                       | **Enlace Directo (Hard Link)**                       |
|--------------------------|-------------------------------------------------------|-----------------------------------------------------|
| **Definición**           | Es un archivo especial que apunta a otro archivo o directorio mediante su ruta. | Es una referencia directa al mismo i-nodo del archivo original. |
| **Relación con el i-nodo** | Crea un nuevo i-nodo que contiene la ruta al archivo original. | Apunta al mismo i-nodo que el archivo original.     |
| **Dependencia**          | Si el archivo original se elimina, el enlace simbólico queda roto (inválido). | El enlace sigue funcionando mientras exista al menos un hard link. |
| **Uso entre sistemas**   | Puede apuntar a archivos en diferentes sistemas de archivos. | Solo funciona dentro del mismo sistema de archivos. |
| **Modificaciones**       | Cambios en el archivo original se reflejan en el enlace. | Cambios en cualquier enlace afectan al archivo porque comparten el i-nodo. |
| **Identificación**       | El tamaño del enlace simbólico es pequeño, ya que solo contiene la ruta al archivo. | Comparte el tamaño del archivo original.            |
| **Comando de creación**  | `ln -s archivo_origen enlace_simbólico`               | `ln archivo_origen enlace_directo`                  |

---

### **Ficheros Ocultos**
En Linux, los ficheros ocultos son aquellos cuyo nombre comienza con un punto (`.`). Estos archivos suelen ser utilizados para almacenar configuraciones o datos que no necesitan ser visibles en el uso diario del sistema.

#### **Características básicas:**
- **Nombre**: Siempre empiezan con `.` (ejemplo: `.bashrc`, `.config`).
- **Visibilidad**: No se muestran de forma predeterminada al listar archivos con `ls`. Para verlos, usa la opción `-a` o `-A`:
  ```bash
  ls -a
  ```
- **Propósito**: Almacenan configuraciones del sistema, aplicaciones o del usuario.

#### **Ejemplo de creación de un fichero oculto:**
```bash
touch .mi_configuracion
```

---

### **Ficheros de Configuración**
Los ficheros de configuración son archivos que almacenan ajustes o parámetros utilizados por el sistema operativo, aplicaciones o el entorno de usuario. Estos archivos controlan el comportamiento del software o del sistema.

#### **Características principales:**
- **Ubicación común**: Se encuentran en `/etc` para configuraciones globales del sistema o en el directorio del usuario (archivos ocultos) para configuraciones personales.
- **Formato**: Generalmente son archivos de texto plano, por lo que se pueden leer y editar con un editor de texto como `nano` o `vim`.
- **Nombres típicos**: Suelen terminar con `.conf` o empezar con un punto (ficheros ocultos).

---

### **Ejemplos de ficheros de configuración**

#### 1. **`/boot/grub/grub.cfg`**  
Este archivo pertenece al cargador de arranque GRUB y se utiliza para configurar cómo se inicia el sistema operativo.

- **Ubicación**: `/boot/grub/grub.cfg`
- **Propósito**: 
  - Define qué sistemas operativos están instalados y cómo se seleccionan en el arranque.
  - Configura parámetros avanzados como la resolución de la pantalla en el menú de arranque.
- **Nota**: No se recomienda editar este archivo manualmente. En su lugar, se deben realizar cambios en `/etc/default/grub` y luego ejecutar:
  ```bash
  sudo update-grub
  ```

#### 2. **`~/.bashrc`**  
El archivo `.bashrc` almacena configuraciones específicas para el intérprete de comandos Bash.

- **Ubicación**: En el directorio personal de cada usuario (por ejemplo, `/home/usuario/.bashrc`).
- **Propósito**:
  - Definir alias personalizados.
  - Configurar variables de entorno.
  - Ejecutar comandos automáticamente al iniciar una nueva sesión de terminal.
- **Ejemplo de alias en `.bashrc`:**
  ```bash
  alias ll="ls -la"
  export PATH=$PATH:/ruta/adicional
  ```
- **Cómo aplicar los cambios tras editarlo**:
  ```bash
  source ~/.bashrc
  ```

---

# **Directorios o Carpetas**

En Linux, los directorios son equivalentes a las carpetas en otros sistemas operativos. Se utilizan para organizar archivos y otros directorios.

---

### **Directorios Especiales:**
1. **`.` (Directorio actual):**  
   Representa el directorio en el que te encuentras actualmente.

2. **`..` (Directorio padre):**  
   Representa el directorio que contiene al actual. Por ejemplo, moverte al directorio padre:
   ```bash
   cd ..
   ```

3. **Directorio personal (`~`):**  
   Es el directorio privado de cada usuario, normalmente ubicado en `/home/usuario`. Puedes acceder con:
   ```bash
   cd ~
   ```

---

### **Rutas:**
1. **Ruta absoluta:**  
   Especifica la ubicación completa de un archivo o directorio desde la raíz (`/`).
   - Ejemplo: `/home/usuario/documentos`

2. **Ruta relativa:**  
   Especifica la ubicación de un archivo o directorio desde el directorio actual.
   - Ejemplo: Si estás en `/home/usuario`, la ruta relativa a `documentos` sería:
     ```bash
     cd documentos
     ```

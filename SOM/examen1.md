### **Examen de Sistemas Operativos Monopuesto**

---

## **1. Gestión de Usuarios**
### **Tipos de usuarios**
1. **Usuario estándar**:
   - Puede usar software instalado y realizar cambios menores.
   - No puede instalar ni desinstalar programas.
2. **Usuario administrador**:
   - Acceso total al sistema y configuraciones avanzadas.

### **Gestión desde la interfaz gráfica**
1. **Creación de usuarios**:
   - `Herramientas del sistema > Usuarios y grupos locales > Usuarios`.
   - Clic derecho → `Nuevo usuario`. Completar campos necesarios:
     - Contraseña, opciones de expiración o bloqueo.
2. **Eliminación de usuarios**:
   - Clic derecho sobre la cuenta → `Eliminar`.
3. **Propiedades de usuario**:
   - Cambiar contraseña, permisos, o habilitar/deshabilitar usuarios.

### **Gestión desde la línea de comandos (CMD)**
- **Crear usuario**:  
  ```bash
  net user nombre_usuario contraseña /add
  ```
- **Eliminar usuario**:  
  ```bash
  net user nombre_usuario /delete
  ```
- **Modificar contraseña**:  
  ```bash
  net user nombre_usuario nueva_contraseña
  ```
- **Agregar usuario a un grupo**:  
  ```bash
  net localgroup nombre_grupo nombre_usuario /add
  ```
- **Configurar expiración de cuenta**:  
  ```bash
  net user nombre_usuario /expires:dd/mm/yyyy
  ```

---

## **2. Gestión de Archivos y Directorios**
### **Comandos básicos**
1. **Crear directorios**:  
   ```bash
   md nombre_directorio
   ```
2. **Cambiar directorio**:  
   ```bash
   cd nombre_directorio
   ```
   - Subir al directorio padre: `cd ..`.
3. **Eliminar directorios**:  
   ```bash
   rd nombre_directorio /S
   ```
   (`/S` incluye contenido del directorio).
4. **Mover directorios**:  
   ```bash
   move origen destino
   ```
5. **Copiar directorios**:  
   ```bash
   xcopy origen destino /e
   ```
   - `/e`: Copia subdirectorios vacíos.
   - `/t`: Solo estructura.

### **Visualización de contenido**
- **Listar archivos y carpetas**:  
  ```bash
  dir
  ```
- **Mostrar en formato árbol**:  
  ```bash
  tree /f
  ```

### **Ejercicios relevantes**
- Crear estructuras jerárquicas con subdirectorios y archivos.
- Practicar con `move`, `xcopy`, y `tree`.

---

## **3. Gestión de Discos**
### **Desfragmentador de disco**
- Mejora el rendimiento organizando archivos fragmentados.
  - Uso: `Inicio > Desfragmentador de disco > Analizar > Desfragmentar`.

### **Liberación de espacio**
1. Vaciar papelera de reciclaje.
2. Eliminar archivos temporales de Internet y Windows:
   - Herramienta: `Liberador de espacio en disco`.

### **Chequeo de disco**
- Comprobar integridad del disco y reparar errores:
  - `Propiedades del disco > Herramientas > Comprobar ahora`.

### **Conversión de sistemas de archivos**
- Convertir de FAT a NTFS:  
  ```bash
  convert C: /FS:NTFS
  ```

### **Copias de seguridad**
1. **Crear copia de seguridad** en un disco externo.
2. **Restaurar copia** utilizando herramientas de Windows.

---

## **4. El Registro de Windows**
### **Introducción**
- Contiene configuraciones del sistema, software, hardware y usuarios.
- Acceso:
  ```bash
  regedit
  ```

### **Estructura clave**
1. **HKEY_CLASSES_ROOT**: Asociaciones de tipos de archivos.
2. **HKEY_CURRENT_USER**: Configuración del usuario actual.
3. **HKEY_LOCAL_MACHINE**: Configuración del sistema.
4. **HKEY_USERS**: Configuraciones de todos los usuarios.

### **Ejercicios relevantes**
- Cambiar el programa predeterminado para abrir archivos.
- Añadir opciones al menú contextual (ej. "Abrir en consola").

---

## **5. Programación de Tareas**
### **Comandos relevantes**
- Crear una tarea programada:  
  ```bash
  schtasks /create /tn "Tarea1" /tr "notepad.exe" /sc daily /st 19:00
  ```
- Eliminar una tarea programada:  
  ```bash
  schtasks /delete /tn "Tarea1"
  ```

---

## **6. Comandos Avanzados**
### **Usuarios y Grupos**
- Mostrar usuarios:  
  ```bash
  net user
  ```
- Mostrar grupos:  
  ```bash
  net localgroup
  ```
- Cambiar contraseña del usuario actual:  
  ```bash
  net user %username% *
  ```

### **Atributos de archivos**
- **Tipos de atributos**:
  - **R**: Solo lectura.
  - **H**: Oculto.
  - **S**: Sistema.
  - **A**: Archivo preparado para copia.
- **Gestión desde CMD**:
  - Agregar atributo:  
    ```bash
    attrib +R archivo.txt
    ```
  - Quitar atributo:  
    ```bash
    attrib -H archivo.txt
    ```

---

## **7. Resolución de Trayectorias**
### **Rutas absolutas y relativas**
1. **Ruta absoluta**:
   - Desde la raíz del sistema (ej.: `C:\Usuarios\Carpeta`).
2. **Ruta relativa**:
   - Desde el directorio actual (ej.: `..\Carpeta`).

### **Ejercicio práctico**
- Dado un esquema jerárquico, determinar rutas absolutas y relativas para llegar a diferentes directorios y archivos.

---

## **8. Ejercicios Clave**
### **Directorio y archivos**
1. Crear un directorio con 5 subdirectorios. Cada subdirectorio debe tener 2 subcarpetas.
2. Mover una carpeta de un directorio a otro y eliminarla después.
3. Crear un archivo de texto, agregarle contenido y moverlo entre carpetas.

### **Usuarios y grupos**
1. Crear dos usuarios: uno administrador y otro estándar.
2. Restringir horarios de acceso para un usuario.
3. Comprobar a qué grupos pertenece un usuario específico.

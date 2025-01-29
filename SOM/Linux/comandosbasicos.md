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

---


# **Operaciones Ficheros y Directorios en Linux - I**

### **1. ls (list)**

**Muestra información sobre ficheros y directorios.**  
Formato: `ls [opciones] [argumentos]`

1. Muestra el manual de usuario del comando `ls`.  
   Comando: `man ls`  
   ![imagen](https://github.com/user-attachments/assets/5eaf5a78-d03f-4ac6-ba94-8581dd852aeb)


2. Lista todos los archivos del directorio `bin` (con ruta absoluta).  
   Comando: `ls /bin`  
   ![imagen](https://github.com/user-attachments/assets/7aa4da13-c538-4fd9-a8bd-2a83f4fd97de)


3. Lista todos los archivos del directorio `bin` (con ruta relativa).  
   Comando: `ls bin`  
   ![imagen](https://github.com/user-attachments/assets/55b0e10b-e58f-4647-bde5-5b5959553be0)


4. Muestra todos los archivos del directorio `tmp`.  
   Comando: `ls /tmp`  
   ![imagen](https://github.com/user-attachments/assets/b730f48f-8aef-4c87-b28d-1cc653769750)


5. Lista todos los archivos, incluidos los ocultos, del directorio raíz.  
   Comando: `ls -a /`
   ![imagen](https://github.com/user-attachments/assets/d44b5119-3b07-4f5d-97f3-49bde8f53d1c)

   

7. Muestra el contenido del directorio `usr` y sus subdirectorios.  
   Comando: `ls -R /usr`  
   ![imagen](https://github.com/user-attachments/assets/15155867-d815-4bb1-aac9-a2eb675a1b96)


8. Lista todos los ficheros del directorio `home` mostrando su número de inodo.  
   Comando: `ls -i /home`  
   ![imagen](https://github.com/user-attachments/assets/a4f46da3-ae1c-46d9-bd40-131d2c624077)


---

### **2. pwd (print working directory)**

**Muestra la ruta absoluta del directorio actual donde nos encontramos.**  
Formato: `pwd`

8. Muestra el manual de usuario del comando `pwd`.  
   Comando: `man pwd`  
   ![imagen](https://github.com/user-attachments/assets/20d611c2-6804-4ee5-8bab-ccb84e01582c)


9. Muestra la ruta absoluta del directorio en el que te encuentras.  
   Comando: `pwd`  
   ![imagen](https://github.com/user-attachments/assets/6a9a9338-5820-4eed-9ca1-bfec38be0fde)


---

### **3. cd (change directory)**

**Cambia de directorio.**  
Formato: `cd [opciones] [directorio]`

10. Muévete al directorio raíz y comprueba que estás en él.  
    Comando:  
    ```
    cd /
    pwd
    ```  
    ![imagen](https://github.com/user-attachments/assets/164be448-03c1-4572-b810-e5c363fb566a)


11. Cambia al directorio `/etc/init.d`.  
    Comando: `cd /etc/init.d`  
    ![imagen](https://github.com/user-attachments/assets/2b9839f7-3fa4-4f8d-a597-b267a3871e24)


12. Muévete a tu directorio personal de usuario (recuerda que hay 2 formas de hacerlo).  
    Comandos:  
    ```
    cd ~
    cd /home/[nombre_usuario]
    ```  
    ![imagen](https://github.com/user-attachments/assets/33436887-00b0-4aef-9269-3b6629ff579b)


13. Sitúate en el directorio raíz (ruta absoluta).  
    Comando: `cd /`  
    ![imagen](https://github.com/user-attachments/assets/621fa13f-0649-4c52-b130-bebc36c7391f)

14. Sitúate en el directorio raíz (ruta relativa).  
    Comando: `cd ../..`  


---

### **4. mkdir (make directories)**

**Crea directorios.**  
Formato: `mkdir [opciones] [directorio/s]`

15. Crea el siguiente árbol de directorios. PRÁCTICA 2, estará situado en tu Escritorio de usuario.  
    Comandos:  
    ```
    mkdir -p ~/Escritorio/PRÁCTICA2/{PERSONAL/{MIS_PROGRAMAS,EXPEDIENTE},ESTUDIOS/2021/SOM,MISCELANEA/{TXT,JPG}}
    ```  
    ![imagen](https://github.com/user-attachments/assets/ac4c8c4b-1bb4-4d35-a719-f455fa3f8a0e)


---

### **16. Muestra el contenido de la carpeta PRÁCTICA2**
- Comando:  
  ```
  ls ~/Escritorio/PRÁCTICA2
  ```  
  ![imagen](https://github.com/user-attachments/assets/dcda252b-ba72-4a40-b1e2-f1ed83c7243e)



---

### **17. Muévete a la carpeta PERSONAL**
- Comando:  
  ```
  cd ~/Escritorio/PRÁCTICA2/PERSONAL
  ```  
  ![imagen](https://github.com/user-attachments/assets/7eb6a185-b724-4144-8ba3-d9184b5c45aa)



---

### **18. Muestra el contenido de la carpeta EXPEDIENTE sin cambiar de directorio activo**
- Comando:  
  ```
  ls ~/Escritorio/PRÁCTICA2/PERSONAL/EXPEDIENTE
  ```  
  ![imagen](https://github.com/user-attachments/assets/a3f8c2c2-4c27-4d28-9460-4ebb448772cc)



---

### **19. Sitúate en la carpeta ESTUDIOS utilizando únicamente un comando**
- Comando:  
  ```
  cd ~/Escritorio/PRÁCTICA2/ESTUDIOS
  ```  
  ![imagen](https://github.com/user-attachments/assets/4bb76609-f3b9-4b57-a9eb-7b5c07560aa6)



---

### **20. Comprueba que te encuentras en la carpeta ESTUDIOS**
- Comando:  
  ```
  pwd
  ```  
  ![imagen](https://github.com/user-attachments/assets/4ad72858-803b-42b8-b1a4-5306d6c66d2f)



---

### **21. Muestra el contenido de la carpeta ESTUDIOS**
- Comando:  
  ```
  ls
  ```  
  ![imagen](https://github.com/user-attachments/assets/de8499e0-b0d2-413b-b0c5-2ef051aae25c)



---

### **22. Muestra el contenido de la carpeta PRÁCTICA2 (sin moverte del directorio)**
- Comando:  
  ```
  ls ~/Escritorio/PRÁCTICA2
  ```  
  ![imagen](https://github.com/user-attachments/assets/2d946c1f-9470-40c9-96b1-c0d0b8c106bc)



---

### **23. Muestra el contenido de la carpeta PERSONAL (sin moverte del directorio)**
- Comando:  
  ```
  ls ~/Escritorio/PRÁCTICA2/PERSONAL
  ```  
  ![imagen](https://github.com/user-attachments/assets/b2b55521-5dc2-4b51-9fee-fa7f862872d1)


---

### **24. Muestra el contenido de la carpeta padre de donde estás (sin moverte del directorio)**
- Comando:  
  ```
  ls ..
  ```  
  ![imagen](https://github.com/user-attachments/assets/d4ee4407-c9f8-4ac0-b202-6978b0635d68)




---

### **25. Sitúate en la carpeta TXT. Utiliza únicamente un comando**
- Comando:  
  ```
  cd ~/Escritorio/PRÁCTICA2/MISCELANEA/TXT
  ```  
  ![imagen](https://github.com/user-attachments/assets/71dfaf61-6136-45b2-bef9-b2bd0ab5b8e5)


---

### **26. Muestra el contenido del directorio en el que te encuentras**
- Comando:  
  ```
  ls
  ```  
  ![imagen](https://github.com/user-attachments/assets/d620b0ea-516b-4e4b-9f73-cfad70aa422a)


---

### **27. Muestra el contenido del directorio en el que te encuentras en forma de lista**
- Comando:  
  ```
  ls -l
  ```  
  ![imagen](https://github.com/user-attachments/assets/14096aa3-d22b-4382-9c34-bb1cf2d4f46e)

---

### **28/01/25**

## **Operaciones Ficheros y Directorios en Linux - II**

---

### **1. Muestra la fecha y hora del sistema**
- Comando:  
  ```
  date
  ```

---

### **2. Cámbiate al directorio /etc**
- Comando:  
  ```
  cd /etc
  ```

---

### **3. Crea un directorio denominado SOM (¿Te deja?)**
- Comando:  
  ```
  su -
  mkdir /etc/SOM
  ```
Si, porque hemos iniciado como root al usar su -
---

### **4. Cámbiate al directorio /tmp**
- Comando:  
  ```
  cd /tmp
  ```

---

### **5. Crea el directorio TEMPORAL**
- Comando:  
  ```
  mkdir TEMPORAL
  ```

---

### **6. Muestra la ayuda que se da del comando SORT**
- Comando:  
  ```
  man sort
  ```

---

### **7. Comprobar que has cambiado de directorio**
- Comando:  
  ```
  pwd
  ```

---

### **8. Listar todos los ficheros del directorio TEMPORAL**
- Comando:  
  ```
  ls -l /tmp/TEMPORAL
  ```

---

### **9. Crear los directorios dir1, dir2 y dir3 en el directorio TEMPORAL**
- Comando:  
  ```
  mkdir /tmp/TEMPORAL/{dir1,dir2,dir3}
  ```

---

### **10. Dentro de dir1 crear el directorio dir11**
- Comando:  
  ```
  mkdir /tmp/TEMPORAL/dir1/dir11
  ```

---

### **11. Dentro del directorio dir3 crear el directorio dir31**
- Comando:  
  ```
  mkdir /tmp/TEMPORAL/dir3/dir31
  ```

---

### **12. Dentro del directorio dir31, crear los directorios dir311 y dir312**
- Comando:  
  ```
  mkdir /tmp/TEMPORAL/dir3/dir31/{dir311,dir312}
  ```

---

### **13. Sitúate en el directorio TEMPORAL**
- Comando:  
  ```
  cd /tmp/TEMPORAL
  ```

---

### **14. Elimina el directorio dir3 junto con su contenido**
- Comando:  
  ```
  rm -r /tmp/TEMPORAL/dir3
  ```

---

### **15. Crea un fichero llamado “SistemasLinux.txt” (que esté vacío) en el directorio dir11**
- Comando:  
  ```
  touch /tmp/TEMPORAL/dir1/dir11/SistemasLinux.txt
  ```

---

### **16. Crea un fichero llamado “Fich_Texto.txt” con el texto “Sistemas Operativos” en dir11**
- Comando:  
  ```
  echo "Sistemas Operativos" > /tmp/TEMPORAL/dir1/dir11/Fich_Texto.txt
  ```

---

### **17. Muestra el contenido del fichero por pantalla**
- Comando:  
  ```
  cat /tmp/TEMPORAL/dir1/dir11/Fich_Texto.txt
  ```

---

### **18. Elimina el fichero llamado “SistemasLinux.txt”**
- Comando:  
  ```
  rm /tmp/TEMPORAL/dir1/dir11/SistemasLinux.txt
  ```

---

### **29/01/25**

## **Operaciones Ficheros y Directorios en Linux - IV**

---

### **1. Crea la siguiente estructura de directorios dentro de tu directorio de trabajo personal con 5 comandos como máximo.**

#### **Estructura a crear:**
```
multimedia
├── musica
├── imagenes
├── video
├── presentaciones
│   ├── personales
│   ├── otras
```

#### **Comando para crear la estructura en un solo paso:**
```bash
mkdir -p ~/multimedia/{musica,imagenes,video,presentaciones/{personales,otras}}
```
![imagen](https://github.com/user-attachments/assets/2ef36a6e-2aa1-4c82-b3b2-0b6f218b8ca8)

---

### **2. Comprueba el resultado con `ls -R`**
- Comando:  
  ```bash
  ls -R ~/multimedia
  ```
  ![imagen](https://github.com/user-attachments/assets/3ef21f7b-bb7d-445d-8ba7-70dfd70b34af)

---

### **3. Crea un fichero vacío dentro del directorio música, con nombre `MI_MUSICA.txt`**
- Comando:  
  ```bash
  touch ~/multimedia/musica/MI_MUSICA.txt
  ```
  ![imagen](https://github.com/user-attachments/assets/264b13ae-399e-41f2-966e-3e6ec1180fd7)

---

### **4. Utiliza tu editor preferido para abrir el fichero `MI_MUSICA.txt` e introduce tus grupos o los estilos de música que más te gusten. Guarda los cambios y sal.**
- Con `nano`:  
  ```bash
  nano ~/multimedia/musica/MI_MUSICA.txt
  ```
- Con `vim`:  
  ```bash
  vim ~/multimedia/musica/MI_MUSICA.txt
  ```
- Con `echo` (para añadir texto directamente desde la terminal):  
  ```bash
  echo "KPop, Japanese Pop" > ~/multimedia/musica/MI_MUSICA.txt
  ```
Mi favorito es nano, pero para algo tan simple prefiero usar echo:
![imagen](https://github.com/user-attachments/assets/a18b157d-ac54-4905-94d5-e2c41ee592a6)

---

### **5. ¿Conoces más formas de editar con comandos Linux? Inclúyelas.**
- **Usando `cat` (para escribir manualmente el contenido, finalizar con `Ctrl+D`):**  
  ```bash
  cat > ~/multimedia/musica/MI_MUSICA.txt
  ```
  ![imagen](https://github.com/user-attachments/assets/6ce7b804-24c3-48cf-afd2-f1ea96b3152b)

- **Usando `sed` (para añadir una línea específica de texto):**  
  ```bash
  sed -i '1s/^/KPop, Japanese Pop\n/' ~/multimedia/musica/MI_MUSICA.txt
  ```
  ![imagen](https://github.com/user-attachments/assets/b35fb69a-e6e6-40ea-8717-a7b586623722)

- **Usando `printf` (para escribir múltiples líneas en el archivo):**  
  ```bash
  printf "KPop\nJapanese pop\nNada mas :b este es el ejemplo de printf\n" >> ~/multimedia/musica/MI_MUSICA.txt
  ```
  ![imagen](https://github.com/user-attachments/assets/98f20880-a5c9-42d2-ba8e-463246518921)

---

### **6. Muestra en el terminal todo el contenido de `MI_MUSICA.txt`**
- Comando:  
  ```bash
  cat ~/multimedia/musica/MI_MUSICA.txt
  ```
  ![imagen](https://github.com/user-attachments/assets/8d92c4c8-10a6-4b2f-ac55-bb850bf0b0f8)

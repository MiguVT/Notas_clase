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

---

### **30/01/25**

## **Operaciones Ficheros y Directorios en Linux - V**

### **1. Crea `Princip`, `Datos` y `C` desde el directorio `Origen`**
- Comando:  
  ```bash
  mkdir -p ~/Origen/{Princip,Datos,C}
  ```
  ![imagen](https://github.com/user-attachments/assets/213df834-8aaf-4633-b8c2-3ca190be1f8f)

---

### **2. Cambia al directorio `Princip` y crea desde ahí el directorio `Result` con trayectoria relativa**
- Comandos:  
  ```bash
  cd ~/Origen/Princip
  mkdir ../Result
  ```
  ![imagen](https://github.com/user-attachments/assets/a809b2e4-43d7-40e4-bacf-146d3d0333f9)

---

### **3. Utilizando trayectoria absoluta, crea los directorios `Programa` y `Ejercici`**
- Comando:  
  ```bash
  mkdir -p ~/Origen/C/{Programa,Ejercici}
  ```
  ![imagen](https://github.com/user-attachments/assets/1909dbac-401b-4a9a-bfc1-0c1c82a20801)

---

### **4. Cambia al directorio `Ejercici` y desde ahí, con trayectoria relativa, crea `Nuevos` y `Revisado`**
- Comandos:  
  ```bash
  cd ~/Origen/C/Ejercici
  mkdir Nuevos Revisado
  ls -R ~/Origen
  ```
  ![imagen](https://github.com/user-attachments/assets/cb43ac8b-0d40-4096-a628-f978c008b78a)

---

### **5. Visualiza el contenido del directorio `C`**
- Comando:  
  ```bash
  ls -R ~/Origen/C
  ```
  ![imagen](https://github.com/user-attachments/assets/e6fa7154-f202-4e31-93fa-c120a515083d)

---

### **6. Borra `Ejercici` (y todo su contenido) utilizando la trayectoria absoluta**
- Comando:  
  ```bash
  rm -r ~/Origen/C/Ejercici
  ```
  ![imagen](https://github.com/user-attachments/assets/728101ff-04ab-4267-bdd5-3f1880945c49)

---

### **7. Crea dentro del directorio `Result`, los directorios `c.dat` y `c.bak`**
- Comando:  
  ```bash
  mkdir ~/Origen/Result/{c.dat,c.bak}
  ```
  ![imagen](https://github.com/user-attachments/assets/fb89fd30-393a-4935-a008-2697140d1a21)

---

### **8. Crea en tu directorio personal dos directorios nuevos llamados `árbol1` y `árbol2`**
- Comando:  
  ```bash
  mkdir -p ~/árbol1 ~/árbol2
  ```
  ![imagen](https://github.com/user-attachments/assets/103ecfaf-b170-4979-bdbc-e9338764a009)

#### **A. Copia en `árbol1` la estructura de directorios de `Origen`**
- Comando:  
  ```bash
  cp -r ~/Origen ~/árbol1/
  ```
  ![imagen](https://github.com/user-attachments/assets/49496c20-15f0-47d7-bbfb-faae2a0712ba)

#### **B. Copia en `árbol2` la estructura de directorios de `C`**
- Comando:  
  ```bash
  cp -r ~/Origen/C ~/árbol2/
  ```
  ![imagen](https://github.com/user-attachments/assets/b4898332-0c92-4571-b560-c4e353815065)

---

### **9. Borra los directorios `árbol1` paso a paso y `árbol2` con una sola instrucción**

#### **A. Borrar `árbol1` paso a paso**
- Comandos:  
  ```bash
  rm -r ~/árbol1/Origen/Result/c.dat
  rm -r ~/árbol1/Origen/Result/c.bak
  rm -r ~/árbol1/Origen/Result
  rm -r ~/árbol1/Origen/C/Programa
  rm -r ~/árbol1/Origen/C
  rm -r ~/árbol1/Origen/Princip
  rm -r ~/árbol1/Origen/Datos
  rm -r ~/árbol1/Origen
  rmdir ~/árbol1
  ```
  ![imagen](https://github.com/user-attachments/assets/d57e4550-8c7e-458c-9bdb-43239e409dd8)

#### **B. Borrar `árbol2` con una sola instrucción**
- Comando:  
  ```bash
  rm -r ~/árbol2
  ```
  ![imagen](https://github.com/user-attachments/assets/c8a476ad-1e65-4fd1-a0e3-c1dd99515319)

---

### **10. Mueve los directorios `c.dat` y `c.bak` del directorio `Result` al directorio `Datos`**
- Comando:  
  ```bash
  mv ~/Origen/Result/{c.dat,c.bak} ~/Origen/Datos/
  ```
  ![imagen](https://github.com/user-attachments/assets/27970c57-d0fc-4d9e-a97d-a11f789d42c3)

---

### **11. Copia el directorio `Programa` al directorio `Result`**
- Comando:  
  ```bash
  cp -r ~/Origen/C/Programa ~/Origen/Result/
  ```
  ![imagen](https://github.com/user-attachments/assets/8210af45-c74c-4ac7-b4a8-7963cf3573d1)

---

### **12. Cambia el nombre de `Result` por `Final`**
- Comando:  
  ```bash
  mv ~/Origen/Result ~/Origen/Final
  ```
  ![imagen](https://github.com/user-attachments/assets/116fca2e-31b1-4e6e-92dd-08f8ee2be4ae)

---

### **13. Copia la estructura del directorio `C` en `Final`**
- Comando:  
  ```bash
  cp -r ~/Origen/C ~/Origen/Final/
  ```
  ![imagen](https://github.com/user-attachments/assets/3519f26d-e80d-49e5-a9dd-efe16f55ddda)

---

### **14. Muestra los permisos de todos los directorios de la estructura**
- Comando:  
  ```bash
  ls -lR ~/Origen
  ```
  ![imagen](https://github.com/user-attachments/assets/97c4d335-2a06-46c2-b183-696a6ed93a53)

### **04/02/25**

## EJERCICIO DE METACARACTERES

### * ANTES DE EMPEZAR: DESCARGAR ARCHIVO
- Para descargar el archivo he abierto un server http en el host donde esta el archivo deseado (`Metacaracteres.zip`)
  ![imagen](https://github.com/user-attachments/assets/0098e956-d27a-4d8c-9265-bd4610431f58)
- Lo he descargando usando en linux el comando wget (Haciendo un `GET` a `/Metacaracteres.zip`), pero antes he comprabado con ping que la vm tenga acceso al servidor del host, despues lo movi a `~/Metacaracteres` y lo descomprimí en este directorio
  ![imagen](https://github.com/user-attachments/assets/ce59103a-3e53-4db4-87fc-1bdba3d9a06a)
  
---

### **1. Mostrar ficheros cuyos nombres comiencen por "fichero" y tengan un solo carácter adicional**  
- Comando:  
  ```bash
  ls fichero?
  ```  
  **Explicación**: Se listan los archivos que comienzan con `"fichero"` y tienen **un carácter más** después.
  ![imagen](https://github.com/user-attachments/assets/93fb12d6-04a5-42fd-b847-ab97f8850f62)



---

### **2. Mostrar ficheros cuyos nombres comiencen por "fichero" y tengan exactamente dos caracteres adicionales**  
- Comando:  
  ```bash
  ls fichero??
  ```  
  **Explicación**: Se listan archivos con exactamente **dos caracteres** después de `"fichero"`.
  ![imagen](https://github.com/user-attachments/assets/a48e38e8-6f98-4ce4-8301-4f80574c0fbe)


---

### **3. Mostrar ficheros que empiecen por "ficheroPDF", seguido de un carácter cualquiera y terminen en ".pdf"**  
- Comando:  
  ```bash
  ls ficheroPDF?.pdf
  ```  
  **Explicación**: Se buscan archivos PDF con nombres como `"ficheroPDF1.pdf"`, `"ficheroPDFA.pdf"`, etc.
  ![imagen](https://github.com/user-attachments/assets/7fc07dcf-d7d5-4c11-b8af-090edf49e1f6)


---

### **4. Mostrar ficheros cuyos nombres empiecen por "archivo" y tengan exactamente 11 caracteres**  
- Comando:  
  ```bash
  ls archivo????
  ```  
  **Explicación**: Se muestran archivos cuyo nombre tenga **4 caracteres más** después de `"archivo"`,.
  ![imagen](https://github.com/user-attachments/assets/5cd0a5b7-47a4-4782-a319-48ca28b04875)

---

### **5. Mostrar ficheros cuyos nombres tengan exactamente 15 caracteres**  
- Comando:  
  ```bash
  ls ???????????????
  ```  
  **Explicación**: Se filtran archivos con **15 caracteres en total**, sin importar su nombre.
  ![imagen](https://github.com/user-attachments/assets/14db11cb-f3bb-4796-bfd9-3fe44a249769)

---

### **6. Mostrar ficheros cuyos nombres comiencen por "archivo"**  
- Comando:  
  ```bash
  ls archivo*
  ```  
  **Explicación**: Se listan **todos los archivos** que comiencen por `"archivo"`, sin importar qué caracteres sigan.
  ![imagen](https://github.com/user-attachments/assets/404cfd41-db08-49c7-a8b4-677b7f7ce9af)

---

### **7. Mostrar ficheros cuya extensión sea ".jpeg"**  
- Comando:  
  ```bash
  ls *.jpeg
  ```  
  **Explicación**: Se listan todos los archivos que terminan en `".jpeg"`.
  ![imagen](https://github.com/user-attachments/assets/777f6f7d-5b96-4d8f-8945-29a9fe217a0b)

---

### **8. Mostrar todos los ficheros cuyos nombres empiecen por "imagen", después tengan una letra y terminen en ".jpeg"**  
- Comando:  
  ```bash
  ls imagen[A-Za-z].jpeg
  ```  
  **Explicación**: Se listan imágenes como `"imagenA.jpeg"`, `"imagenB.jpeg"`, etc. (Tiene que ser mayuscula o `[A-Za-z]`)
  ![imagen](https://github.com/user-attachments/assets/6d71baf7-cb98-4fbb-9887-acbcc2b31ce9)
  

---

### **9. Mostrar ficheros que contengan la cadena "Exámenes" en el nombre**  
- Comando:  
  ```bash
  ls *Exámenes*
  ```  
  **Explicación**: Se buscan archivos con `"Exámenes"` en cualquier parte del nombre. Al ser sensible a mayusculas y tildes, no encontrará ningun resultado.
  
  ![imagen](https://github.com/user-attachments/assets/396ba431-1675-4aee-b1b2-10742e060703)

---

### **10. Mostrar todos los ficheros cuyos nombres comiencen por "fichero" y estén seguidos por un número del 4 al 9**  
- Comando:  
  ```bash
  ls fichero[4-9]*
  ```  
  **Explicación**: Se listan archivos como `"fichero4"`, `"fichero5"`, hasta `"fichero9"`.
  ![imagen](https://github.com/user-attachments/assets/3ce84db2-1f29-479f-80fa-fef900ab28ab)

---

## **Parte II - Organización de Archivos con Metacaracteres**

### **11. Crear una carpeta llamada "carpetaTXT" en el directorio personal**  
- Comando:  
  ```bash
  mkdir ~/carpetaTXT
  ```
  ![imagen](https://github.com/user-attachments/assets/4d76d3a0-9a9e-4569-970d-d5bdffb7b293)

---

### **12. Crear una carpeta llamada "carpetaPDF"**  
- Comando:  
  ```bash
  mkdir ~/carpetaPDF
  ```
  ![imagen](https://github.com/user-attachments/assets/8db034ed-bfb4-4320-8140-ab3ec04a0c10)

---

### **13. Crear una carpeta llamada "carpetaJPEG"**  
- Comando:  
  ```bash
  mkdir ~/carpetaJPEG
  ```
  ![imagen](https://github.com/user-attachments/assets/c594b935-dd0c-4dcd-9fe5-2228b8b69684)


---

### **14. Mover todos los archivos ".txt" a la carpeta "carpetaTXT"**  
- Comando:  
  ```bash
  mv *.txt ~/carpetaTXT/
  ```  
  **Explicación**: Se trasladan **todos los archivos de texto** a la carpeta `"carpetaTXT"`.
  ![imagen](https://github.com/user-attachments/assets/39c00c29-3276-46c6-823d-3d7fc6db12c4)

---

### **15. Mover todos los archivos ".pdf" a la carpeta "carpetaPDF"**  
- Comando:  
  ```bash
  mv *.pdf ~/carpetaPDF/
  ```  
  **Explicación**: Se trasladan **todos los archivos PDF** a `"carpetaPDF"`.
  ![imagen](https://github.com/user-attachments/assets/00f98a90-9260-4cdb-a5ac-c75b2a78b94f)

---

### **16. Mover todos los archivos ".jpeg" a la carpeta "carpetaJPEG"**  
- Comando:  
  ```bash
  mv *.jpeg ~/carpetaJPEG/
  ```  
  **Explicación**: Se trasladan **todas las imágenes JPEG** a `"carpetaJPEG"`.
  ![imagen](https://github.com/user-attachments/assets/b895d221-1c86-464b-9ceb-a6888f1b6e5e)

---

### **17. Mover todos los archivos que comiencen por "JAVIER" a una carpeta "personal_JAVIER"**  
- Comando:  
  ```bash
  mv JAVIER* ~/personal_JAVIER/
  ```  
  **Explicación**: Se trasladan archivos como `"JAVIER1"`, `"JAVIER2"`, etc. Como no existe la carpeta, la creamos con `mkdir`.
  ![imagen](https://github.com/user-attachments/assets/4c5d97a0-dd4e-4900-ba00-d915a4cc7b87)
  ![imagen](https://github.com/user-attachments/assets/375b78b4-f496-4559-85d2-3526e1a589a7)

---

### **18. Mover todos los ficheros que tengan una extensión a la carpeta "conExtension"**  
- Comando:  
  ```bash
  mv *.* ~/conExtension/
  ```  
  **Explicación**: Se mueven **todos los archivos que tienen un punto (`.`) en su nombre**, es decir, archivos con extensión (`.txt`, `.pdf`, `.jpeg`...). Como no existe la carpeta, la creamos con `mkdir`.
  
  ![imagen](https://github.com/user-attachments/assets/b2190374-6c19-421d-b073-ebb2b2388915)

---

### **19. Mostrar los archivos que quedaron en la carpeta "METACARACTERES"**  
- Comando:  
  ```bash
  ls ~/METACARACTERES
  ```  
  **Explicación**: Se listan los archivos que **no fueron movidos a otras carpetas**. Como es sensible a mayusculas, no lo detectará, para ello he corregido el comando.
  ![imagen](https://github.com/user-attachments/assets/2b9abed0-ab27-460d-815f-26d8fb98f620)

---

### 06/02/25

## **Ejercicios II - Metacaracteres**  

---

### **Actividad 1: Completar la tabla sobre metacaracteres**  

| **Expresión** | **Referencia a ficheros y directorios que...** |
|--------------|--------------------------------------|
| `*[ab]*` | Contengan la letra `a` o `b` en cualquier parte del nombre. |
| `texto1[1-4]` | Empiecen con `texto1` y el siguiente carácter sea un número entre `1` y `4`. |
| `le[ae]me` | Empiecen con `le`, seguido de `a` o `e`, y terminen en `me`. |
| `[!0-9]*` | No empiecen con un número (`0-9`). |

---

### **Actividad 2: Lista todos los archivos del directorio `/etc` que empiecen por `t` en orden inverso**  

- **Comando:**  
  ```bash
  ls -r /etc/t*
  ```

---

### **Actividad 3: Lista todos los archivos del directorio `/dev` que empiecen por `tty` y tengan exactamente 5 caracteres**  

- **Comando:**  
  ```bash
  ls /dev/tty??
  ```

---

### **Actividad 4: Lista todos los archivos del directorio `/dev` que empiecen por `tty` y terminen en `1`, `2`, `3` o `4`**  

- **Comando:**  
  ```bash
  ls /dev/tty*[1-4]
  ```

---

### **Actividad 5: Lista todos los archivos del directorio `/dev` que empiecen por `t` y terminen en `C1`**  

- **Comando:**  
  ```bash
  ls /dev/t*C1
  ```

---

### **Actividad 6: Lista todos los archivos del directorio `/etc` que no empiecen por `t`**  

- **Comando:**  
  ```bash
  ls /etc/[^t]*
  ```

---

### **12/02/25**  

## **Ejercicios I - Comando `grep`**  

Antes de empezar la práctica, es necesario descargar y preparar los archivos necesarios. Como no me resulta muy dificil, hare un tutorial para cualquier persona que no tenga conocimiento, lo tratare de hacer lo mas sencillo posible.

---

### **📌 Descarga del archivo en la máquina virtual**  

Para obtener los archivos desde el host Windows, podemos iniciar un **servidor HTTP temporal** en la carpeta donde se encuentra el archivo `ficherosGrep.zip`.  

1️⃣ **Iniciar servidor HTTP en Windows**  
En la terminal de Windows (`cmd` o `PowerShell`), dirigirse a la carpeta donde está el archivo y ejecutar:  
```powershell
python -m http.server 8080
```
Esto iniciará un servidor web en el puerto **8080**.

2️⃣ **Descargar el archivo en Linux**  
Desde la máquina Linux, abrir la terminal y ejecutar:  
```bash
wget http://<IP_DEL_HOST>:8080/ficherosGrep.zip
```
⚠️ **Reemplaza `<IP_DEL_HOST>` con la IP del equipo Windows en la red local**. Puedes obtener esta IP con:  
```powershell
ipconfig
```
En mi caso es la 192.168.5.13

Luego, descomprimir el archivo en el directorio personal:  
```bash
unzip ficherosGrep.zip -d ~/PATRONES
```

✅ **Archivos preparados en `~/PATRONES`**  
![imagen](https://github.com/user-attachments/assets/a53c6127-18aa-41f6-ac3c-84dd2b1d6d52)

---

### **Ejercicios `grep`**  

#### 📂 **Sobre el archivo `comprimirDescomprimir.md`**  

### **1. Obtén las líneas que empiezan por `#` en el fichero.**  
- Comando:  
  ```bash
  grep '^#' ~/PATRONES/comprimirDescomprimir.md
  ```
  ![imagen](https://github.com/user-attachments/assets/fdc49ce7-0cb7-43d3-8469-2a9ce6af8d92)

---

### **2. Obtén solo las líneas que comiencen por `#`, pero excluyendo `##`**  
- Comando:  
  ```bash
  grep '^#[^#]' ~/PATRONES/comprimirDescomprimir.md
  ```
  ![imagen](https://github.com/user-attachments/assets/95e687a4-5b35-43bc-b5e7-2e28545033ac)

---

### **3. Muestra solo las líneas que comiencen con el comando `tar`.**  
- Comando:  
  ```bash
  grep '^tar' ~/PATRONES/comprimirDescomprimir.md
  ```
  ![imagen](https://github.com/user-attachments/assets/a82e1768-600e-45bb-880c-925637b63aca)

---

#### 📂 **Sobre el archivo `gestionUsuarios.md`**  

### **4. Muestra los comandos ejecutados como `sudo` (que comienzan por `sudo`).**  
- Comando:  
  ```bash
  grep '^sudo' ~/PATRONES/gestionUsuarios.md
  ```
  ![imagen](https://github.com/user-attachments/assets/f3b0ac96-5d2b-4ee9-b156-97696a5acb93)


---

### **5. Busca todas las líneas que contengan palabras remarcadas con `*` (ejemplo: `*palabra*`).**  
- Comando:  
  ```bash
  grep '\*.*\*' ~/PATRONES/gestionUsuarios.md
  ```
  ![imagen](https://github.com/user-attachments/assets/1ec95975-32dd-42c1-a0ba-8f044e0204e3)


---

### **6. Devuelve todas las líneas que contengan la palabra `grupo`.**  
- Comando:  
  ```bash
  grep 'grupo' ~/PATRONES/gestionUsuarios.md
  ```
  ![imagen](https://github.com/user-attachments/assets/37987dc4-72ae-4569-8106-324b6413c93a)

---

### **7. Devuelve todas las líneas que terminen en dos puntos (`:`).**  
- Comando:  
  ```bash
  grep ':$' ~/PATRONES/gestionUsuarios.md
  ```
  ![imagen](https://github.com/user-attachments/assets/01303217-bc35-4bee-9fae-60c8706fdfe9)

---

### **8. Devuelve todas las líneas que contengan la palabra `bash`.**  
- Comando:  
  ```bash
  grep 'bash' ~/PATRONES/gestionUsuarios.md
  ```
  ![imagen](https://github.com/user-attachments/assets/5778c26f-fa51-4988-aac0-6f284943c2b8)

---

#### 📂 **Sobre todos los archivos (`*.md`)**  

### **9. Devuelve todas las líneas que comiencen con `#`.**  
- Comando:  
  ```bash
  grep '^#' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/520b8343-75ac-4c8b-9271-dd19708ed6aa)

---

### **10. Devuelve todas las líneas que comiencen con `##`.**  
- Comando:  
  ```bash
  grep '^##' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/d9b5eba9-c3e4-434c-badd-83ae0a1394d9)

---

### **11. Devuelve todas las líneas que comiencen con `###`.**  
- Comando:  
  ```bash
  grep '^###' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/3c6ec824-0639-4a02-b268-21dcffb308f1)

---

### **12. ¿Qué archivos contienen una sección llamada `Referencias`?**  
- Comando:  
  ```bash
  grep -l 'Referencias' ~/PATRONES/*.md
  ```
  ✅ **El parámetro `-l` solo muestra el nombre del archivo, sin el contenido.**  
  ![imagen](https://github.com/user-attachments/assets/a988975d-4a8d-4585-b831-26985fb2c431)

---

### **13. Devuelve todas las líneas que comiencen por `N`, `P` o `S`.**  
- Comando:  
  ```bash
  grep '^[NPS]' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/88edc708-ed59-4d2a-82f1-03bf6733735a)

---

### **14. Devuelve todas las líneas que terminen en `t`, `s` o `n`.**  
- Comando:  
  ```bash
  grep '[tsn]$' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/21d288d2-7ec8-4247-9f5f-e61f7238f449)

---

### **15. Devuelve todas las líneas que terminen en mayúscula.**  
- Comando:  
  ```bash
  grep '[A-Z]$' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/7e709d19-c59b-4c0e-af92-0ea2889bb9cd)

---

### **16. Devuelve todas las líneas que comiencen en mayúscula.**  
- Comando:  
  ```bash
  grep '^[A-Z]' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/243cdad2-9842-4b20-baa2-eee5e40d9c8f)
  ![imagen](https://github.com/user-attachments/assets/23c4d5b5-7b10-4ad7-ad16-a678d0cfb44a)

---

### **17. Devuelve todas las líneas que comiencen en mayúscula y terminen en minúscula.**  
- Comando:  
  ```bash
  grep '^[A-Z].*[a-z]$' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/c696047a-898d-447c-a34e-4433be224874)

---

### **18. Devuelve todas las líneas que pertenezcan a una enumeración (empiezan por un número).**  
- Comando:  
  ```bash
  grep '^[0-9]' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/9007447e-a765-44d0-a9fe-3881dd1322de)

---

### **19. Devuelve todas las líneas que formen parte de una lista no numerada (`-`).**  
- Comando:  
  ```bash
  grep '^- ' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/c36b8bc0-1319-4109-aebe-16e3c5c5e61c)

---

### **20. ¿En qué archivos aparece la palabra `autoclean`?**  
- Comando:  
  ```bash
  grep -l 'autoclean' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/11ff6f95-e63c-47b8-a821-a633f167b39f)

---

### **21. ¿En qué archivos aparece la ruta `/etc/passwd`?**  
- Comando:  
  ```bash
  grep -l '/etc/passwd' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/2d6a3359-e496-4292-8a84-a0220f8a1dce)

---

### **22. Devuelve todas las líneas que comiencen en mayúscula, contengan la palabra `para` y terminen en punto.**  
- Comando:  
  ```bash
  grep '^[A-Z].*para.*\.$' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/84e0e6d8-1783-4c78-b20d-b432b44678d0)

---

### **23. Devuelve todas las líneas que comiencen en mayúscula, contengan la palabra `para` y terminen en `.` o `:`.**  
- Comando:  
  ```bash
  grep '^[A-Z].*para.*[.:]$' ~/PATRONES/*.md
  ```
  ![imagen](https://github.com/user-attachments/assets/b951f18f-4f09-4ca8-a55f-2c09752afe5f)

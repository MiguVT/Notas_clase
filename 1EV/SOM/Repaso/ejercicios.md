# Cuaderno SOM - Ejercicios Repaso

## RUTAS

### 1.- Teniendo en cuenta que la unidad activa es la referente al disco duro, C:, y el directorio en el que estamos es Docs
- ¿Cuál es la trayectoria en la que se encuentra el archivo doc1.txt?
	- .\doc1.txt
- Indica las trayectorias absolutas para tema1.doc y fichero.txt
	- C:\Princip\Apuntes\Sistemas\tema1.doc
	- C:\Princip\fichero.txt
- Indica las trayectorias relativas para los 2 ficheros anteriores (recuerda el
directorio activo)
	- <div>..\fichero.txt</div>
	- <div>..\Apuntes\Sistemas\tema1.txt</div>

### 2.- Partiendo de Sistemas, indica la ruta absoluta y relativa para el directorio Excel.
- <div>Relativa: ..\..\Docs\Excel</div>
- <div>Absoluta: C:\Princip\Docs\Excel</div>

### 3. – Crea los directorios y archivos en modo comando. Muestra su estructura final en modo árbol.
```
C:\Borrar>tree
Listado de rutas de carpetas
El número de serie del volumen es 9CF4-DB86
C:.
└───Princip
    ├───Apuntes
    │   └───Sistemas
    ├───Docs
    │   ├───Excel
    │   └───Word
    └───Programa
```

## REPASO

### **Ejercicios CMD – Usuarios & Grupos**

1. **Crear un usuario llamado "user1" con contraseña "pass123":**
   ```cmd
   net user user1 pass123 /add
   ```

2. **Eliminar el usuario "user1":**
   ```cmd
   net user user1 /delete
   ```

3. **Cambiar la contraseña del usuario actual:**
   ```cmd
   net user %username% *
   ```

4. **Mostrar información del usuario "Administrador":**
   ```cmd
   net user Administrador
   ```

5. **Crear un nuevo grupo llamado "Grupo1":**
   ```cmd
   net localgroup Grupo1 /add
   ```

6. **Eliminar el grupo "Grupo1":**
   ```cmd
   net localgroup Grupo1 /delete
   ```

7. **Agregar el usuario "user1" al grupo "Grupo1":**
   ```cmd
   net localgroup Grupo1 user1 /add
   ```

8. **Eliminar el usuario "user1" del grupo "Grupo1":**
   ```cmd
   net localgroup Grupo1 user1 /delete
   ```

9. **Mostrar los miembros del grupo "Administradores":**
   ```cmd
   net localgroup Administradores
   ```

10. **Cambiar el nombre del usuario "user1" a "usuario1":**
    ```cmd
    wmic useraccount where name='user1' rename usuario1
    ```

11. **Crear un nuevo usuario llamado "user2" con contraseña "pass456":**
    ```cmd
    net user user2 pass456 /add
    ```

12. **Crear un nuevo grupo llamado "Grupo2":**
    ```cmd
    net localgroup Grupo2 /add
    ```

13. **Agregar el usuario "user2" al grupo "Grupo2":**
    ```cmd
    net localgroup Grupo2 user2 /add
    ```

14. **Mostrar todos los usuarios del sistema:**
    ```cmd
    net user
    ```

15. **Mostrar todos los grupos del sistema:**
    ```cmd
    net localgroup
    ```

16. **Cambiar la contraseña del usuario "user2":**
    ```cmd
    net user user2 *
    ```

17. **Mostrar la fecha de expiración de la cuenta del usuario "Administrador":**
    ```cmd
    net user Administrador
    ```

18. **Desactivar la cuenta del usuario "user2":**
    ```cmd
    net user user2 /active:no
    ```

19. **Mostrar los grupos a los que pertenece el usuario "Administrador":**
    ```cmd
    whoami /groups
    ```

---

### **Ejercicios CMD – Archivos & Directorios**

1. **Crea un directorio llamado "Ejercicios_CMD":**
   ```cmd
   mkdir Ejercicios_CMD
   ```

2. **Entra en ese directorio:**
   ```cmd
   cd Ejercicios_CMD
   ```

3. **Crea tres subdirectorios dentro de "Ejercicios_CMD" llamados "Directorio1", "Directorio2" y "Directorio3":**
   ```cmd
   mkdir Directorio1 Directorio2 Directorio3
   ```

4. **Muestra el contenido del directorio actual:**
   ```cmd
   dir
   ```

5. **Repite la creación de los directorios en caso de errores o nueva estructura:**
   - **Crear el directorio principal:**
     ```cmd
     mkdir Ejercicios_CMD
     ```
   - **Entrar:**
     ```cmd
     cd Ejercicios_CMD
     ```
   - **Crear los subdirectorios:**
     ```cmd
     mkdir Directorio1 Directorio2 Directorio3
     ```
   - **Mostrar el contenido:**
     ```cmd
     dir
     ```

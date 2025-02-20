**Manual Rápido de Diskpart**

**¿Qué es Diskpart?**
Diskpart es una herramienta de Windows que sirve para gestionar discos y particiones. Con ella podemos ver, crear, eliminar y cambiar discos y particiones fácilmente desde la línea de comandos.

**Comandos Básicos de Diskpart**

1. **Ver los discos disponibles:**
   - Escribe `list disk` y presiona **Enter**.
   - Te mostrará una lista de discos conectados.

2. **Seleccionar un disco:**
   - Escribe `select disk X` (reemplaza X por el número del disco que quieres usar) y presiona **Enter**.
   - Esto hará que trabajemos con ese disco.

3. **Ver las particiones de un disco:**
   - Escribe `list partition` y presiona **Enter**.
   - Aparecerán todas las particiones de ese disco.

4. **Seleccionar una partición:**
   - Escribe `select partition X` (reemplaza X por el número de la partición) y presiona **Enter**.

5. **Eliminar una partición:**
   - Primero, selecciona la partición.
   - Luego, escribe `delete partition` y presiona **Enter**.
   - Si es una partición protegida, usa `delete partition override`.

6. **Crear una partición nueva:**
   - Escribe `create partition primary` y presiona **Enter**.
   - Esto creará una nueva partición en el disco seleccionado.

7. **Formatear una partición:**
   - Primero, selecciona la partición.
   - Luego, escribe `format fs=ntfs quick` y presiona **Enter**.
   - Esto la formateará en NTFS rápidamente. Si quieres en FAT32, cambia `ntfs` por `fat32`.

8. **Asignar una letra a una partición:**
   - Primero, selecciona la partición.
   - Luego, escribe `assign letter=X` (cambia X por la letra que quieras) y presiona **Enter**.

9. **Salir de Diskpart:**
   - Escribe `exit` y presiona **Enter**.

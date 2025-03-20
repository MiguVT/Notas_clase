![imagen](https://github.com/user-attachments/assets/9567b4f1-e396-412b-81a7-e93b58dc1c6f)# **Gestión de Procesos en GNU/Linux**

## **1. ¿Qué es el PID de un proceso en GNU/Linux?**  
El **PID (Process ID)** es un número único que el sistema operativo asigna a cada proceso en ejecución. Sirve para identificar y gestionar procesos dentro del sistema.

---

## **2. ¿Qué diferencia hay entre la opción `-a` y la opción `-x` de la orden `ps`?**  
- **`ps -a`**: Muestra los procesos de todos los usuarios en el sistema que tienen terminal asociado.  
- **`ps -x`**: Muestra los procesos que no están asociados a una terminal, como daemons o procesos en segundo plano.

---

## **3. Mostrar todos los procesos del sistema y visualizar el árbol jerárquico**  

Para listar todos los procesos del sistema:  
```bash
ps aux
```
![imagen](https://github.com/user-attachments/assets/2f730ff6-cca4-465b-af92-0555cc03253d)

Para mostrar un árbol jerárquico con la ruta del programa:  
```bash
pstree -p
```
![imagen](https://github.com/user-attachments/assets/939af8f0-ac6b-41f7-b796-ca37c334d048)

---

## **4. Filtrar los procesos de `ps` para obtener únicamente los pertenecientes a `bash`**  
```bash
ps -aux | grep bash
```
![imagen](https://github.com/user-attachments/assets/18a3a6fc-f199-46c7-9336-3bf61f90101d)


O también:  
```bash
pgrep -l bash
```
![imagen](https://github.com/user-attachments/assets/72b33ce3-0efd-406e-b03c-d62d4f8adb4e)

---

## **5. Diferencias entre `top` y `ps`**  
| Comando | Descripción |
|---------|-------------|
| `top` | Muestra una lista dinámica de procesos en tiempo real. Permite monitorear el uso de CPU, memoria y otras métricas. |
| `ps` | Muestra una instantánea estática de los procesos en el momento en que se ejecuta el comando. |

---

## **6. Uso del comando `top` para realizar las siguientes tareas:**  

1. **Realizar un muestreo cada 5 segundos:**  
   ```bash
   top -d 5
   ```
   ![imagen](https://github.com/user-attachments/assets/b987d18b-1100-4568-acf3-bae9a4e82d0b)

2. **Ordenar los procesos por tiempo de CPU:**  
   Dentro de `top`, presiona la tecla `P`.  
   ![imagen](https://github.com/user-attachments/assets/ccb9d968-d626-4ed9-8ea7-8f343af89590)

3. **Mostrar solo los procesos del usuario actual:**
   Voy a usar whoami permitiendo que sea ejecutando en cualquier sistema sin que el usuario necesite ser som113
   ```bash
   top -u $(whoami)
   ```
   ![imagen](https://github.com/user-attachments/assets/9d038e99-77d0-4820-b90e-2d96872c9343)

---

## **7. Diferencias entre `htop` y `top`**  
| Comando | Diferencias |
|---------|------------|
| `top` | Herramienta predeterminada en Unix/Linux. Interfaz en texto, básica y menos intuitiva. |
| `htop` | Versión mejorada de `top`. Soporta navegación con el teclado, permite matar procesos con teclas de acceso rápido y tiene una mejor presentación gráfica. |

Para instalar `htop`:  
```bash
sudo apt install htop  # Debian/Ubuntu
sudo dnf install htop  # Fedora
sudo pacman -S htop    # Arch Linux
```
![imagen](https://github.com/user-attachments/assets/489215d9-310c-408a-81f0-4e18f90e49cd)

Para ejecutarlo:  
```bash
htop
```
![imagen](https://github.com/user-attachments/assets/67c4bc65-c548-4d32-a77e-a7852890f961)

---

## **8. Intentar cerrar un proceso desde una cuenta de usuario normal**  
Si intentamos cerrar un proceso que pertenece a `root`, como usuario normal, no podremos, dará un error de permisos. Para matar el proceso como `root`, ejecutamos:  
```bash
sudo htop # Ejecutamos htop como root

sudo kill <PID> # Opcion alternativa, hacemos kill como root al proceso usando su PID
```

---

## **9. ¿Para qué sirve el comando `kill`?**  
El comando `kill` envía señales a los procesos para terminarlos o controlarlos. Algunas señales comunes son:  

| Señal | Descripción |
|-------|------------|
| `kill -15 <PID>` | Enviar la señal SIGTERM para cerrar un proceso de forma segura. |
| `kill -9 <PID>` | Enviar la señal SIGKILL para forzar la terminación del proceso. |
| `kill -1 <PID>` | Reiniciar el proceso enviando SIGHUP. |

---

## **10. Terminar un proceso por su nombre en lugar de su PID**  
Para matar un proceso usando su nombre:  
```bash
pkill nombre_proceso
```
Ejemplo, para cerrar `firefox`:  
```bash
pkill firefox
```
![imagen](https://github.com/user-attachments/assets/f404d460-0261-488a-9429-58e6a894fb26)

---

## **11. Cerrar todos los procesos pertenecientes a Mozilla Firefox**  
```bash
killall firefox
```
O usando `pkill`:  
```bash
pkill -9 firefox
```
Como no esta firefox abierto, no encontrará el proceso:

![imagen](https://github.com/user-attachments/assets/adbcfbae-9165-40b4-ae9e-82e9fa9a6931)


---

## **Comando `jobs`**  

El comando `jobs` se usa para listar procesos ejecutándose en segundo plano o en primer plano.  

### **Sintaxis:**
```bash
jobs [opciones]
```

### **Opciones:**
- `-l`: Muestra el identificador del grupo de proceso.
- `-n`: Muestra solo los trabajos que se han detenido recientemente.
- `-p`: Muestra solo el identificador de proceso para los líderes de grupo.

### **Ejemplo de uso:**
```bash
sleep 100 &
jobs
```
![imagen](https://github.com/user-attachments/assets/bb40def2-dbf2-4a63-a002-3e2010e45db1)

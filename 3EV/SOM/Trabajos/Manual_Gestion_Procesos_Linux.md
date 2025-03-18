# 📌 Gestión de Procesos en Linux

## 🖥️ Entorno Gráfico

### 🛠️ **Monitor del Sistema**
Para ejecutarlo en entornos gráficos:
1. Ir a **Aplicaciones** -> **Buscar "Monitor del Sistema"**  
   *(En versiones antiguas teniamos la pestaña "Sistema" dentro del Monitor del Sistema. Ahora está en **Configuración** -> **Detalles** -> **Acerca de**.)*

#### 🔹 **Pestaña Procesos**
- Muestra todos los procesos en ejecución junto con información relevante:
  - **PID (Process ID)**  
  - **Usuario que lo ejecuta**  
  - **Uso de CPU y memoria**  
  - **Prioridad**  
  - **Estado del proceso (Running, Sleeping, etc.)**  
  - **Comando que lo inició**  

#### 🔹 **Pestaña Recursos**
- Permite ver el consumo de:
  - **CPU**
  - **Memoria RAM**
  - **Red (tráfico de subida y bajada)**

---

## 🖥️ **Modo Texto (Comandos)**

### 🔍 `ps` – Información de procesos
#### 🔹 **Uso:**
Muestra el estado de los procesos con distintas opciones para personalizar la salida.

#### 🔹 **Sintaxis:**
```bash
ps [opciones]
```
#### 🔹 **Opciones:**
| Opción | Descripción |
|--------|------------|
| `-A` | Muestra todos los procesos con PID, TTY, TIME y CMD |
| `-ely` | Lista todos los procesos con información detallada (PID, PPID, NI, RSS, etc.) |
| `aux` | Muestra todos los procesos con columnas como USER, PID, %CPU, TIME, etc. (sin guion) |

---

### 🌳 `pstree` – Árbol de procesos
#### 🔹 **Uso:**
Muestra los procesos en forma de árbol, indicando qué procesos han sido iniciados por otros.

#### 🔹 **Ejemplo:**
```bash
pstree -p
```
*(Muestra los procesos junto con sus PID en un formato de árbol.)*

---

### 🔄 `nohup` y `&` – Ejecutar procesos en segundo plano
#### 🔹 **Uso:**
Permiten ejecutar procesos que continúan funcionando incluso si se cierra la terminal.

#### 🔹 **Ejemplo:**
```bash
nohup comando &
```
*(Ejecuta `comando` en segundo plano y evita que se detenga al cerrar sesión.)*

---

### ⚖️ `nice` y `renice` – Ajustar prioridad de procesos
#### 🔹 **Uso:**
Permiten modificar la prioridad de ejecución de un proceso.

#### 🔹 **Ejemplos:**
```bash
nice -n 10 mi_proceso
```
*(Ejecuta `mi_proceso` con prioridad 10.)*

```bash
renice -5 -p 1234
```
*(Cambia la prioridad del proceso con PID 1234 a -5.)*

---

### 📋 `jobs`, `fg`, `bg` – Manejo de trabajos en segundo plano
#### 🔹 **Uso:**
Controlan procesos en segundo plano.

#### 🔹 **Ejemplos:**
```bash
jobs
```
*(Lista procesos suspendidos o en segundo plano.)*

```bash
fg %1
```
*(Trae al primer plano el trabajo número 1.)*

```bash
bg %2
```
*(Reanuda en segundo plano el trabajo número 2.)*

---

### 🔫 `kill` y `killall` – Finalizar procesos
#### 🔹 **Uso:**
Permiten terminar procesos de forma segura o forzada.

#### 🔹 **Ejemplos:**
```bash
kill -9 1234
```
*(Mata el proceso con PID 1234 de manera forzada.)*

```bash
killall firefox
```
*(Finaliza todos los procesos con el nombre "firefox".)*

---

### ⏱️ `time` – Medir tiempo de ejecución
#### 🔹 **Uso:**
Muestra cuánto tiempo tarda un proceso en ejecutarse.

#### 🔹 **Ejemplo:**
```bash
time ls -l
```
*(Muestra el tiempo que tarda en ejecutarse el comando `ls -l`.)*

---

### 📊 `top` – Monitorización en tiempo real
#### 🔹 **Uso:**
Muestra información en tiempo real de los procesos activos, uso de CPU, memoria, etc.

#### 🔹 **Ejemplo:**
```bash
top
```

---

### 🚀 `htop` – Versión mejorada de `top`
#### 🔹 **Uso:**
Proporciona una interfaz más visual e interactiva para monitorear procesos. Aunque no lo ponga en el libro, lo he incluido porque hoy en dia muchos sistemas lo incluyen y me ha sido muy util.

#### 🔹 **Ejemplo:**
```bash
htop
```
*(Debe estar instalado. Se puede instalar con `sudo apt install htop` en Debian/Ubuntu o `sudo pacman -S htop` en Arch.)*

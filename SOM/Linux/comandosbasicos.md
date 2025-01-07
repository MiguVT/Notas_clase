Claro, aquí tienes un README mejorado con los comandos básicos de Linux, incluyendo `whereis` y `alias`:

---

# Comandos Básicos de Linux

Este documento cubre algunos de los comandos más útiles en Linux para interactuar con el sistema y obtener información sobre él.

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

¡Espero que encuentres útil esta información para trabajar de manera más eficiente con Linux!

# Manual de Gestión de Usuarios y Permisos en Linux

## 1. Gestión de Usuarios y Grupos

### 1.1 Comandos Básicos

#### Crear un usuario:
```bash
sudo useradd -m usuario
```

#### Establecer contraseña a un usuario:
```bash
sudo passwd usuario
```

#### Modificar un usuario:
```bash
sudo usermod -aG grupo usuario  # Añadir a un grupo
sudo usermod -l nuevo_nombre usuario  # Cambiar nombre de usuario
sudo usermod -d /nuevo/directorio usuario  # Cambiar directorio home
```

#### Eliminar un usuario:
```bash
sudo userdel -r usuario
```

### 1.2 Gestión de Grupos

#### Crear un grupo:
```bash
sudo groupadd grupo
```

#### Añadir un usuario a un grupo:
```bash
sudo usermod -aG grupo usuario
```

#### Eliminar un usuario de un grupo:
```bash
sudo deluser usuario grupo
```

#### Cambiar el grupo principal de un usuario:
```bash
sudo usermod -g grupo usuario
```

#### Eliminar un grupo:
```bash
sudo groupdel grupo
```

---

## 2. Gestión de Permisos y Propiedades

### 2.1 Cambiar permisos con `chmod`
Los permisos en Linux se dividen en:
- **r (read)**: Permiso de lectura (4)
- **w (write)**: Permiso de escritura (2)
- **x (execute)**: Permiso de ejecución (1)

#### Cambiar permisos con modo numérico:
```bash
chmod 755 archivo
```
Explicación:
- **7 (rwx)**: Dueño puede leer, escribir y ejecutar
- **5 (r-x)**: Grupo puede leer y ejecutar
- **5 (r-x)**: Otros pueden leer y ejecutar

#### Cambiar permisos con modo simbólico:
```bash
chmod u+x archivo  # Añadir ejecución al usuario
chmod g-w archivo  # Quitar escritura al grupo
chmod o=r archivo  # Establecer permisos de solo lectura a otros
```

### 2.2 Cambiar propietario con `chown`

#### Cambiar el dueño de un archivo:
```bash
sudo chown usuario archivo
```

#### Cambiar el grupo de un archivo:
```bash
sudo chown :grupo archivo
```

#### Cambiar dueño y grupo a la vez:
```bash
sudo chown usuario:grupo archivo
```

---

## 3. Ejercicios Prácticos

### Ejercicio 1: Crear un usuario y asignarlo a un grupo
**Instrucciones:**
1. Crea un usuario llamado `estudiante` con directorio home.
2. Crea un grupo llamado `linux`.
3. Añade `estudiante` al grupo `linux`.
4. Verifica que el usuario pertenece al grupo.

**Solución:**
```bash
sudo useradd -m estudiante
sudo groupadd linux
sudo usermod -aG linux estudiante
groups estudiante
```

---

### Ejercicio 2: Modificar permisos de un archivo
**Instrucciones:**
1. Crea un archivo llamado `practica.txt`.
2. Establece permisos de lectura y escritura para el dueño, pero solo lectura para los demás.
3. Cambia el dueño del archivo a `estudiante`.

**Solución:**
```bash
touch practica.txt
chmod 644 practica.txt
sudo chown estudiante practica.txt
```

---

### Ejercicio 3: Crear un directorio compartido entre usuarios
**Instrucciones:**
1. Crea un grupo llamado `colaboradores`.
2. Crea un directorio `/opt/colaborativo`.
3. Cambia el grupo del directorio a `colaboradores`.
4. Da permisos para que los miembros del grupo puedan leer, escribir y ejecutar.

**Solución:**
```bash
sudo groupadd colaboradores
sudo mkdir /opt/colaborativo
sudo chown :colaboradores /opt/colaborativo
sudo chmod 770 /opt/colaborativo
```

---

## Conclusión
Este manual que he creado proporciona una base sólida para gestionar usuarios, grupos y permisos en Linux. Con estos conocimientos, es posible administrar sistemas de manera efectiva, asegurando seguridad y control sobre los archivos y usuarios del sistema.

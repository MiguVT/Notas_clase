# Práctica: Usuarios del Sistema en Linux

## 1. Usuarios del Sistema en la Máquina Virtual
Para listar los usuarios del sistema, debo que ejecutar el siguiente comando:

```bash
cat /etc/passwd
```

**Captura del output:**

![imagen](https://github.com/user-attachments/assets/adea1bf0-b04c-46e4-9203-d59a45d90795)

Los usuarios del sistema suelen tener identificadores de usuario (UID) por debajo de 1000 y no tienen un directorio home asignado.

---

## 2. Investigación sobre Usuarios del Sistema

Estos son los propósitos de algunos usuarios comunes del sistema en Linux:

- **nobody:** Es un usuario con privilegios mínimos utilizado para ejecutar procesos sin permisos especiales.
- **games:** Se usaba antiguamente para ejecutar juegos en sistemas multiusuario sin necesidad de privilegios elevados.
- **daemon:** Se asigna a procesos de fondo (demonios) que no requieren acceso root.
- **sys:** Asociado a tareas administrativas del sistema.
- **bin:** Se usaba en versiones antiguas de UNIX para ejecutar comandos esenciales.
- **sync:** Permite sincronizar datos con el disco antes de apagar el sistema.

---

## 3. Conclusión sobre el Uso de Usuarios del Sistema

Los usuarios del sistema en Linux cumplen una función esencial y principal en la separación de privilegios y la seguridad del sistema. Permiten que procesos y servicios operen con permisos específicos sin necesidad de ejecutarse como root, minimizando riesgos de seguridad en aplicaciones maliciosas o vulnerables. Esta arquitectura refuerza la estabilidad y protección del sistema operativo, previniendo accesos no autorizados y limitando el impacto de posibles vulnerabilidades.

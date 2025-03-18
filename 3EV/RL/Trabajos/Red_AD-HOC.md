# Creación de una Red Ad-hoc en Windows

## ¿Qué es una red Ad-hoc?

Una red **Ad-hoc** es una red inalámbrica temporal en la que los dispositivos se conectan directamente entre sí sin necesidad de un punto de acceso o router. Este tipo de redes es útil en situaciones donde se requiere una conexión rápida y sin infraestructura adicional, como compartir archivos o conexión a Internet entre equipos cercanos.

---

## Creación de una red Ad-hoc en Windows

A continuación, se detallan los pasos para crear una red Ad-hoc en Windows utilizando la línea de comandos.

### 1️⃣ Comprobar compatibilidad de la tarjeta WiFi
Para verificar si la tarjeta WiFi del equipo admite el modo **Hosted Network**, abrimos la terminal de comandos:

1. Pulsamos `Win + R`, escribimos `cmd` y presionamos `Enter`.
2. Ejecutamos el siguiente comando:
   ```cmd
   netsh wlan show drivers
   ```
3. Buscamos la línea que dice **Hosted network supported** y verificamos que diga "Yes".

![Comprobación de compatibilidad](https://github.com/user-attachments/assets/88d16600-0f8b-4e09-9a17-5038095f5266)

---

### 2️⃣ Crear la red Ad-hoc
Para crear la red Ad-hoc con el nombre `Mi_RED13` y la clave `Contra13`, utilizamos el siguiente comando:

```cmd
netsh wlan set hostednetwork mode=allow ssid=Mi_RED13 key=Contra13
```

![Creación de la red](https://github.com/user-attachments/assets/a9bf3253-2115-463f-8c9d-58611a1cbb6a)

---

### 3️⃣ Iniciar la red Ad-hoc
Para activar la red que acabamos de crear, ejecutamos:

```cmd
netsh wlan start hostednetwork
```

![Inicio de la red](https://github.com/user-attachments/assets/dc46ac1d-8bf6-440b-a0b0-3f1ba65c05e8)

---

### 4️⃣ Compartir la conexión de Internet
Para compartir el acceso a Internet desde la conexión Ethernet con la red Ad-hoc creada:

1. Vamos a **Panel de control** > **Redes e Internet** > **Centro de redes y recursos compartidos**.
2. Localizamos la conexión principal a Internet (Ethernet en nuestro caso).
3. Hacemos **clic derecho** sobre la conexión y seleccionamos **Propiedades**.
4. En la pestaña **Compartir**, marcamos la opción:
   - ✅ "Permitir que otros usuarios de la red se conecten a través de la conexión a Internet de este equipo".
5. En **Conexión de red doméstica**, seleccionamos la red Ad-hoc `Mi_RED13`.

![Compartir Internet](https://github.com/user-attachments/assets/e89419db-3bdc-46ed-adb7-d0e8b2a2f1fe)

---

### 5️⃣ Comprobar que la red funciona
Para verificar que la red está operativa, podemos utilizar otro dispositivo para conectarnos a `Mi_RED13` e intentar acceder a Internet.

![Comprobación de conexión](https://github.com/user-attachments/assets/1a7e6ea5-875c-4968-80ea-88eb71938579)

---

### 6️⃣ Detener la red Ad-hoc
Si queremos desactivar la red Ad-hoc, ejecutamos el siguiente comando:

```cmd
netsh wlan stop hostednetwork
```

![Detención de la red](https://github.com/user-attachments/assets/9ca22cab-36f1-4eb3-a6b8-1652704460e4)

---

### ✅ Conclusión
Siguiendo estos pasos, hemos creado una red Ad-hoc en Windows, la hemos configurado para compartir la conexión a Internet y hemos verificado su correcto funcionamiento. Esta configuración es útil en entornos donde no se dispone de un router WiFi y se necesita compartir la conexión entre varios dispositivos.

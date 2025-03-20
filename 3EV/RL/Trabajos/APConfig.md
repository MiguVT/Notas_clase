# Configuración de un Punto de Acceso (AP)

## 📌 Portada
- **Título:** Configuración de un Punto de Acceso (AP)
- **Nombre:** Yara
- **Curso:** 21F
- **Año:** 2025

---

## 📖 Índice  
1. [**Objetivo del documento**](#-objetivo-del-documento)  
2. [**Configuración del dispositivo**](#-configuración-del-dispositivo)  
   - [Acceso al AP](#-acceso-al-ap)  
   - [Dirección IP y DHCP](#-dirección-ip-y-dhcp)
   - [Configuración de la red WiFi](#-configuración-de-la-red-wifi)  
   - [Seguridad y filtrado MAC](#-seguridad-y-filtrado-mac)  
3. [**Elección del canal menos interferido**](#-elección-del-canal-menos-interferido)  
4. [**Comando `netsh wlan` en Windows**](#%EF%B8%8F-uso-del-comando-netsh-wlan)  
   - [Ver perfiles de red WiFi](#-a-ver-perfiles-de-red-wifi)  
   - [Obtener información de la tarjeta inalámbrica](#-b-obtener-información-de-la-tarjeta-inalámbrica)  
   - [Conocer la configuración del adaptador WiFi](#-c-conocer-la-configuración-del-adaptador-wifi)  
   - [Recuperar claves de seguridad de perfiles almacenados](#-d-recuperar-claves-de-seguridad-de-perfiles-almacenados)  
   - [Borrar un perfil de red WiFi](#-e-borrar-un-perfil-de-red-wifi)  
   - [Explorar redes cercanas](#-f-explorar-redes-wifi-cercanas)  

---

## 🎯 Objetivo del Documento
Este documento detalla el proceso de configuración de un punto de acceso (AP) mediante un emulador web y la selección del canal menos interferido utilizando la aplicación **Vistumbler** (elegida por mi, al ser codigo abierto). También se explorará el uso del comando `netsh wlan` en Windows para la gestión de redes WiFi.

---

## 🔧 Configuración del Dispositivo

### 🔹 Acceso al AP
Para acceder al punto de acceso:
1. Abrimos el navegador y entramos en:
   [https://emulator.tp-link.com/EMULATOR_wr840nv4_eu/index.htm](https://emulator.tp-link.com/EMULATOR_wr840nv4_eu/index.htm)
2. Introducimos las credenciales:
   - **Usuario:** `jesuitas13`
   - **Contraseña:** `Colegio01`

El simulador no tiene Login, por lo que pasamos directamente al siguiente punto.

---

### 🔹 Dirección IP y Deshabilitación del DHCP
1. Configuramos la IP del AP:
   - Dirección IP: `192.168.4.13`
2. Deshabilitamos el **servidor DHCP** para evitar conflictos en la red.

![imagen](https://github.com/user-attachments/assets/2918ccc6-dda4-4925-b093-2a4a1f02a17b)
![imagen](https://github.com/user-attachments/assets/4c4c1ee3-2f2b-437d-8350-4df26a3043e7)


---

### 🔹 Configuración de la Red WiFi
1. Configuramos el **SSID** con el nombre `Mi_red_13`.
2. Elegimos el **canal menos interferido** (ver apartado siguiente).
3. Seleccionamos el modo **11bgn mixed**, ya que en la red hay tarjetas que soportan ambos estándares.

![imagen](https://github.com/user-attachments/assets/5a3f9221-2c1b-43c6-bab9-3827602760f8)

---

### 🔹 Seguridad y Filtrado MAC
1. Configuramos la seguridad con **cifrado WPA2** y la clave `pelota`.
2. Habilitamos el **filtrado MAC**, permitiendo solo el acceso a nuestro equipo. (En el simulador no me deja activarlo)

![imagen](https://github.com/user-attachments/assets/5c43f2be-93f6-4d09-a4c9-18dbbb001d19)
![imagen](https://github.com/user-attachments/assets/79167503-2edb-45fa-8532-6d8f2c48082d)

---

## 📡 Elección del Canal Menos Interferido
Para evitar interferencias con otras redes WiFi cercanas, utilizamos **Vistumbler** (software open-source) para analizar el espectro de canales.

### 📌 Pasos:
1. Descargamos e instalamos **Vistumbler**.
2. Escaneamos las redes cercanas. (boton Start)
3. Identificamos el canal menos saturado. (Para una vista mas clara a la izquierda esta un desplegable "Channel" con todos los canales escaneados.
4. Configuramos el AP en dicho canal.

![imagen](https://github.com/user-attachments/assets/186eab53-0365-4855-8120-10a8c51ae8d6)
![imagen](https://github.com/user-attachments/assets/2495ec9a-d531-4f39-b651-7681a039623c)

📌 **Justificación:** Se ha seleccionado el canal `2` porque presenta menos interferencias en comparación con otros canales cercanos y hay uno llamado WIFI-BUS que interpreto que sera un wifi de un bus y sera temporal.
Para elegir un mejor canal, suelo usar el movil con la app WifiAnalyzer disponible en la tienda F-Droid, pero en este caso he utilizado este otro programa ya que no podemos usar el movil.

---

## ⚙️ Uso del Comando `netsh wlan`
El comando `netsh wlan` en Windows nos permite gestionar conexiones WiFi desde la terminal.

### 📌 Comandos utilizados:

#### 🔹 a) Ver perfiles de red WiFi
```cmd
netsh wlan show profiles
```
![imagen](https://github.com/user-attachments/assets/f0fcf874-999f-493b-8fa3-562a0772ef49)

#### 🔹 b) Obtener información de la tarjeta inalámbrica
```cmd
netsh wlan show interfaces
```
**[INSERTAR IMAGEN DEL RESULTADO]**

#### 🔹 c) Conocer la configuración del adaptador WiFi
```cmd
netsh wlan show drivers
```
![imagen](https://github.com/user-attachments/assets/86adc278-3c89-4657-82d8-48e7573bb1e5)

#### 🔹 d) Recuperar claves de seguridad de perfiles almacenados
```cmd
netsh wlan show profile name="NombreDeRed" key=clear
```
![imagen](https://github.com/user-attachments/assets/77921a0e-5166-4bef-a35a-70bf7449c799)

#### 🔹 e) Borrar un perfil de red WiFi
```cmd
netsh wlan delete profile name="NombreDeRed"
```
![imagen](https://github.com/user-attachments/assets/3d32e01b-096d-4d9a-bcfb-62c8cf0eb160)

#### 🔹 f) Explorar redes WiFi cercanas
```cmd
netsh wlan show networks mode=bssid
```
![imagen](https://github.com/user-attachments/assets/6d8e3f54-abff-40ec-8e51-5a8b7dd73013)

---

## ✅ Conclusión
En este documento hemos configurado un punto de acceso de manera óptima, seleccionado el mejor canal mediante Vistumbler y aprendido a gestionar redes WiFi con `netsh wlan`.

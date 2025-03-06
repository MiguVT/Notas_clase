# **Vulnerabilidades del SSID Oculto en Redes WiFi**

## **Introducción**
En la actualidad, la seguridad en redes inalámbricas es un aspecto fundamental para garantizar la protección de los datos y la privacidad de los usuarios. Una práctica común es ocultar el SSID (Service Set Identifier) de una red WiFi con la idea de que esto aumentará la seguridad. Sin embargo, diversas investigaciones han demostrado que esta estrategia **no solo es inefectiva, sino que puede hacer que la red sea más vulnerable a ciertos ataques**. Este documento explora las razones técnicas por las cuales ocultar el SSID no representa una mejora en la seguridad y qué medidas alternativas pueden implementarse para proteger una red inalámbrica.

---

## **1. ¿Qué es el SSID y cómo funciona?**
El SSID es el identificador de una red WiFi y permite que los dispositivos la reconozcan y se conecten a ella. Normalmente, los routers transmiten el SSID en intervalos regulares mediante paquetes llamados **beacon frames**, lo que permite que los dispositivos descubran la red de manera automática y sin necesidad de realizar búsquedas manuales.

Cuando el SSID está oculto, el router deja de incluir el nombre de la red en estos paquetes, lo que hace que los dispositivos no puedan detectarla de forma pasiva. En su lugar, deben enviar **solicitudes de búsqueda activas (Probe Requests)** para intentar encontrar la red y conectarse a ella.

---

## **2. ¿Por qué ocultar el SSID no es seguro?**
### **2.1. No oculta la existencia de la red**
Ocultar el SSID solo impide que la red aparezca en la lista de redes disponibles para usuarios comunes, pero **no impide que un atacante con herramientas avanzadas la detecte**. 

**Razones por las que la red sigue siendo visible para un atacante:**
- Los dispositivos conectados a la red envían paquetes de autenticación que contienen el SSID en texto claro.
- Un atacante puede utilizar herramientas como **Wireshark, Kismet o Airodump-ng** para capturar estos paquetes y revelar el SSID.

### **2.2. Aumenta el riesgo de ataques de suplantación de red (Evil Twin Attack)**
Cuando el SSID está oculto, los dispositivos que se han conectado previamente a la red comienzan a **enviar solicitudes de búsqueda activas (Probe Requests)** preguntando por la red específica a la que quieren conectarse.

Este comportamiento permite a un atacante capturar estas solicitudes y conocer el nombre de la red, lo que facilita un ataque de **suplantación de red (Evil Twin Attack)**. En este tipo de ataque:
1. El atacante configura un punto de acceso falso con el mismo SSID.
2. Los dispositivos intentan conectarse a la red falsa sin darse cuenta.
3. Una vez conectados, el atacante puede interceptar tráfico, robar credenciales o incluso inyectar malware.

### **2.3. No protege contra ataques de fuerza bruta o cracking de contraseñas**
El SSID oculto **no afecta la seguridad del cifrado de la red**. Un atacante que capture el **handshake WPA2/WPA3** durante el proceso de autenticación podrá:
- Intentar descifrar la clave con ataques de fuerza bruta o diccionario utilizando herramientas como **Aircrack-ng o Hashcat**.
- Enviar paquetes de **deautenticación** para forzar a los dispositivos a reconectarse y capturar nuevamente el handshake.

---

## **3. Problemas adicionales de ocultar el SSID**
### **3.1. Problemas de compatibilidad y conectividad**
- Algunos dispositivos IoT o más antiguos no pueden conectarse correctamente a redes con SSID oculto.
- Puede causar que los dispositivos consuman más batería al realizar búsquedas constantes de la red.
- El usuario debe ingresar manualmente el SSID en cada dispositivo, lo que puede generar errores de conexión.

### **3.2. Dificulta la administración de la red**
- Para diagnosticar problemas de conexión, se necesita acceder manualmente a la configuración de cada dispositivo.
- No impide la detección de la red por parte de atacantes, lo que hace que la gestión de la seguridad sea más complicada.

---

## **4. Estrategias efectivas para mejorar la seguridad del WiFi**
En lugar de ocultar el SSID, se recomienda aplicar las siguientes medidas de seguridad:

1. **Usar WPA3 (o WPA2-AES en su defecto)** para garantizar un cifrado robusto.
2. **Desactivar WPS** (Wi-Fi Protected Setup), ya que es una vulnerabilidad frecuente.
3. **Reducir la potencia de emisión del router** para minimizar la exposición de la red a áreas no deseadas.
4. **Habilitar 802.11w (Protected Management Frames)** para evitar ataques de deautenticación.
5. **Segmentar la red con VLANs o una red de invitados** para dispositivos menos seguros.
6. **Establecer una contraseña segura** y cambiarla periódicamente en caso de sospecha de actividad maliciosa.

---

## **Conclusión**
Contrario a la creencia popular, ocultar el SSID **no mejora la seguridad** y, en muchos casos, **puede hacer que una red sea más vulnerable**. Esto se debe a que obliga a los dispositivos a enviar solicitudes constantes para encontrar la red, exponiéndola a atacantes. Además, **los ataques más comunes contra redes WiFi no dependen de si el SSID está visible o no**, sino de la fortaleza del cifrado y la configuración del router.

Para una seguridad efectiva, es fundamental **utilizar un cifrado fuerte (WPA3/WPA2-AES), desactivar WPS y aplicar medidas de protección adicionales** en lugar de depender de estrategias ineficaces como la ocultación del SSID.


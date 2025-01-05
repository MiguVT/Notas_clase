### ¡ADVERTENCIA! Este documento es para un trabajo, pero lo documentare tambien para cualquier persona que no sepa nada pueda entender y aprender.

---

# **Configuración de red en Ubuntu 14.04 en una MV con VMware**

Este documento explica paso a paso cómo configurar una IP estática y una IP dinámica en Ubuntu 14.04 instalado en una máquina virtual (MV) usando VMware. Se mostrarán dos métodos: usando el entorno gráfico y editando el archivo de configuración `/etc/network/interfaces`. Además, se incluyen pruebas de conectividad para verificar que todo funcione correctamente.

---

## **Requisitos previos**

- Máquina virtual con Ubuntu 14.04 ya instalada (en mi caso en VMware).
- Conexión a Internet funcional en la MV para actualizar paquetes.
- Conocimientos básicos de comandos Linux y configuración de red.
- VMWare en modo Bridged o su equivalente en otro software de emulación (VirtualBox puede dar conflictos con VMWare, en virtual network editor haz bridged to a tu tarjeta de red)

---
#### La configuración escrita supone que:
- La puerta de enlace es 192.168.31.1 (Como la de mi hogar)
- La direccion ip no esta en uso en tu red local
- Dispones de un servidor DHCP en tu entorno
- Los DNS usados funcionan.
- [Mascara de red /24](https://es.wikipedia.org/wiki/M%C3%A1scara_de_red) ([CIDR](https://es.wikipedia.org/wiki/Classless_Inter-Domain_Routing))
## **Configuración de red: IP Estática**

### **1. Configuración usando el entorno gráfico**

1. **Abrir las opciones de red**:
   - En el menú de ajustes, haz clic en **Network/Red** (o simplemente busca "Red" o "Network" en el menú).
![image](https://github.com/user-attachments/assets/ca6496fd-c74d-4d72-9d4b-23028096c0e5)

2. **Seleccionar la conexión**:
   - Verás las conexiones disponibles (como `eth0` o `ens33` dependiendo del adaptador aunque no se vera este nombre). Selecciona la conexión activa y haz clic en **Options**.
![image](https://github.com/user-attachments/assets/d7de424d-65fb-4bf6-9dce-ac6662c12261)

3. **Cambiar el método a manual**:
   - En la pestaña **IPv4**, cambia el método a **Manual**.
![image](https://github.com/user-attachments/assets/15ec7468-69c8-4bdc-a855-e5d7a1ba1a4f)

   - Añade los siguientes datos:
     - Dirección IP: `192.168.31.10` (o cualquier IP que no esté en uso en tu red local).
     - Máscara de subred: `255.255.255.0` (24 ya que Ubuntu te lo pide en formato [CIDR](https://es.wikipedia.org/wiki/Classless_Inter-Domain_Routing)).
     - Puerta de enlace: `192.168.31.1`.
     - DNS: `8.8.8.8` (puedes añadir más si quieres, separados por comas).
       ![image](https://github.com/user-attachments/assets/6c6ccb9d-7720-4462-bf4e-6037da09a1da)


4. **Guardar los cambios y aplicar**:
   - Haz clic en **Guardar** y desconecta/reconecta la red para asegurarte de aplicar los cambios.

5. **Comprobar la configuración**:
   - Abre una terminal y escribe:
     ```bash
     ifconfig
     ```
     Asegúrate de que la IP configurada aparece en la interfaz correcta.
   - Haz un ping para comprobar la conectividad:
     ```bash
     ping 8.8.8.8
     ```

   - **Anecdota:**
     - Tras intentar hacer el ping, descubri que mi router solo da acceso a la red a los dispositivos con la ip 192.168.31.xxx
     ![image](https://github.com/user-attachments/assets/ded549e1-dd88-4497-b062-e9e75cfdfde3)

---

### **2. Configuración editando el archivo `/etc/network/interfaces`**

1. **Abrir el archivo**:
   - Abre una terminal y escribe:
     ```bash
     sudo nano /etc/network/interfaces
     ```

2. **Añadir la configuración de la IP estática**:
   - Localiza o añade las líneas correspondientes a la interfaz (por ejemplo, `eth0` o `ens33`) y escribe lo siguiente:
     ```bash
     auto eth0
     iface eth0 inet static
     address 192.168.31.10
     netmask 255.255.255.0
     gateway 192.168.31.1
     dns-nameservers 8.8.8.8
     ```
     ![image](https://github.com/user-attachments/assets/5e596a48-a4c3-467d-9633-157c914790bf)


3. **Reiniciar la red**:
   - Guarda los cambios (Ctrl+O para guardar, Ctrl+X para salir) y reinicia eth0 con:
     ```bash
     sudo ifdown eth0 && sudo ifup eth0
     ```
     Si no consigues reiniciar, ni con el comando service como en mi caso, reiniciar lo soluciona casi siempre.

4. **Verificar la configuración**:
   - Usa `ifconfig` para confirmar que la IP estática se aplicó correctamente.
   - Haz un ping para comprobar la conectividad:
     ```bash
     ping 8.8.8.8
     ```
![image](https://github.com/user-attachments/assets/cee02b7f-6d0a-4a32-82ec-013c17c04db5)

---

## **Configuración de red: IP Dinámica**

### **1. Configuración usando el entorno gráfico**

1. **Abrir las opciones de red**:
   - Igual que antes, ve al menú de red y selecciona la conexión activa.

2. **Cambiar a DHCP**:
   - En la pestaña **IPv4**, selecciona el método **Automático (DHCP)**.

3. **Guardar y aplicar**:
   - Haz clic en **Guardar** y reinicia la conexión.

4. **Verificar**:
   - En la terminal, escribe:
     ```bash
     ifconfig
     ```
     La IP asignada debería ser proporcionada automáticamente por el servidor DHCP de tu red.

#### No creo que sea necesario poner una captura aqui, ya que esto es practicamente lo anterior solo que en vez Manual se selecciona la opción de DHCP
---

### **2. Configuración editando el archivo `/etc/network/interfaces`**

1. **Abrir el archivo**:
   - Igual que antes, abre `/etc/network/interfaces` con:
     ```bash
     sudo nano /etc/network/interfaces
     ```

2. **Cambiar la configuración a DHCP**:
   - Escribe lo siguiente para la interfaz correspondiente:
     ```bash
     auto eth0
     iface eth0 inet dhcp
     ```

3. **Reiniciar la red**:
   - Guarda los cambios y reinicia la red, si no funciona ni el anterior comando ni este prueba a reiniciar:
     ```bash
     sudo service networking restart
     ```

4. **Verificar**:
   - Usa `ifconfig` para comprobar que se ha asignado una IP automáticamente.
![image](https://github.com/user-attachments/assets/9f028515-0a0b-418c-8c77-6d1376d68550)

---

## **Pruebas de conectividad**

1. **Verificar la IP**:
   - Asegúrate de que la IP configurada (estática o dinámica) aparece correctamente con:
     ```bash
     ifconfig
     ```

2. **Probar la conexión**:
   - Haz un ping a una dirección externa, como:
     ```bash
     ping 8.8.8.8
     ```
   - Si recibes respuesta, la conexión está funcionando.

3. **Comprobar resolución de DNS**:
   - Haz un ping a un dominio para confirmar que los servidores DNS funcionan:
     ```bash
     ping miguvt.com
     ```

* Si abres el navegador y te carga una pagina web (siempre que no este en local) significa que todo lo mencionado anteriormente funciona, si eso comprobar ifconfig para saber si se ha cambiado correctamente.
* ![image](https://github.com/user-attachments/assets/d34863c7-1e1b-4cd7-9fd9-f04ddf4daa93)

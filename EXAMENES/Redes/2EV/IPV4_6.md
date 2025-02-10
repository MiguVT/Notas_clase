# 📘 **Resumen Completo para el Examen: Direccionamiento IPv4 & IPv6**

Este resumen ha sido elaborado como un libro de estudio estructurado, con un enfoque claro y técnico. Su objetivo es proporcionar un recurso preciso y bien organizado para el aprendizaje del direccionamiento IP y redes.

El contenido sigue un estilo formal y técnico, evitando un tono excesivamente coloquial, para asemejarse más a un manual de referencia. Se presentan explicaciones detalladas, ejercicios resueltos y cálculos paso a paso, asegurando una comprensión profunda de cada concepto.

Este documento está diseñado tanto para mi estudio personal como para servir de guía en futuras consultas.

## **Índice de Contenidos**
1. [Dirección IPv4](#1-dirección-ipv4)
   - [Clases de direcciones IPv4](#-11-clases-de-direcciones-ipv4)
   - [Máscara de subred y CIDR](#-12-máscara-de-subred-y-cidr)
   - [Dirección de Red y Broadcast](#-13-dirección-de-red-y-broadcast)
   - [Direcciones Especiales en IPv4](#-14-direcciones-especiales-en-ipv4)
   - [Subredes y Cálculo de Hosts](#-15-subredes-y-cálculo-de-hosts)
2. [Dirección IPv6](#2-dirección-ipv6)
   - [Tipos de direcciones IPv6](#-21-tipos-de-direcciones-ipv6)
   - [Prefijos importantes en IPv6](#-22-prefijos-importantes-en-ipv6)
   - [Representación de direcciones IPv6](#-23-representación-de-direcciones-ipv6)
3. [Mecanismos de Migración y Coexistencia entre IPv4 e IPv6](#3-mecanismos-de-migración-y-coexistencia-entre-ipv4-e-ipv6)
   - [Pila Dual](#-31-pila-dual)
   - [Túneles](#-32-túneles)
   - [Traducción de Direcciones (NAT64)](#-33-traducción-de-direcciones-nat64)
4. [Ejemplos de Ejercicios](#4-ejemplos-de-ejercicios)
   - [Cálculo de direcciones de red y broadcast](#-41-cálculo-de-direcciones-de-red-y-broadcast)
   - [Identificación de clases de direcciones](#-42-identificación-de-clases-de-direcciones)
   - [Conversión de direcciones IPv4 a IPv6](#-43-conversión-de-direcciones-ipv4-a-ipv6)
5. [Consejos y Recursos Adicionales](#5-consejos-y-recursos-adicionales)
6. [Preguntas tipo examen](#-6-preguntas-tipo-examen)

---

## 1. **Dirección IPv4**

### 📌 **Formato y Estructura**
- **Dirección IPv4:** Compuesta por 32 bits, divididos en 4 octetos de 8 bits cada uno.  
- **Ejemplo:** `192.168.1.1`  
- **Cada dirección IP tiene:**  
  - **Parte de red:** Identifica la red.
  - **Parte de host:** Identifica al dispositivo dentro de esa red.

### 📌 **1.1. Clases de direcciones IPv4**

Las direcciones IPv4 se dividen en varias clases, definidas por el valor de los primeros bits:

| **Clase** | **Rango del primer octeto** | **Máscara por defecto** | **Uso**                             |
|-----------|-----------------------------|-------------------------|-------------------------------------|
| **A**     | `0 - 127`                   | `255.0.0.0`             | Redes muy grandes                  |
| **B**     | `128 - 191`                 | `255.255.0.0`           | Redes medianas                     |
| **C**     | `192 - 223`                 | `255.255.255.0`         | Redes pequeñas                     |
| **D**     | `224 - 239`                 | N/A                     | Multicast                           |
| **E**     | `240 - 255`                 | N/A                     | Reservado para investigación        |

**💡 Ejemplo de Ejercicio:**  
👉 **¿Qué clase es la IP `172.20.10.5`?**  
**Respuesta:** Clase B (ya que el primer octeto es `172`).

### 📌 **1.2. Máscara de subred y CIDR**

- **Máscara de subred:** Se utiliza para determinar qué parte de una dirección IP es la parte de red y cuál es la parte de host.
- **CIDR (Classless Inter-Domain Routing):** Notación que indica cuántos bits pertenecen a la parte de red. Ejemplo: `/24` indica que los primeros 24 bits son la parte de red.

| **CIDR** | **Máscara Decimal**    | **Hosts Disponibles** |
|----------|-----------------------|------------------------|
| `/8`     | `255.0.0.0`           | 16,777,214             |
| `/16`    | `255.255.0.0`         | 65,534                 |
| `/24`    | `255.255.255.0`       | 254                    |

**💡 Ejemplo de Ejercicio:**  
👉 **Encuentra la dirección de red de `192.168.10.45/24`.**  
**Solución:**  
```
192.168.10.45  -> 11000000.10101000.00001010.00101101
255.255.255.0  -> 11111111.11111111.11111111.00000000
Resultado      -> 11000000.10101000.00001010.00000000  (192.168.10.0)
```
**Dirección de Red:** `192.168.10.0`

### 📌 **1.3. Dirección de Red y Broadcast**

- **Dirección de red:** Se obtiene poniendo todos los bits de host en `0`.
- **Dirección de broadcast:** Se obtiene poniendo todos los bits de host en `1`.

**💡 Ejemplo de Ejercicio:**  
👉 **Determina la dirección de red y broadcast de `172.16.5.33/16`.**  
**Solución:**  
```
172.16.5.33  -> 10101100.00010000.00000101.00100001
255.255.0.0  -> 11111111.11111111.00000000.00000000
Red          -> 10101100.00010000.00000000.00000000 (172.16.0.0)
Broadcast    -> 10101100.00010000.11111111.11111111 (172.16.255.255)
```
**Dirección de Red:** `172.16.0.0`  
**Dirección de Broadcast:** `172.16.255.255`

### 📌 **1.4. Direcciones Especiales en IPv4**

- **Loopback (`127.0.0.1`):** Usada para pruebas internas.
- **Enlace local (`169.254.0.0/16`):** Asignadas automáticamente cuando no hay DHCP.
- **Broadcast (`255.255.255.255`):** Envía datos a todos los dispositivos en la red.
- **Dirección por defecto (`0.0.0.0`):** Indica cualquier dirección IP.

**💡 Ejemplo de Ejercicio:**  
👉 **¿Qué dirección se utiliza para pruebas locales en un dispositivo?**  
**Respuesta:** `127.0.0.1` (Loopback).

### 📌 **1.5. Subredes y Cálculo de Hosts**

- **Subredes:** Se crean dividiendo una red grande en redes más pequeñas.
- **Cálculo de subredes:** `2^n` (donde `n` es el número de bits tomados prestados).
- **Cálculo de hosts:** `2^h - 2` (donde `h` es el número de bits de host).

**💡 Ejemplo de Ejercicio:**  
👉 **En una red con máscara `/26`, ¿cuántos hosts se pueden tener?**  
**Solución:**  
```
Bits de host = 6
Hosts posibles = 2^6 - 2 = 62
```
**Total de Hosts:** `62`

---

## 2. **Dirección IPv6**

### 📌 **2.1. Tipos de Direcciones IPv6**

- **Unicast:** Identifica un único dispositivo.
- **Multicast:** Envía datos a un grupo de dispositivos.
- **Anycast:** Se envía al nodo más cercano en un grupo de dispositivos.

### 📌 **2.2. Prefijos Importantes en IPv6**

| **Prefijo**     | **Descripción**                   |
|-----------------|-----------------------------------|
| `2000::/3`      | Unicast global                    |
| `FE80::/10`     | Enlace local                      |
| `FF00::/8`      | Multicast                         |
| `::1`           | Loopback (equivalente a `127.0.0.1`) |

**💡 Ejemplo de Ejercicio:**  
👉 **¿Qué tipo de dirección es `FF02::1`?**  
**Respuesta:** Es una dirección **Multicast**.

### 📌 **2.3. Representación de Direcciones IPv6**

- **Abreviación:** Se omiten los ceros iniciales y se utiliza `::` para múltiples ceros consecutivos.
- **Ejemplo:** `FF01:0:0:0:0:0:0:1` se convierte en `FF01::1`.

**💡 Ejemplo de Ejercicio:**  
👉 **Abrevia la dirección `2001:0db8:0000:0000:0000:0000:0000:1`.**  
**Respuesta:** `2001:db8::1`

---

## 3. **Mecanismos de Migración y Coexistencia entre IPv4 e IPv6**

### 📌 **3.1. Pila Dual**
- Los dispositivos utilizan simultáneamente IPv4 e IPv6.

### 📌 **3.2. Túneles**
- Encapsulan paquetes IPv6 dentro de paquetes IPv4.

### 📌 **3.3. Traducción de Direcciones (NAT64)**
- Traduce direcciones IPv4 a IPv6 y viceversa.

---

## 4. **Ejemplos de Ejercicios**

### 📌 **4.1. Cálculo de direcciones de red y broadcast**

👉 **IP:** `10.0.1.25/8`  
📌 **Dirección de Red:** `10.0.0.0`  
📌 **Broadcast:** `10.255.255.255`

### 📌 **4.2. Identificación de clases de direcciones**

👉 **IP:** `192.168.1.1`  
📌 **Clase:** C

### 📌 **4.3. Conversión de direcciones IPv4 a IPv6**

👉 **IPv4:** `192.168.1.1`  
📌 **IPv6 Mapeada:** `::FFFF:192.168.1.1`

---

## 5. **Consejos y Recursos Adicionales**

1. **Memoriza los rangos de direcciones privadas y las máscaras por defecto.**
2. **Practica ejercicios de conversión binaria y operaciones AND.**
3. **Familiarízate con los prefijos y tipos de direcciones IPv6.**

---

# 📌 **6. Preguntas Tipo Examen**

## **🔹 Sección 1: Clases y tipos de direcciones IPv4**
**1.1.** ¿A qué clase pertenecen las siguientes direcciones IPv4?  
a) `15.25.67.89`  
b) `172.16.45.200`  
c) `220.134.55.78`  
d) `192.168.1.1`  
e) `127.0.0.1`  

📌 **Respuesta esperada:** Identificar si es **Clase A, B, C, D o E** y si es pública o privada.

---

## **🔹 Sección 2: Máscara de subred y CIDR**
**2.1.** Completa la siguiente tabla:

| IP | Máscara de Subred | Notación CIDR |
|----|------------------|--------------|
| `10.0.0.1` | `255.0.0.0` | ? |
| `192.168.100.5` | `255.255.255.0` | ? |
| `172.16.5.10` | `255.255.0.0` | ? |
| `200.10.50.75` | ? | `/26` |
| `150.25.18.60` | ? | `/20` |

📌 **Respuesta esperada:** Completar las máscaras o la notación CIDR correcta.

---

## **🔹 Sección 3: Cálculo de Dirección de Red y Broadcast**
**3.1.** Encuentra la dirección de **red** y de **broadcast** para:  
a) `192.168.20.35 /24`  
b) `172.25.100.200 /22`  
c) `10.0.5.78 /16`  
d) `150.45.10.3 /30`  

📌 **Respuesta esperada:**  
- Convertir a binario  
- Aplicar la máscara con **operación AND**  
- Identificar dirección de broadcast poniendo **todos los bits de host en 1**  

---

## **🔹 Sección 4: Subredes y cantidad de hosts**
**4.1.** ¿Cuántos hosts disponibles tiene una red con estas máscaras?  
a) `/25`  
b) `/27`  
c) `/30`  
d) `/22`  

📌 **Respuesta esperada:** Aplicar la fórmula `2^h - 2` donde `h` es el número de bits de host.

**4.2.** Si tienes la red `192.168.5.0/26`, ¿cuáles son las 4 primeras subredes posibles?  

📌 **Respuesta esperada:** Dividir en **bloques de 64 direcciones**.

---

## **🔹 Sección 5: Direcciones IPv4 Especiales**
**5.1.** ¿Qué función tienen estas direcciones?  
a) `127.0.0.1`  
b) `169.254.1.50`  
c) `0.0.0.0`  
d) `255.255.255.255`  

📌 **Respuesta esperada:** Indicar **Loopback, Enlace local, Default Route o Broadcast**.

---

## **🔹 Sección 6: IPv6 - Prefijos y Representación**
**6.1.** ¿Qué tipo de dirección IPv6 es cada una?  
a) `2001:db8::1`  
b) `FE80::1`  
c) `FF02::1`  
d) `::1`  

📌 **Respuesta esperada:** **Unicast Global, Enlace Local, Multicast o Loopback**.

**6.2.** Escribe en **forma abreviada** las siguientes direcciones IPv6:  
a) `2001:0db8:0000:0000:0000:0000:0000:0001`  
b) `FE80:0000:0000:0000:0200:5AFF:FEA7:521C`  
c) `FF01:0000:0000:0000:0000:0000:0000:101`  

📌 **Respuesta esperada:** Usar **notación `::` para omitir ceros**.

---

## **🔹 Sección 7: Migración IPv4 - IPv6**
**7.1.** ¿Cuál de los siguientes métodos permite la coexistencia de IPv4 e IPv6?  
a) **Pila Dual**  
b) **Traducción NAT64**  
c) **Túneles**  
d) **Todas las anteriores**  

📌 **Respuesta esperada:** Explicar **cómo funciona cada método**.

**7.2.** Convierte la IPv4 `192.168.1.1` a su equivalente IPv6 en formato **mapped IPv6 address**.  

📌 **Respuesta esperada:** `::FFFF:192.168.1.1`

---

## **🔹 Sección 8: Redes y Subredes**
**8.1.** Dos ordenadores tienen estas direcciones:  
- **PC1:** `192.168.1.100 /27`  
- **PC2:** `192.168.1.129 /27`  

📌 **¿Están en la misma red?** **Justifica tu respuesta.**  

**8.2.** Un router tiene una dirección IP pública `200.150.10.1 /28`.  
📌 **¿Cuántas direcciones pueden asignarse a dispositivos dentro de esta subred?**  

---

### 🎯 **¿Cómo usar este apartado?**
✅ **Intenta responder cada pregunta sin mirar los apuntes.**
✅ **Haz los cálculos en papel, sobre todo las operaciones en binario.**
✅ **Si fallas en una pregunta, revisa el resumen en esa sección.**

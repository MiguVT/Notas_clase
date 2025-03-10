### 📖 **Introducción al Cuaderno (Ejercicios) de Redes** 📖  

Este cuaderno ha sido elaborado como un **libro de estudio estructurado**, con un enfoque claro y técnico. Su objetivo es proporcionar un recurso preciso y bien organizado para el aprendizaje del **direccionamiento IP y redes**.  

El contenido sigue un **estilo formal y técnico**, evitando un tono excesivamente coloquial, para asemejarse más a un **manual de referencia**. Se presentan **explicaciones detalladas**, ejercicios resueltos y cálculos paso a paso, asegurando una comprensión profunda de cada concepto.  

Este documento está diseñado tanto para el **estudio personal** como para servir de **guía en futuras consultas**.

# 13/01/25
## Ejercicio 2
Mi ip: 192.168.31.43

## Ejercicio 3
- a) 12.45.56.78 ➜ Clase A
- b) 111.222.111.222 ➜ Clase A
- c) 222.125.1.1 ➜ Clase C
- d) 172.14.5.1 ➜ Clase B
- e) 172.35.1.1 ➜ Clase B
- f) 10.20.30.40 ➜ Clase A
- g) 1.2.3.4 ➜ Clase A

## Ejercicio A.7.4: Averiguar la dirección de red

### **a) 188.10.18.2 / 255.255.0.0**
#### Cálculo en binario:
```
188.10.18.2   -> 10111100.00001010.00010010.00000010
255.255.0.0   -> 11111111.11111111.00000000.00000000
Resultado      -> 10111100.00001010.00000000.00000000 (188.10.0.0)
```
**Dirección de Red:** 188.10.0.0

---

### **b) 192.149.24.191 / 255.255.255.0**
#### Cálculo en binario:
```
192.149.24.191 -> 11000000.10010101.00011000.10111111
255.255.255.0  -> 11111111.11111111.11111111.00000000
Resultado       -> 11000000.10010101.00011000.00000000 (192.149.24.0)
```
**Dirección de Red:** 192.149.24.0

---

### **c) 10.10.48.80 / 255.255.255.0**
#### Cálculo en binario:
```
10.10.48.80   -> 00001010.00001010.00110000.01010000
255.255.255.0 -> 11111111.11111111.11111111.00000000
Resultado      -> 00001010.00001010.00110000.00000000 (10.10.48.0)
```
**Dirección de Red:** 10.10.48.0

---

### **d) 150.203.23.19 / 255.255.0.0**
#### Cálculo en binario:
```
150.203.23.19 -> 10010110.11001011.00010111.00010011
255.255.0.0   -> 11111111.11111111.00000000.00000000
Resultado      -> 10010110.11001011.00000000.00000000 (150.203.0.0)
```
**Dirección de Red:** 150.203.0.0


# 16/01/25
## Ejercicio 1: Cálculo de dirección de red y broadcast

### **a) 18.120.16.250**
- Máscara por defecto: 255.0.0.0
#### Cálculo en binario:
```
18.120.16.250 -> 00010010.01111000.00010000.11111010
255.0.0.0      -> 11111111.00000000.00000000.00000000
Resultado red  -> 00010010.00000000.00000000.00000000 (18.0.0.0)
Resultado bcast-> 00010010.11111111.11111111.11111111 (18.255.255.255)
```
**Dirección de Red:** 18.0.0.0
**Dirección de Broadcast:** 18.255.255.255

---

### **b) 18.120.16.255 / 255.255.0.0**
#### Cálculo en binario:
```
18.120.16.255 -> 00010010.01111000.00010000.11111111
255.255.0.0    -> 11111111.11111111.00000000.00000000
Resultado red  -> 00010010.01111000.00000000.00000000 (18.120.0.0)
Resultado bcast-> 00010010.01111000.11111111.11111111 (18.120.255.255)
```
**Dirección de Red:** 18.120.0.0
**Dirección de Broadcast:** 18.120.255.255

---

### **c) 155.4.220.39**
- Máscara por defecto: 255.255.0.0
#### Cálculo en binario:
```
155.4.220.39  -> 10011011.00000100.11011100.00100111
255.255.0.0    -> 11111111.11111111.00000000.00000000
Resultado red  -> 10011011.00000100.00000000.00000000 (155.4.0.0)
Resultado bcast-> 10011011.00000100.11111111.11111111 (155.4.255.255)
```
**Dirección de Red:** 155.4.0.0
**Dirección de Broadcast:** 155.4.255.255

---

### **d) 194.209.14.33**
- Máscara por defecto: 255.255.255.0
#### Cálculo en binario:
```
194.209.14.33 -> 11000010.11010001.00001110.00100001
255.255.255.0 -> 11111111.11111111.11111111.00000000
Resultado red  -> 11000010.11010001.00001110.00000000 (194.209.14.0)
Resultado bcast-> 11000010.11010001.00001110.11111111 (194.209.14.255)
```
**Dirección de Red:** 194.209.14.0
**Dirección de Broadcast:** 194.209.14.255

---

### **e) 190.33.109.133 / 255.255.255.0**
#### Cálculo en binario:
```
190.33.109.133 -> 10111110.00100001.01101101.10000101
255.255.255.0  -> 11111111.11111111.11111111.00000000
Resultado red  -> 10111110.00100001.01101101.00000000 (190.33.109.0)
Resultado bcast-> 10111110.00100001.01101101.11111111 (190.33.109.255)
```
**Dirección de Red:** 190.33.109.0
**Dirección de Broadcast:** 190.33.109.255

---

## Ejercicio 2: IP de red y broadcast
#### Estos ejercicios son del Word en el aula virtual llamado "Ejercicios sobre Ips"
### **a) 11.2.3.78 / 8**
#### Cálculo en binario:
```
11.2.3.78 -> 00001011.00000010.00000011.01001110
/8        -> 11111111.00000000.00000000.00000000
Red        -> 00001011.00000000.00000000.00000000 (11.0.0.0)
Broadcast   -> 00001011.11111111.11111111.11111111 (11.255.255.255)
```
**IP de Red:** 11.0.0.0
**Broadcast:** 11.255.255.255

---

### **b) 152.63.98.45 / 16**
#### Cálculo en binario:
```
152.63.98.45 -> 10011000.00111111.01100010.00101101
/16          -> 11111111.11111111.00000000.00000000
Red           -> 10011000.00111111.00000000.00000000 (152.63.0.0)
Broadcast      -> 10011000.00111111.11111111.11111111 (152.63.255.255)
```
**IP de Red:** 152.63.0.0
**Broadcast:** 152.63.255.255

---

### **c) 222.222.253.56 / 24**
#### Cálculo en binario:
```
222.222.253.56 -> 11011110.11011110.11111101.00111000
/24            -> 11111111.11111111.11111111.00000000
Red             -> 11011110.11011110.11111101.00000000 (222.222.253.0)
Broadcast        -> 11011110.11011110.11111101.11111111 (222.222.253.255)
```
**IP de Red:** 222.222.253.0
**Broadcast:** 222.222.253.255

---

### **d) 192.168.52.34 / 24**
#### Cálculo en binario:
```
192.168.52.34 -> 11000000.10101000.00110100.00100010
/24           -> 11111111.11111111.11111111.00000000
Red            -> 11000000.10101000.00110100.00000000 (192.168.52.0)
Broadcast       -> 11000000.10101000.00110100.11111111 (192.168.52.255)
```
**IP de Red:** 192.168.52.0
**Broadcast:** 192.168.52.255

---

### **e) 129.23.56.65 / 16**
#### Cálculo en binario:
```
129.23.56.65 -> 10000001.00010111.00111000.01000001
/16          -> 11111111.11111111.00000000.00000000
Red           -> 10000001.00010111.00000000.00000000 (129.23.0.0)
Broadcast      -> 10000001.00010111.11111111.11111111 (129.23.255.255)
```
**IP de Red:** 129.23.0.0
**Broadcast:** 129.23.255.255

---

### **f) 1.1.1.1 / 8**
#### Cálculo en binario:
```
1.1.1.1 -> 00000001.00000001.00000001.00000001
/8      -> 11111111.00000000.00000000.00000000
Red      -> 00000001.00000000.00000000.00000000 (1.0.0.0)
Broadcast -> 00000001.11111111.11111111.11111111 (1.255.255.255)
```
**IP de Red:** 1.0.0.0
**Broadcast:** 1.255.255.255

---

## Ejercicio 3: Dirección de red y broadcast con subredes específicas

### **a) 190.33.109.133 / 255.255.255.128**
#### Cálculo en binario:
```
190.33.109.133 -> 10111110.00100001.01101101.10000101
255.255.255.128-> 11111111.11111111.11111111.10000000
Red             -> 10111110.00100001.01101101.10000000 (190.33.109.128)
Broadcast        -> 10111110.00100001.01101101.11111111 (190.33.109.255)
```
**Dirección de Red:** 190.33.109.128
**Broadcast:** 190.33.109.255

---

### **b) 192.168.20.25 / 255.255.255.240**
#### Cálculo en binario:
```
192.168.20.25 -> 11000000.10101000.00010100.00011001
255.255.255.240-> 11111111.11111111.11111111.11110000
Red             -> 11000000.10101000.00010100.00010000 (192.168.20.16)
Broadcast        -> 11000000.10101000.00010100.00011111 (192.168.20.31)
```
**Dirección de Red:** 192.168.20.16
**Broadcast:** 192.168.20.31

---

### **c) 192.168.20.25 / 255.255.255.224**
#### Cálculo en binario:
```
192.168.20.25 -> 11000000.10101000.00010100.00011001
255.255.255.224-> 11111111.11111111.11111111.11100000
Red             -> 11000000.10101000.00010100.00000000 (192.168.20.0)
Broadcast        -> 11000000.10101000.00010100.00011111 (192.168.20.31)
```
**Dirección de Red:** 192.168.20.0
**Broadcast:** 192.168.20.31

---

### **d) 140.190.20.10 / 255.255.192.0**
#### Cálculo en binario:
```
140.190.20.10 -> 10001100.10111110.00010100.00001010
255.255.192.0 -> 11111111.11111111.11000000.00000000
Red             -> 10001100.10111110.00000000.00000000 (140.190.0.0)
Broadcast        -> 10001100.10111110.00111111.11111111 (140.190.63.255)
```
**Dirección de Red:** 140.190.0.0
**Broadcast:** 140.190.63.255

---

### **e) 140.190.130.10 / 255.255.192.0**
#### Cálculo en binario:
```
140.190.130.10 -> 10001100.10111110.10000010.00001010
255.255.192.0  -> 11111111.11111111.11000000.00000000
Red             -> 10001100.10111110.10000000.00000000 (140.190.128.0)
Broadcast        -> 10001100.10111110.10111111.11111111 (140.190.191.255)
```
**Dirección de Red:** 140.190.128.0
**Broadcast:** 140.190.191.255

---

### **f) 140.190.220.10 / 255.255.192.0**
#### Cálculo en binario:
```
140.190.220.10 -> 10001100.10111110.11011100.00001010
255.255.192.0  -> 11111111.11111111.11000000.00000000
Red             -> 10001100.10111110.11000000.00000000 (140.190.192.0)
Broadcast        -> 10001100.10111110.11111111.11111111 (140.190.255.255)
```
**Dirección de Red:** 140.190.192.0
**Broadcast:** 140.190.255.255

---


## Ejercicio 4: Cálculo de dirección de red, broadcast y máscara

### **Rango de IPs: 194.143.17.145 - 194.143.17.158**
#### Observaciones:
- El rango está contenido dentro de una subred. Las direcciones van desde 145 hasta 158, lo cual implica que la subred tiene capacidad para cubrir estas IPs.
- Se buscará la máscara más ajustada que incluya ambas direcciones.

#### Paso 1: Convertir las direcciones IP a binario
```
194.143.17.145 -> 11000010.10001111.00010001.10010001
194.143.17.158 -> 11000010.10001111.00010001.10011110
```

#### Paso 2: Encontrar la dirección de red
- Para hallar la dirección de red, realizamos una operación AND entre las direcciones en binario considerando la parte común.
```
194.143.17.145 -> 11000010.10001111.00010001.10010001
194.143.17.158 -> 11000010.10001111.00010001.10011110
Red             -> 11000010.10001111.00010001.10010000 (194.143.17.144)
```

#### Paso 3: Encontrar la dirección de broadcast
- Para hallar la dirección de broadcast, completamos con unos el resto de la subred.
```
Broadcast       -> 11000010.10001111.00010001.10011111 (194.143.17.159)
```

#### Paso 4: Determinar la máscara de subred
- La máscara debe incluir las IPs del rango sin exceder. Se observa que el rango pertenece a una subred con máscara de /28 (255.255.255.240).
```
Máscara        -> 11111111.11111111.11111111.11110000 (255.255.255.240)
```

#### Resumen:
**Dirección de Red:** 194.143.17.144  
**Broadcast:** 194.143.17.159  
**Máscara:** 255.255.255.240



### **21/01/25**

## **Ejercicio 1: Red con IP 172.175.12.2 /22**

### a) Máscara de red en notación decimal y binario:
- **Notación Decimal Puntuada:** 255.255.252.0  
- **Binario:** `11111111.11111111.11111100.00000000`

### b) Dirección de red:
```
IP:           172.175.12.2   -> 10101100.10101111.00001100.00000010
Máscara:      255.255.252.0  -> 11111111.11111111.11111100.00000000
Resultado:    172.175.12.0   -> 10101100.10101111.00001100.00000000
```
**Dirección de red:** 172.175.12.0

### c) Dirección de difusión:
```
Dirección de red:   172.175.12.0 -> 10101100.10101111.00001100.00000000
Complemento máscara: 0.0.3.255   -> 00000000.00000000.00000011.11111111
Resultado difusión: 172.175.15.255 -> 10101100.10101111.00001111.11111111
```
**Dirección de difusión:** 172.175.15.255

### d) Dirección 172.175.14.0, ¿es válida en la misma red?
La red **172.175.12.0/22** tiene un rango de direcciones:
- Desde: **172.175.12.1**  
- Hasta: **172.175.15.254**  

**Conclusión:** La dirección **172.175.14.0** está dentro del rango, por lo que **sí es válida**.

---

## **Ejercicio 2: Máscara para 192.168.43.3 y 192.168.5.23**

### Cálculo:
#### Binario de las IPs:
```
192.168.43.3 ->  11000000.10101000.00101011.00000011
192.168.5.23 ->  11000000.10101000.00000101.00010111
```
Los primeros **16 bits** son comunes (`192.168`), por lo que usamos una máscara **/16**.

### Resultado:
- **Máscara:** 255.255.0.0 (/16)
- **Dirección de red:** 192.168.0.0
- **Broadcast:** 192.168.255.255
- **Número máximo de dispositivos:** \( 2^{16} - 2 = 65,534 \).

---

## **Ejercicio 3: Clase y tipo de las direcciones**

### a) 12.45.56.78
- **Clase:** A (primer octeto: 12 → 0-127)  
- **Tipo:** Pública  

### b) 111.222.111.222
- **Clase:** A (primer octeto: 111 → 0-127)  
- **Tipo:** Pública  

### c) 222.125.1.1
- **Clase:** C (primer octeto: 222 → 192-223)  
- **Tipo:** Pública  

### d) 172.14.5.1
- **Clase:** B (primer octeto: 172 → 128-191)  
- **Tipo:** Pública  

### e) 172.35.1.1
- **Clase:** B (primer octeto: 172 → 128-191)  
- **Tipo:** Pública  

### f) 10.20.30.40
- **Clase:** A (primer octeto: 10 → 0-127)  
- **Tipo:** Privada (rango reservado: 10.0.0.0 - 10.255.255.255)  

### g) 1.2.3.4
- **Clase:** A (primer octeto: 1 → 0-127)  
- **Tipo:** Pública


### **22/01/25**

## **Ejercicio 2: Comprueba si las siguientes parejas de ordenadores están en la misma red**

### **a) 172.120.34.78 /21 y 172.120.60.30 /21**

#### Máscara de red:
- **Notación decimal:** 255.255.248.0  
- **Binario:** `11111111.11111111.11111000.00000000`

#### Dirección de red:
- **172.120.34.78**
  - IP: `172.120.34.78`  
  - Máscara: `255.255.248.0`  
  - Dirección de red: **172.120.32.0**

- **172.120.60.30**
  - IP: `172.120.60.30`  
  - Máscara: `255.255.248.0`  
  - Dirección de red: **172.120.56.0**

#### Conclusión:
- **No están en la misma red**, ya que:  
  - Red 1: **172.120.32.0/21**  
  - Red 2: **172.120.56.0/21**

---

### **b) 192.168.1.130 /27 y 192.168.1.160 /27**

#### Máscara de red:
- **Notación decimal:** 255.255.255.224  
- **Binario:** `11111111.11111111.11111111.11100000`

#### Dirección de red:
- **192.168.1.130**
  - IP: `192.168.1.130`  
  - Máscara: `255.255.255.224`  
  - Dirección de red: **192.168.1.128**

- **192.168.1.160**
  - IP: `192.168.1.160`  
  - Máscara: `255.255.255.224`  
  - Dirección de red: **192.168.1.160**

#### Conclusión:
- **No están en la misma red**, ya que:  
  - Red 1: **192.168.1.128/27**  
  - Red 2: **192.168.1.160/27**

---

### **c) 20.10.1.152 /6 y 30.100.212.122 /6**

#### Máscara de red:
- **Notación decimal:** 252.0.0.0  
- **Binario:** `11111100.00000000.00000000.00000000`

#### Dirección de red:
- **20.10.1.152**
  - IP: `20.10.1.152`  
  - Máscara: `252.0.0.0`  
  - Dirección de red: **20.0.0.0**

- **30.100.212.122**
  - IP: `30.100.212.122`  
  - Máscara: `252.0.0.0`  
  - Dirección de red: **28.0.0.0**

#### Conclusión:
- **No están en la misma red**, ya que:  
  - Red 1: **20.0.0.0/6**  
  - Red 2: **28.0.0.0/6**

---

### **04/02/25**  

## **Ejercicio 1: Análisis de configuración de una red**  

Un cliente tiene la siguiente configuración de red:  

- **Dirección IP:** `192.168.3.1`  
- **Máscara de subred:** `255.255.254.0`  
- **Puerta de Enlace:** `192.168.1.1`  
- **DNS Primario:** `8.8.8.8`  
- **DNS Secundario:** `4.4.4.4`  

---

### **a) ¿Se podrá comunicar con un PC con IP `192.169.3.2` y la misma máscara de subred?**  

#### **Paso 1: Identificar la red de la IP `192.168.3.1`**  
Máscara en binario:  
```plaintext
255.255.254.0 → 11111111.11111111.11111110.00000000
```
Red a la que pertenece `192.168.3.1`:  
```plaintext
192.168.2.0/23
```
Rango de direcciones válidas:  
```plaintext
192.168.2.1 - 192.168.3.254
```

#### **Paso 2: Identificar la red de la IP `192.169.3.2`**  
Máscara en binario:  
```plaintext
255.255.254.0 → 11111111.11111111.11111110.00000000
```
Red a la que pertenece `192.169.3.2`:  
```plaintext
192.169.2.0/23
```

✅ **Conclusión:**  
Las direcciones `192.168.3.1` y `192.169.3.2` pertenecen a **redes diferentes**, por lo que **no pueden comunicarse directamente**.  

🔧 **Solución:**  
1. **Cambiar la IP de uno de los equipos** para que pertenezca a la misma red (`192.168.2.X` o `192.169.2.X`).  
2. **Cambiar la dirección de red para que ambas IPs pertenezcan a la misma subred.**  

---

### **Solución alternativa: Cambiar la dirección de red**  

Queremos encontrar la **máscara de subred más grande posible** que incluya **ambas direcciones IP (`192.168.3.1` y `192.169.3.2`)**.  

#### **Paso 1: Convertir las direcciones IP a binario**  

IP `192.168.3.1`:  
```plaintext
11000000.10101000.00000011.00000001
```
IP `192.169.3.2`:  
```plaintext
11000000.10101001.00000011.00000010
```
Observamos que los **primeros 23 bits no son iguales**.  

#### **Paso 2: Buscar la máscara adecuada**  

- Si usamos una máscara **/22** (`255.255.252.0`), la dirección de red sería:  
  ```plaintext
  192.168.0.0/22 (cubre de 192.168.0.0 a 192.168.3.255)
  ```
  → **No cubre la IP `192.169.3.2`**.

- Si usamos una máscara **/21** (`255.255.248.0`), la dirección de red sería:  
  ```plaintext
  192.168.0.0/21 (cubre de 192.168.0.0 a 192.168.7.255)
  ```
  → **No cubre la IP `192.169.3.2`**.

- Si usamos una máscara **/20** (`255.255.240.0`), la dirección de red sería:  
  ```plaintext
  192.160.0.0/20 (cubre de 192.160.0.0 a 192.175.255.255)
  ```
  → **Ahora ambas direcciones están en la misma red**.

✅ **Solución final:**  
- **Dirección de red:** `192.160.0.0/20`  
- **Máscara de subred:** `255.255.240.0`  
- **Nueva puerta de enlace recomendada:** `192.160.0.1`  

---

### **b) ¿Podrá navegar por Internet normalmente?**  

Para navegar en Internet, la **puerta de enlace** debe estar en la misma red.  

- **IP:** `192.168.3.1` pertenece a la red **`192.168.2.0/23`**.  
- **Puerta de enlace:** `192.168.1.1` pertenece a la red **`192.168.0.0/23`**.  

✅ **Conclusión:**  
La IP del PC y la **puerta de enlace no están en la misma red**, por lo que **no podrá salir a Internet**.  

🔧 **Solución:**  
- Cambiar la puerta de enlace a **`192.168.3.254`** (última IP válida en la red `192.168.2.0/23`).  
- Si se aplica la solución alternativa con **máscara /20**, la puerta de enlace debería cambiarse a `192.160.0.1`.

---

### **c) ¿Podrá navegar si el DNS primario `8.8.8.8` está apagado?**  

Los **servidores DNS** convierten nombres de dominio en direcciones IP.  

- Si el **DNS primario (`8.8.8.8`)** está apagado, el sistema usará el **DNS secundario (`4.4.4.4`)**.  
- Si **ambos están caídos**, no podrá resolver nombres de dominio, pero **sí podrá acceder a Internet si usa direcciones IP directamente**.  

✅ **Conclusión:**  
Podrá navegar **siempre que el DNS secundario (`4.4.4.4`) funcione**. Si ambos fallan, solo podrá acceder a sitios mediante sus direcciones IP.

---

## **Ejercicio 2: Análisis de puertos en una trama de red**  

Los **puertos TCP/UDP** están en el rango **0 - 65535** y se dividen en tres categorías:  

1. **Puertos Bien Conocidos (Well-Known Ports) [0 - 1023]**  
   - Reservados para servicios estándar como **HTTP (`80`)**, **HTTPS (`443`)**, **SSH (`22`)**, etc.  

2. **Puertos Registrados (Registered Ports) [1024 - 49151]**  
   - Asignados a aplicaciones específicas por **IANA**, como **MySQL (`3306`)**, **Minecraft (`25565`)**, etc.  

3. **Puertos Dinámicos o Efímeros (Dynamic or Ephemeral Ports) [49152 - 65535]**  
   - Asignados **temporalmente** por el sistema a clientes cuando establecen conexiones de salida (ejemplo: al navegar en Internet).

✅ **Clasificación en los puertos:**  

| **Puerto** | **Clasificación** | **Es válido?** |
|------------|------------------|---------------|
| **100** | **Bien conocido (0-1023)** | ✅ **Sí** |
| **300** | **Bien conocido (0-1023)** | ✅ **Sí** |
| **45065** | **Registrado (1024-49151)** | ✅ **Sí** |
| **69830** | **Fuera de rango (máximo permitido 65535)** | ❌ **No** |

## **Ejercicio 3: Análisis de una IP con máscara /27**  

Dada la dirección IP **192.133.14.33/27**, respondemos a las siguientes preguntas.  

---

### **a) ¿Es una IP pública o privada?**  

📌 **Reglas de direcciones privadas:**  
Las direcciones privadas están en los siguientes rangos:  

- **Clase A:** `10.0.0.0 - 10.255.255.255`  
- **Clase B:** `172.16.0.0 - 172.31.255.255`  
- **Clase C:** `192.168.0.0 - 192.168.255.255`  

🔍 **Análisis:**  
- La IP **192.133.14.33** **NO** está en ninguno de los rangos anteriores.  
- Por lo tanto, **es una IP pública**.  

✅ **Respuesta:** **IP pública**  

---

### **b) Máscara en notación decimal puntuada**  

📌 **Conversión de `/27` a notación decimal:**  

En binario, una máscara **/27** tiene 27 bits en `1`:  
```plaintext
11111111.11111111.11111111.11100000
```
En decimal:  
```plaintext
255.255.255.224
```

✅ **Respuesta:** `255.255.255.224`  

---

### **c) Dirección de red**  

📌 **La dirección de red se obtiene haciendo una operación AND entre la IP y la máscara de subred.**  

**Paso 1: Convertir a binario**  
```plaintext
IP:      192.133.14.33  ->  11000000.10000101.00001110.00100001
Máscara: 255.255.255.224 ->  11111111.11111111.11111111.11100000
```

**Paso 2: Aplicar AND bit a bit**  
```plaintext
Red:     192.133.14.32  ->  11000000.10000101.00001110.00100000
```

✅ **Dirección de red:** `192.133.14.32`  

---

### **d) Dirección de difusión**  

📌 **La dirección de difusión (broadcast) se obtiene poniendo todos los bits de host en `1` dentro del rango de la subred.**  

**Paso 1: Complemento de la máscara**  
```plaintext
00000000.00000000.00000000.00011111
```

**Paso 2: Aplicar OR con la dirección de red**  
```plaintext
192.133.14.32  |  0.0.0.31  =  192.133.14.63
```

✅ **Dirección de difusión:** `192.133.14.63`  

---

### **e) Número máximo de ordenadores en la red**  

📌 **Fórmula para calcular hosts en una subred:**  
```plaintext
(2^bits_de_host) - 2
```
- `/27` significa que hay **5 bits para los hosts** (`32 - 27 = 5`).  
- **Número de hosts posibles:**  
  ```plaintext
  (2^5) - 2 = 32 - 2 = 30 hosts
  ```

✅ **Máximo número de ordenadores en la red:** **30**  

---

### **f) ¿Está en la misma red que la máquina `192.133.14.67`?**  

📌 **Paso 1: Encontrar la dirección de red de `192.133.14.67` con máscara `/27`**  

**Conversión a binario**  
```plaintext
192.133.14.67  ->  11000000.10000101.00001110.01000011
```

**Aplicando la máscara `/27` (AND con `255.255.255.224`)**  
```plaintext
192.133.14.67  &  255.255.255.224  =  192.133.14.64
```

📌 **Comparación de direcciones de red**  
| IP | Dirección de Red |
|----|-----------------|
| `192.133.14.33` | `192.133.14.32` |
| `192.133.14.67` | `192.133.14.64` |

**Diferentes redes.**  

✅ **Respuesta:** **No están en la misma red** porque pertenecen a redes diferentes:  
- `192.133.14.32/27`  
- `192.133.14.64/27`  

---

### **Resultados**  

| Pregunta | Respuesta |
|----------|----------|
| **a) Pública o privada?** | Pública |
| **b) Máscara en decimal?** | `255.255.255.224` |
| **c) Dirección de red?** | `192.133.14.32` |
| **d) Dirección de difusión?** | `192.133.14.63` |
| **e) Máximo número de ordenadores?** | `30` |
| **f) ¿Misma red que `192.133.14.67`?** | **No**, `192.133.14.67` está en `192.133.14.64/27` |


### **06/02/25**  

## **Ejercicio 1: Direccionamiento IP en un escenario de red**  

Dado el esquema de red, se han configurado **tres redes de clase C** dentro del rango `192.168.0.0 - 192.168.255.255`, utilizando la **máscara por defecto `255.255.255.0 (/24)`**.  

---

### **a) Direcciones de red, broadcast y rango de direcciones**  

Cada subred con máscara `/24` tiene:  
- **Dirección de red**: `XXX.XXX.XXX.0`  
- **Dirección de broadcast**: `XXX.XXX.XXX.255`  
- **Rango de direcciones utilizables**: `XXX.XXX.XXX.1 - XXX.XXX.XXX.254`  

✅ **Asignación de subredes**  

| **Subred** | **Dirección de Red** | **Dirección de Broadcast** | **Rango de IPs** |
|-----------|----------------|------------------|-----------------------|
| **Red 1** | `192.168.1.0` | `192.168.1.255` | `192.168.1.1 - 192.168.1.254` |
| **Red 2** | `192.168.2.0` | `192.168.2.255` | `192.168.2.1 - 192.168.2.254` |
| **Red 3** | `192.168.3.0` | `192.168.3.255` | `192.168.3.1 - 192.168.3.254` |

---

### **b) Direcciones IP de cada máquina y del router**  

📌 **Suposición**:  
- Cada red tiene un **switch** y se conectan a un **router** que permite la comunicación entre ellas.  
- Asignamos la primera IP disponible (`.1`) al **router** de cada red.  

✅ **Asignación de direcciones IP**  

| **Dispositivo** | **IP Asignada** | **Máscara (CIDR)** | **Gateway** |
|--------------|-------------|--------------|--------------|
| **Router - Red 1** | `192.168.1.1` | `/24` | |
| **PC1** | `192.168.1.2` | `/24` | `192.168.1.1` |
| **PC2** | `192.168.1.3` | `/24` | `192.168.1.1` |
| **PC3** | `192.168.1.4` | `/24` | `192.168.1.1` |
| **PC4** | `192.168.1.5` | `/24` | `192.168.1.1` |
| **Router - Red 2** | `192.168.2.1` | `/24` |
| **PC5** | `192.168.2.2` | `/24` | `192.168.2.1` |
| **PC6** | `192.168.2.3` | `/24` | `192.168.2.1` |
| **PC7** | `192.168.2.4` | `/24` | `192.168.2.1` |
| **PC8** | `192.168.2.5` | `/24` | `192.168.2.1` |
| **Router - Red 3** | `192.168.3.1` | `/24` |
| **PC9** | `192.168.3.2` | `/24` | `192.168.3.1` |
| **PC10** | `192.168.3.3` | `/24` | `192.168.3.1` |
| **PC11** | `192.168.3.4` | `/24` | `192.168.3.1` |
| **PC12** | `192.168.3.5` | `/24` | `192.168.3.1` |

📌 **Nota:**  
Cada PC tiene asignada una IP dentro del rango **válido** de su subred y la puerta de enlace para cada subred es la dirección del **router** correspondiente (`.1`).  

### **12/02/25**  

## **2: La orden `ipconfig/ifconfig`**  

Las órdenes `ipconfig` (Windows) e `ifconfig` (Linux) proporcionan información sobre la configuración de la red de la máquina, incluyendo direcciones IP, máscaras de subred y puertas de enlace.  

---

### **Ejercicio 2.1**  

📌 **Salida de `ipconfig` y datos extraídos:**  

| **Parámetro** | **Valor obtenido** |
|--------------|------------------|
| **Dirección física del adaptador Ethernet** | `7C-10-C9-83-AA-1B` |
| **Dirección IP** | `192.168.5.13` |
| **Máscara de subred** | `255.255.240.0` |
| **Dirección IP del router (puerta de enlace)** | `192.168.0.99` |
| **Servidor DNS** | `192.168.0.99` |
| **Servidor DHCP** | **No habilitado** (configuración manual) |

---

### **Ejercicio 2.2**  

📌 **¿Qué información no se podría obtener con `ifconfig` en Linux?**  

El comando `ifconfig` en Linux **no muestra**:  
- **Dirección IP del router (puerta de enlace)**  
- **Servidor DNS**  
- **Servidor DHCP**  

📌 **¿Cómo encontrar esta información en Linux?**  

Para obtener estos datos en Linux, se utilizan los siguientes comandos:  

- **Puerta de enlace predeterminada (router):**  
  ```bash
  ip route show | grep default
  ```
  
- **Servidores DNS configurados:**  
  ```bash
  cat /etc/resolv.conf
  ```

- **Servidor DHCP asignado:**  
  ```bash
  journalctl -u NetworkManager | grep DHCP
  ```

---

## **Ejercicio 2.2: Alternativa sin `net-tools` en Ubuntu 20+**  

Desde Ubuntu 20.04 en adelante, el paquete `net-tools` (que incluye `ifconfig`) **no viene preinstalado** y ha sido reemplazado por `ip` y `nmcli`.  

📌 **Alternativas modernas para obtener la misma información:**  

| **Parámetro** | **`ifconfig` (antiguo)** | **Alternativa moderna** |
|--------------|----------------|----------------------|
| **Dirección IP** | `ifconfig` | `ip addr show` |
| **Máscara de subred** | `ifconfig` | `ip -4 addr show` |
| **Dirección MAC (física)** | `ifconfig` | `ip link show` |
| **Puerta de enlace (router)** | `route -n` | `ip route show \| grep default` |
| **Servidores DNS** | `/etc/resolv.conf` | `systemd-resolve --status` o `nmcli dev show` |
| **Servidor DHCP** | `dhclient -v` | `journalctl -u NetworkManager \| grep DHCP` |

---

### **📌 Comandos equivalentes en Ubuntu 20+**  

1️⃣ **Ver IP, máscara de subred y MAC:**  
```bash
ip addr show
```

2️⃣ **Ver la puerta de enlace predeterminada:**  
```bash
ip route show | grep default
```

3️⃣ **Ver servidores DNS en uso:**  
```bash
systemd-resolve --status | grep 'DNS Servers'
```
o alternativamente:  
```bash
nmcli dev show | grep 'IP4.DNS'
```

4️⃣ **Ver información de DHCP:**  
```bash
journalctl -u NetworkManager | grep DHCP
```

---

✅ **Conclusión:**  
- `ifconfig` y `route` **han sido reemplazados** por `ip` y `nmcli` en sistemas modernos.  
- Ubuntu 20+ **ya no incluye `net-tools` por defecto**, por lo que se recomienda **usar los nuevos comandos** para obtener información de red.  

---

## **Ejercicio 3.1: Configuración de `ping` en Ubuntu y Windows**  

El comando `ping` permite enviar solicitudes de eco a una dirección IP para comprobar la conectividad por el protocolo **ICMP**.

---

### **📌 En Ubuntu (Linux)**  

Para enviar **10 paquetes de ping** con un **intervalo de 2 segundos** entre cada solicitud, se usa:  

- **Comando:**  
  ```bash
  ping -c 10 -i 2 <IP_PUERTA_DE_ENLACE>
  ```
  
📌 **Explicación de opciones:**  
- `-c 10` → Envía **10 paquetes**.  
- `-i 2` → Intervalo de **2 segundos** entre cada solicitud.  

✅ **Ejemplo real:** Si la puerta de enlace es `192.168.1.1`:  
```bash
ping -c 10 -i 2 192.168.1.1
```

---

### **📌 En Windows (`cmd` o `PowerShell`)**  

En Windows, el comando `ping` usa una sintaxis diferente:  

- **Comando:**  
  ```cmd
  ping -n 10 -w 2000 <IP_PUERTA_DE_ENLACE>
  ```
  
📌 **Explicación de opciones:**  
- `-n 10` → Envía **10 paquetes**.  
- `-w 2000` → Espera **2000 milisegundos (2 segundos)** entre cada solicitud.  

✅ **Ejemplo real:**  
```cmd
ping -n 10 -w 2000 192.168.1.1
```

---

### **📌 Conclusión**  
- **Sí, se puede realizar la misma acción en Windows y Linux**, pero la sintaxis varía.  
- En **Ubuntu**, el intervalo se define con `-i`, mientras que en **Windows** se usa `-w` en milisegundos.

---

## **Ejercicio 4.3: Uso de `tracert`/`traceroute`**  

El comando `tracert` (Windows) o `traceroute` (Linux) permite analizar la ruta que siguen los paquetes hasta un destino determinado, mostrando los **saltos intermedios** entre el origen y el destino.  

---

### **Resultados obtenidos**  

| **Destino** | **Número de saltos** | **Observaciones** |
|-------------|----------------------|--------------------|
| `www.google.es` | **10 saltos** | Un salto con *timeout*, pero la traza llega al destino. |
| `www.us.es` | **14 saltos** | Varios saltos con *timeout*, pero la traza llega al destino. |
| `www.net.princeton.edu` | **23 saltos** | Múltiples *timeouts*, pero la traza llega al destino. |

---

### **Análisis del comportamiento de `tracert www.us.es`**  

Durante la ejecución del `tracert` a `www.us.es`, se observaron varios **saltos intermedios con "Tiempo de espera agotado"** (`* * *` en la salida).  

🔍 **Posibles causas de los *timeouts***:  
1. **Filtros de seguridad**: Algunos routers o firewalls pueden **bloquear respuestas ICMP**, lo que impide que ciertos saltos respondan al `tracert`.  
2. **Política de la red de destino**: Algunas organizaciones, como podria ser Jesuitas, pueden **restringir la visibilidad de su infraestructura** en la red.  
3. **Pérdida de paquetes o congestión**: Un *timeout* en algunos nodos no significa que el tráfico no fluya, sino que **no responden a la solicitud ICMP**.  

📌 **Conclusión:**  
- Aunque algunos nodos intermedios **no respondieron**, la traza **llegó correctamente** a `www.us.es`, lo que confirma que la conexión con el destino es **funcional**.  
- La ausencia de respuesta en ciertos saltos **no implica necesariamente un problema de conectividad**, sino que podría ser una **restricción de seguridad** en la red de la Universidad de Sevilla o intermediarios.  


---

### 13/02/25

## **Ejercicio 4.4: Traceroute desde un servidor remoto a nuestra máquina**  

**Dirección IP de la máquina:** `192.168.5.13`  
**IP privada dentro de la red local** (no accesible desde Internet).  

---

### **🔹 Resultado del traceroute desde Springfield University u Host-tracker:**  
```
Tracing route to 192.168.5.13 over a maximum of 30 hops

  1    <1 ms    <1 ms    <1 ms  192.168.0.99
  2     *        *        *     Tiempo de espera agotado para esta solicitud.
  3     *        *        *     Tiempo de espera agotado para esta solicitud.
```
🔹 **Explicación del resultado:**  
- El traceroute **no puede alcanzar** la dirección **192.168.5.13** porque es una **IP privada** y no está accesible desde Internet.  
- El rastreo se detiene en la puerta de enlace (`192.168.0.99`), ya que el router **no reenvía** el tráfico entrante hacia direcciones privadas a menos que haya reglas específicas configuradas (como port forwarding).  

✅ **Conclusión:** No es posible hacer un traceroute desde Internet hasta una dirección IP privada como `192.168.5.13` porque está protegida por NAT y firewalls en el router.

---

## **Ejercicio 4.5: Traceroute a la IP pública del router**  

**IP pública del router:** `88.4.178.31`  

### **🔹 Resultado del traceroute a la IP pública:**  
```
Tracing route to 88.4.178.31 over a maximum of 30 hops

  1     1 ms     1 ms     1 ms  192.168.144.1
  2     5 ms     6 ms     5 ms  161.red-5-205-20.dynamicip.rima-tde.net [5.205.20.161]
  3    10 ms     8 ms    10 ms  238.red-5-205-20.dynamicip.rima-tde.net [5.205.20.238]
  4     *        *        *     Tiempo de espera agotado para esta solicitud.
  5    14 ms    12 ms    13 ms  88.4.178.31
```
🔹 **Explicación del resultado:**  
- En este caso, el traceroute **sí alcanza la IP pública del router** (`88.4.178.31`).  
- Se observan varios saltos dentro de la red del ISP antes de llegar al destino.  
- Algunos routers intermedios no responden porque están configurados para **no revelar su presencia**.  

### **🔹 Comparación con el ejercicio 4.4**  
1. **Diferente resultado**  
   - En el traceroute a `192.168.5.13`, el tráfico **no llega** porque la IP es privada y está bloqueada por NAT.  
   - En el traceroute a `88.4.178.31`, el tráfico **sí llega** porque es la IP pública del router.  

2. **Simetría en el enrutamiento**  
   - El camino de ida y el de vuelta no siempre son idénticos debido a **balanceo de carga** y diferentes políticas de enrutamiento de los ISPs.  
   - Algunos routers pueden ser los mismos en ambos casos, pero con **IPs diferentes**, ya que muchas grandes redes usan múltiples interfaces y sistemas de redundancia.  

✅ **Conclusión:**  
- **Traceroute hasta `192.168.5.13` (IP privada) no funciona** debido a NAT y firewalls.  
- **Traceroute hasta `88.4.178.31` (IP pública) sí funciona**, pero no revela dispositivos dentro de la red local.  
- **Los caminos de ida y vuelta pueden diferir** dependiendo de cómo los ISPs gestionan el tráfico. 🚀

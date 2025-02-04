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

### **04/02/25**  

## **Ejercicio 1: Análisis de conectividad y comunicación en una red**  

### **a) Determinar si dos PCs están en la misma red**  

**Datos proporcionados:**  
- **PC 1:** `172.16.4.100/21`  
- **PC 2:** `172.16.6.200/21`  
- **Máscara de subred:** `255.255.248.0`  

#### **Cálculo en binario:**  
```plaintext
IP:       172.16.4.100    →  10101100.00010000.00000100.01100100
Máscara:  255.255.248.0   →  11111111.11111111.11111000.00000000
Red:      172.16.0.0      →  10101100.00010000.00000000.00000000
```
```plaintext
IP:       172.16.6.200    →  10101100.00010000.00000110.11001000
Máscara:  255.255.248.0   →  11111111.11111111.11111000.00000000
Red:      172.16.0.0      →  10101100.00010000.00000000.00000000
```
**Dirección de Red:** 172.16.0.0  

✅ **Conclusión:** Ambos dispositivos **están en la misma red** (`172.16.0.0/21`), ya que tienen la misma dirección de red.

---

### **b) Determinar el rango de direcciones de la red**  

- **Dirección de red:** `172.16.0.0`  
- **Dirección de broadcast:** `172.16.7.255`  
- **Rango de IPs válidas:**  
  ```plaintext
  Primera IP válida: 172.16.0.1
  Última IP válida: 172.16.7.254
  ```

✅ **Conclusión:** Todos los dispositivos dentro de **172.16.0.1 - 172.16.7.254** pueden comunicarse sin un router.

---

### **c) Determinar el número de hosts en esta subred**  

Se usa la fórmula:  
```plaintext
Número de hosts = 2^(32 - prefijo) - 2
```
Para `/21`:  
```plaintext
2^(32 - 21) - 2 = 2^11 - 2 = 2046 hosts
```
✅ **Conclusión:** La red permite **2046 dispositivos** conectados.

---

## **Ejercicio 2: Análisis de una red IPv6**  

**Dirección IPv6 proporcionada:**  
```plaintext
2001:db8:abcd:1234::1/64
```

### **a) Determinar cuántas direcciones hay en una subred `/64`**  

En IPv6, una **/64** significa que los **primeros 64 bits** representan la red, y los **últimos 64 bits** se usan para **hosts**.  

```plaintext
Número total de direcciones en /64 = 2^(128 - 64) = 2^64 ≈ 18,446,744,073,709,551,616
```
✅ **Conclusión:** Una subred IPv6 `/64` puede tener **18.4 quintillones** de direcciones.  

---

### **b) Determinar la dirección de red y dirección de broadcast**  

- **Dirección de red:**  
  ```plaintext
  2001:db8:abcd:1234::/64
  ```
- **Dirección de broadcast en IPv6:**  
  IPv6 **no usa dirección de broadcast**. En su lugar, se usa **Multicast**.  

✅ **Conclusión:** En IPv6, el **equivalente a broadcast** es la dirección **`ff02::1`**, que envía paquetes a **todos los hosts de la red local**.  

---

### **c) Identificar el rango de direcciones de la red**  

Dado que **los primeros 64 bits son fijos**, el rango de direcciones en **`2001:db8:abcd:1234::/64`** es:  
```plaintext
Primera IP válida: 2001:db8:abcd:1234::1
Última IP válida: 2001:db8:abcd:1234:ffff:ffff:ffff:ffff
```
✅ **Conclusión:** Todas las direcciones dentro de este rango pertenecen a la misma subred.  

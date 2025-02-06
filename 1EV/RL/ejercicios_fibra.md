# Ejercicios libro
## Ejercicio 2
Numero empalmes: 50/2 - 1 = 24<br>
perdida/empalme = 24 x 0.1 = 2.4db<br>
Son 50km, por lo que 50 x 0.4 = 20db de perdida por fibra<br>
Perdidas del conector = 4db<br>
Atenuacion total = 20 + 2.4 + 4 = 26.4db

PR = PT - Atenuación = 4,77 - 26,4 = -21,63dBM
## Ejercicio 3
Empalmes 4 (10/2 - 1)<br>
Atenuación de los 4 empalmes = 0.2 x 4 = 0.8db<br>
Atenuación 10km (fibra) = 0.5db x 10km = 5db<br>
Perdida total aclopamientos y conectores = 6db
Atenuación total = 6 + 5 + 0.8 = 0.8db

## Ejercicio 4

Longitud 50km<br>
Potencia salida 3dBm<br>
Intensidad receptor -31,5<br>
rollos 2km 0,2 empalme<br>
conectores 4,2db<br>
Margen de diseño 8 db calcular atenuacion fibra


50/2 -1 = 24 empalmes<br> 
24*0,2 = 4,8db empalmes<br>
Conectores 4,2dB<br>
Atenuacion /km<br>
4,8+4,2 = 9dB<br>
3-9 = 6dB<br>
31,5-6 - 8 = 17,5dB | atenuacion 0,35db/km 17,5/50


# Ejercicios PDF (FO)

## Ejercicio 1
**Datos:**
- Potencia de emisión: 0 dBm
- Potencia mínima en el receptor: -20 dBm
- Distancia: 10 km
- Empalmes cada 2 km → Total de 5 empalmes
- Pérdida por empalme: 0.2 dB
- Pérdida de conectores: 6 dB
- Margen de 8 dB

**Cálculos:**
1. Atenuación de la fibra: No dada, así que será el valor a buscar.
2. Pérdidas por empalmes = 5 * 0.2 = 1 dB.
3. Pérdida total requerida:
   ```
   0 dBm - (-20 dBm) = 20 dB (pérdida permisible)
   ```
4. Pérdida disponible sin margen: 20 - 6 - 1 = 13 dB.
5. Con margen de 8 dB, queda: 13 - 8 = 5 dB para la fibra.
6. Atenuación de la fibra por km:
   ```
   5 dB / 10 km = 0.5 dB/km
   ```

**Respuesta:** La atenuación de la fibra debe ser **0.5 dB/km**.

---

## Ejercicio 2
**Datos:**
- Potencia de transmisión: 4.77 dBm
- Potencia mínima en receptor: -21.63 dBm
- Pérdida por conector: 4 dB
- Pérdida por empalme: 0.1 dB (cada 2 km)
- Atenuación de la fibra: 0.4 dB/km

**Cálculos:**
1. Pérdida permisible:
   ```
   4.77 dBm - (-21.63 dBm) = 26.4 dB
   ```
2. Pérdida de conectores: 4 dB.
3. Pérdida por empalmes cada 2 km → 0.1 dB * (L / 2) km.
4. Pérdida por fibra: 0.4 dB/km * L.
5. Ecuación total de pérdidas:
   ```
   26.4 = 4 + 0.1 * (L / 2) + 0.4 * L
   ```
6. Resolviendo para `L`, se obtiene **L ≈ 48.5 km**.

**Respuesta:** La longitud máxima del enlace es aproximadamente **48.5 km**.

---

## Ejercicio 3
**Datos:**
- Potencia de emisión: 0 dBm
- Potencia mínima en receptor: -25 dBm
- Distancia: 30 km
- Pérdida de fibra: 0.3 dB/km
- Pérdida por empalme: 0.25 dB (cada 2.5 km, por lo que hay 12 empalmes)
- Pérdida por conectores: 4 dB

**Cálculos:**
1. Pérdida permisible:
   ```
   0 - (-25) = 25 dB
   ```
2. Pérdida por fibra: 0.3 * 30 = 9 dB.
3. Pérdida por empalmes: 12 * 0.25 = 3 dB.
4. Pérdida total:
   ```
   9 + 3 + 4 = 16 dB
   ```
5. Margen disponible:
   ```
   25 - 16 = 9 dB
   ```

**Respuesta:** El margen del sistema es **9 dB**, suficiente para que el enlace sea viable.
# Identificación del PC en una Red Local con Etiquetas

## Introducción
En este cuaderno aprenderemos a identificar un PC en una red local estructurada utilizando el sistema de etiquetado estándar TIA/EIA 606-A. Este proceso nos permitirá saber en qué **edificio**, **aula**, y **armario de telecomunicaciones** se encuentra el equipo, y cómo está conectado a la red.

---

## ¿Qué es una etiqueta en redes?
Una **etiqueta** es un código único que identifica un elemento del cableado estructurado, como:
- El **cable** que conecta un PC a la red.
- La **roseta** de red (el punto físico donde se conecta el cable al PC).
- Los puertos del **panel de parcheo** y el **switch**.

### Ejemplo de Etiqueta:
```plaintext
[E2-0A]/[E3-0A]-23
```

### Significado:
1. **[E2-0A]:**
   - **E2:** Edificio 2.
   - **0A:** Armario A en la planta baja (0).
2. **[E3-0A]:**
   - Conexión al armario A en la planta baja del Edificio 3.
3. **-23:**
   - Cable número 23, que conecta ambos armarios.

---

## Elementos de la Red Estructurada
Para entender cómo se conecta un PC en la red, debemos conocer los siguientes elementos:

### 1. **Roseta (Toma de Red)**
- Punto de conexión físico donde el **PC** se conecta a la red con un cable corto (latiguillo).
- Está etiquetada con un código único, como `[E2-0A-12]`, que indica:
  - Edificio.
  - Planta.
  - Armario.
  - Número de conexión (12).

### 2. **Cable Horizontal**
- Es el cable que conecta la roseta al **panel de parcheo** en el armario de telecomunicaciones.
- Etiqueta ejemplo: `[E2-0A]/[E3-0A]-23`.

### 3. **Panel de Parcheo**
- Panel ubicado en el armario donde terminan los cables que vienen de las rosetas.
- Cada puerto está numerado y coincide con la etiqueta de la roseta.

### 4. **Cable de Parcheo (Patch Cable)**
- Cable corto que conecta el panel de parcheo al switch de red.

### 5. **Switch de Red**
- Dispositivo activo que distribuye la conexión a los PCs.

---

## Pasos para Identificar un PC en la Red

### 1. **Identifica la Etiqueta del PC**
- Busca la etiqueta en el **latiguillo** o en la **roseta** conectada al PC.
- Ejemplo: `[E2-0A-12]`.

### 2. **Localiza la Roseta**
- Sigue el **latiguillo** (cable corto) del PC hasta la **roseta** en la pared.
- Verifica que la etiqueta de la roseta coincide con la del PC.

### 3. **Rastrea el Cable hasta el Panel de Parcheo**
- Encuentra el **puerto numerado** en el panel de parcheo dentro del armario que corresponde a la etiqueta.
  - Ejemplo: Si la roseta está etiquetada como `[E2-0A-12]`, busca el puerto "12" en el panel de parcheo del **armario A** del **Edificio 2**.

### 4. **Conexión al Switch**
- Identifica el puerto del switch conectado al puerto del panel de parcheo.
- Este paso puede requerir herramientas de red o documentación.

---

## Ejemplo Práctico
### Situación:
- Estás trabajando en un aula del **Edificio 2**, planta baja.
- El PC que estás usando tiene la etiqueta: `[E2-0A-12]`.

### Solución:
1. **Ubicación Física:**
   - La etiqueta indica que estás en el **Edificio 2**, **planta baja**, conectado al **armario A**.
2. **Roseta:**
   - Sigue el latiguillo desde el PC hasta la roseta etiquetada `[E2-0A-12]`.
3. **Panel de Parcheo:**
   - Rastrea el cable horizontal desde la roseta hasta el puerto "12" del panel de parcheo en el armario A.
4. **Switch:**
   - Verifica que el puerto "12" del panel de parcheo está conectado al switch de red.

---

## Beneficios del Sistema de Etiquetas
1. **Ubicación Precisa:**
   - Permite saber exactamente dónde está el PC (edificio, aula, armario).
2. **Resolución de Problemas:**
   - Facilita identificar fallos en el cableado o en los dispositivos de red.
3. **Gestión Eficiente:**
   - Mantiene organizada la red estructurada.

---

## Resumen de Elementos Clave
| **Elemento**           | **Función**                                                                 | **Etiqueta Ejemplo**      |
|-------------------------|-----------------------------------------------------------------------------|---------------------------|
| **Roseta**             | Punto de conexión del PC a la red.                                          | `[E2-0A-12]`             |
| **Cable Horizontal**   | Conecta la roseta al panel de parcheo.                                      | `[E2-0A]/[E3-0A]-23`     |
| **Panel de Parcheo**   | Termina los cables de las rosetas y conecta al switch.                      | Puerto 12 en `[E2-0A]`   |
| **Cable de Parcheo**   | Une el panel de parcheo al switch.                                          | Sin etiqueta específica.  |
| **Switch**             | Administra las conexiones de red activas.                                  | Puerto "5" del Switch 2. |

---

## Actividad
1. Encuentra la etiqueta en el PC que estás utilizando.
2. Sigue el latiguillo hacia la roseta y anota su etiqueta.
3. Localiza el puerto correspondiente en el panel de parcheo y documenta la conexión hasta el switch.

---

## Conclusión
Este sistema de identificación nos permite rastrear un PC desde su ubicación física hasta su conexión en el armario de telecomunicaciones y el switch de red, garantizando una gestión ordenada y eficiente de la red.

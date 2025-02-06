# Ejercicio 1: Estándares Ethernet

## Problema
Debemos interconectar **30 ordenadores** para formar una red cumpliendo las siguientes especificaciones:
- Disponemos únicamente de **concentradores de cableado de 8 puertos**.
- Se debe seguir el estándar **100BaseT4**.
- Es necesario usar el menor número posible de elementos de interconexión.

## Solución

### Análisis
1. Cada concentrador dispone de 8 puertos:
   - **7 puertos útiles** para ordenadores (1 puerto se reserva para la interconexión entre concentradores o hacia un nodo central).
2. Para conectar 30 ordenadores:
   - Se necesitan al menos **5 concentradores**.
   - Cuatro concentradores conectarán a 7 ordenadores cada uno.
   - Un concentrador conectará a 2 ordenadores y se encargará de la interconexión central.

### Topología seleccionada: Estrella
La topología en estrella es más eficiente que la cascada para esta tarea, ya que:
- Ofrece un nodo central que distribuye las conexiones hacia los concentradores secundarios.
- Mejora la escalabilidad y minimiza los cuellos de botella.

### Diseño gráfico
A continuación, se presenta el diseño gráfico de la red:

![Topología en estrella](https://i.imgur.com/BGYCQ1C.png)

### Descripción del diseño
1. **HUB_Central**:
   - Este nodo central conecta a todos los concentradores secundarios.
   - Permite organizar la red en forma de estrella, cumpliendo con los requisitos del problema.
2. **Concentradores secundarios (HUB1, HUB2, HUB3, HUB4, HUB5)**:
   - Cada uno de los concentradores secundarios conecta a sus respectivos ordenadores:
     - **HUB1**: PC1 a PC7
     - **HUB2**: PC8 a PC14
     - **HUB3**: PC15 a PC21
     - **HUB4**: PC22 a PC28
     - **HUB5**: PC29 y PC30
3. **Interconexión central**:
   - Cada concentrador se conecta al **HUB_Central** para mantener la conectividad global.

### Conclusión
El diseño propuesto cumple con:
- La conexión de los 30 ordenadores con **5 concentradores** de 8 puertos.
- La topología en estrella, optimizando la interconexión con un nodo central.
- El estándar **100BaseT4**, utilizando cableado trenzado y permitiendo velocidades de 100 Mbps.



# Ejercicio 2: Subestándares Ethernet
### Caso 1: Distancia < 100 m
- **Solución**:
  - Los switches de las dos redes LAN se conectan **directamente** mediante un cable coaxial (10BASE2).
  - La distancia está dentro del límite soportado por el estándar, por lo que no se necesitan repetidores ni dispositivos adicionales.
- **Ventajas**:
  - Simplicidad y bajo coste.
  - Uso óptimo del hardware disponible.

**Diseño**:
![Caso 1](https://i.imgur.com/u7Dl9Gt.png)

---

### Caso 2: Distancia ~190 m
- **Problema**:
  - La distancia supera el límite máximo de un segmento de 10BASE2 (**185 metros**).
- **Solución**:
  - Se coloca un **repetidor** entre las dos redes LAN para amplificar la señal.
  - Esto divide la conexión en dos segmentos, cada uno menor a 185 metros.
- **Ventajas**:
  - Solución sencilla con solo un dispositivo adicional.
  - Cumple con las especificaciones del estándar 10BASE2.

**Diseño**:
![Caso 2](https://i.imgur.com/fa5rx6D.png)

---

### Caso 3: Distancia ~400 m
- **Problema**:
  - La distancia total (400 metros) es mucho mayor que la soportada por un único segmento o un solo repetidor.
- **Solución**:
  - Se utilizan **dos repetidores** para dividir la conexión en tres segmentos, cada uno menor a **185 metros**.
  - Esto asegura que la señal se mantenga dentro de los límites del estándar.
- **Ventajas**:
  - Solución escalable para largas distancias.
  - Permite mantener la integridad de la red.

**Diseño**:
![Caso 3](https://i.imgur.com/9hLsGXQ.png)

---

## Conclusión
Este ejercicio muestra cómo ajustar una red local a diferentes distancias utilizando el subestándar **10BASE2**. Aprendi que:
1. La solución más sencilla (conexión directa) es suficiente para distancias cortas.
2. Los **repetidores** son esenciales para extender la red y mantener la conectividad en distancias mayores.
3. La planificación adecuada asegura que las redes cumplan con los estándares técnicos sin exceder sus límites.

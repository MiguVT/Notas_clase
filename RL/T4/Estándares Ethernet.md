# Ejercicio: Estándares Ethernet

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

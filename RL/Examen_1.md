# **Guía Completa para el Primer Curso - Primer Trimestre (Grado Medio)**

## **1. Introducción a las Redes**

### **1.1 Conceptos Básicos**
- **Definición de red**: Conexión de dispositivos para compartir información y recursos.
- **Tipos de redes**:
  - **LAN**: Red de área local, conexión en un área geográfica reducida.
  - **WAN**: Red de área amplia, conexión entre diferentes ubicaciones geográficas.

### **1.2 Elementos de una Red**
- **Dispositivos finales**:
  - Ordenadores, impresoras, teléfonos IP.
- **Dispositivos intermedios**:
  - Switches, routers, puntos de acceso.
- **Medios de transmisión**:
  - Cables de par trenzado, fibra óptica, cables coaxiales, redes inalámbricas.

### **1.3 Topologías de Red**
- **Físicas**:
  - Estrella, anillo, bus, malla.
- **Lógicas**:
  - Describe cómo fluye la información en la red.

---

## **2. Medios de Transmisión**

### **2.1 Cableado de Par Trenzado**
- **Categorías de cables**:
  - **CAT5e**: Hasta 1 Gbps.
  - **CAT6**: Hasta 10 Gbps en distancias cortas.
- **Esquemas de conexión**:
  - T568A y T568B (diferencias en los colores de los hilos).

#### **Práctica P01: Hacer Latiguillos**
1. **Materiales necesarios**:
   - Cable UTP, conectores RJ45, crimpadora, tester.
2. **Pasos**:
   - Pelar el cable, alinear hilos según el esquema.
   - Crimpar y probar con el tester.
3. **Latiguillos cruzados vs. directos**:
   - **Directos**: Conexión entre PC y switch.
   - **Cruzados**: Conexión entre PCs o switches.

### **2.2 Fibra Óptica**
- **Partes de la fibra**:
  - Núcleo, revestimiento y cubierta.
- **Tipos**:
  - **Monomodo**: Distancias largas, alta velocidad.
  - **Multimodo**: Distancias cortas, mayor ancho de banda.
- **Ventajas**:
  - Alta velocidad, inmunidad a interferencias.
- **Desventajas**:
  - Coste elevado, instalación especializada.

#### **Conectores de Fibra Óptica**
- **SC**: Conexión directa.
- **ST**: Requiere giro para conectar.
- **LC**: Compacto, popular para redes modernas.

### **2.3 Cables Coaxiales**
- **Estructura**:
  - Núcleo conductor, malla metálica y cubierta externa.
- **Tipos**:
  - Thicknet: Mayor alcance, difícil instalación.
  - Thinnet: Más flexible, fácil de instalar.
- **Ventajas**:
  - Menos susceptible a interferencias, buena para largas distancias.
- **Desventajas**:
  - Rigidez, difícil mantenimiento.

---

## **3. Instalaciones de Red**

### **3.1 Canalizaciones**
- **Tipos**:
  - Superficiales (canaletas) y empotradas (dentro de paredes).
- **Reglas**:
  - Separación de cables eléctricos y de red.
  - Uso de curvas suaves.

### **3.2 Rosetas RJ45**
#### **Práctica P02: Instalar Rosetas**
1. **Materiales necesarios**:
   - Roseta, cable UTP, herramienta de impacto.
2. **Pasos**:
   - Pelar el cable, destrenzar pares.
   - Colocar hilos según el esquema.
   - Comprobar conexión con tester.

---

## **4. Protocolos y Estándares**

### **4.1 Ethernet**
- **Velocidades**:
  - 10BASE-T (10 Mbps), 100BASE-TX (100 Mbps), 1000BASE-T (1 Gbps).
- **Tramas Ethernet**:
  - **Encabezado**: Direcciones MAC.
  - **Datos**: Información transmitida.
  - **FCS**: Comprobación de errores.

### **4.2 Estándares de Cableado**
- **ISO/IEC 11801**: Define el cableado estructurado.
- **TIA/EIA-568**: Esquemas de conexión para par trenzado.

---

## **5. Ejercicios de Repaso**

### **5.1 Preguntas sobre Cableado**
- ¿Cuándo se utiliza un cable directo y uno cruzado?  
  Completa la tabla:
  | Dispositivos          | Cruzado (Sí/No) |
  |-----------------------|-----------------|
  | De PC a PC           | Sí             |
  | De PC a HUB          | No             |
  | De PC a SWITCH       | No             |
  | De PC a ROUTER       | No             |

### **5.2 Ejercicios de Fibra**
- Calcula la atenuación de una fibra óptica de 10 km con pérdidas de 0,2 dB/km y 2 conectores (0,5 dB cada uno):
  \[
  \text{Atenuación total} = (10 \times 0,2) + (2 \times 0,5) = 3 \, \text{dB}
  \]

---

## **6. Resumen General**
- **Redes**: Tipologías, dispositivos, medios.
- **Cableado**: Par trenzado, coaxial, fibra óptica.
- **Estándares**: Normativas de instalación.
- **Prácticas**: Latiguillos, rosetas.
- **Ejercicios**: Identificación de componentes, cálculo de atenuación.

## **Cómo Resolver los Ejercicios**

### **Ejercicios de Cableado**

#### **1. Diferencia entre cable directo y cruzado**
- **Cable directo**:
  - Ambos extremos tienen el mismo esquema (T568A o T568B).
  - Ejemplo de uso: Conexión de un PC a un switch o router.
- **Cable cruzado**:
  - Un extremo es T568A y el otro es T568B.
  - Ejemplo de uso: Conexión entre dos PCs o dos switches.

**¿Cómo construirlos?**
- Sigue los pasos de la práctica P01:
  - Pela el cable, organiza los hilos según el esquema y crimpa los conectores.
  - Comprueba la conexión con el tester.

---

### **Ejercicios sobre Fibra Óptica**

#### **2. Cálculo de atenuación**
1. Identifica:
   - **Distancia del cable** (en km).
   - **Pérdida por kilómetro** (dB/km).
   - **Conectores o empalmes** (cada uno añade pérdida en dB).
2. Usa la fórmula:
   \[
   \text{Atenuación total} = (\text{Distancia} \times \text{Pérdida por km}) + (\text{Conectores} \times \text{Pérdida por conector})
   \]
3. Ejemplo:
   - Distancia: 10 km.
   - Pérdida por km: 0,2 dB.
   - 2 conectores con pérdida de 0,5 dB cada uno.
   \[
   \text{Atenuación total} = (10 \times 0,2) + (2 \times 0,5) = 3 \, \text{dB}
   \]

---

### **Ejercicios de Instalación de Rosetas**

#### **3. Conexión de una roseta RJ45**
1. Pela el cable y destrenza los pares.
2. Coloca los hilos en el conector siguiendo el esquema de colores.
3. Usa la herramienta de impacto para asegurar los hilos.
4. Comprueba la conexión con un tester.

---

### **Ejercicios sobre Redes**

#### **4. Topologías de red**
- Dibuja las conexiones según la descripción.
  - **Estrella**: Todos los dispositivos conectados a un switch central.
  - **Bus**: Una línea compartida para todos los dispositivos.
- Ejemplo:
  - "Diseña una red para 5 PCs conectados a un switch" → Usar topología estrella.

---

### **Preguntas de Teoría**
- **Categorización de cables**: Aprende las diferencias entre CAT5e, CAT6, etc.
- **Ventajas y desventajas de cada medio**:
  - Par trenzado: Económico, pero menor distancia.
  - Fibra óptica: Alta velocidad, pero costosa.
  - Coaxial: Resistente a interferencias, pero rígido.

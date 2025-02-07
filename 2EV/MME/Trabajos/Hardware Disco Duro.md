# Taller 02.06: Hardware – Disco Duro

## Objetivo
Conocer las conexiones y características de un disco duro.

## Material Necesario
- Cuaderno de laboratorio
- Bolígrafo
- Equipo de prácticas

## Duración
2 horas

## Instrucciones

### 1. Acceder al Administrador de Dispositivos
1. Abre el menú de inicio y escribe `Administrador de dispositivos`. Ábrelo.
2. Busca la sección `Unidades de disco` y expándela.
3. En mi caso, aparecen **una unidad de disco** aunque fisicamente esten dos, uno de ellos no esta conectado.
![IMG_20250207_113704919](https://github.com/user-attachments/assets/e3dbe9ae-eb3e-4dbe-b86d-280ea67e215f)

#### 1.1 Propiedades de los discos
4. Hago clic derecho sobre la unidad y selecciono `Propiedades`.
5. Anoto las particiones:
   - `C:` 76100 MB (supongo que NTFS, aunque no lo indica)
   - `Datos (D:)` 37612 MB (supongo que tambien NTFS, aunque no lo indica)
7. Selecciono la unidad `C:` y en `Propiedades` veo que el `Sistema de archivos` es **NTFS**, confirmando mi teoría, adicionalmente veo la opcion de 'Liberar espacio'.
   ![IMG_20250207_114003164](https://github.com/user-attachments/assets/da0f0478-fded-4a5d-8a7b-9fd0422024ee)
9. Y en la pestaña `Herramientas` veo estas opciones:
   - **Comprobación de errores:** Analiza el disco en busca de errores.
   - **Optimizar y desfragmentar unidad:** Mejora el rendimiento del disco.

     ![imagen sacada de captura de otro PC para mayor claridad](https://github.com/user-attachments/assets/2f85ca20-30a2-48e7-a10e-950e7a13af12)
     ###### Imagen sacada en otro PC para mayor claridad, ya que en todos es lo mismo.


### 2. Análisis del Disco Duro
1. Mi ordenador tiene **dos discos duros físicos** (Uno desconectado).
![Disco desconectado](https://github.com/user-attachments/assets/ff444f70-9c67-4a10-b291-d7f1e9db709d)



#### 2.1 Esquema de conexiones
2. Hago un esquema de las conexiones del disco duro y las nombro que pide el ejercicio.

```
     +---------------------------------+
     |         Placa Base              |
     |  +---------------------------+  |
     |  |   Puerto SATA 1           |  |
     |  +---------------------------+  |
     |  |   Puerto SATA 2 (Vacío)   |  |
     |  +---------------------------+  |
     +---------------------------------+

                │  
                │  Cable SATA  
                │  
     +-------------------+
     |    SSD (SATA)     |
     |  500GB (Conectado)|
     +-------------------+

     +--------------------------------+
     |     Fuente de Alimentación     |
     |  +-------------------------+  |
     |  |    Conector SATA Power  |  |
     |  +-------------------------+  |
     +--------------------------------+

                │  
                │  Cable de Alimentación  
                │  
     +-------------------+
     |    SSD (SATA)     |
     +-------------------+

     +-------------------+
     |    HDD (SATA)     |
     |  1TB (Desconectado)|
     +-------------------+
     (Sin cables conectados)
```

### 3. Extracción del Disco Duro
1. Desconecto los cables del disco duro.
2. Quito las fijaciones y extraigo el disco.
3. Aquí está la imagen de la etiqueta del disco duro con la ssd:

![Etiqueta Disco duro y SSD](https://github.com/user-attachments/assets/e1b4db1b-4871-4ad6-a086-94db2d402cd5)


4. Características del disco duro:
   - **Marca:** Seagate
   - **Modelo:** Barracuda
   - **Capacidad:** 500 GB
   - **Velocidad:** 7200 RPM
   - **Tipo de conexión:** SATA

### 4. Montaje del Disco Duro
1. Coloco el disco duro en la bahía donde estaba.
2. Conecto los cables correctamente.
3. Enciendo el ordenador y verifico que inicia sin problemas.
![Imagen disco duro montado](https://github.com/user-attachments/assets/6e833722-2897-4ffc-972d-6497d08f8b72)


### 5. Conclusión
Este ejercicio me permitió comprender cómo identificar, desmontar y volver a montar un disco duro. Ahora sé cómo acceder a sus propiedades en Windows, revisar sus particiones y conexiones, además de aprender sobre sus características técnicas.
Aunque ya sabia esto, nunca esta mal refrescar la memoria, mas teniendo en cuenta que hoy en dia cada vez hay menos discos duros y repito este proceso menos frecuentemente.

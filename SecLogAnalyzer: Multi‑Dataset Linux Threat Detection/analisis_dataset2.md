# Análisis del Dataset 2 – Tráfico IoT y Actividades Maliciosas
- **Proyecto**: Real-Time Internet of Things (IoT) 2022  
- **Dataset 2** – Network Flow Analysis

## 1. Introducción
El segundo dataset del proyecto contiene tráfico de red generado por dispositivos IoT junto con múltiples tipos de ataques. El objetivo del análisis es identificar patrones de comportamiento normal, detectar anomalías y caracterizar los ataques presentes.
Este dataset está compuesto por flujos de red (network flows), no por logs crudos, lo que significa que cada fila representa un resumen estadístico de una conexión.

## 2. Preparación del Dataset

- ![](imagenes/13.png)
- ![](imagenes/14.png)
- ![](imagenes/15.png)
- ![](imagenes/16.png)
- ![](imagenes/17.png)

### 2.1 Problemas detectados en el archivo original
El dataset original presentaba varios inconvenientes:
- Más de 80 columnas con nombres incompatibles con SQLite.
- Caracteres no válidos en los encabezados:
- Puntos
- Guiones
- Espacios
- Mayúsculas mezcladas
- Dificultad para importar el CSV en SQLite/DBeaver debido a:
  - Interpretación errónea de puntos como tabla.columna
  - Necesidad de comillas para nombres con espacios
  - Guiones interpretados como operadores
  - Imposibilidad de generar la tabla automáticamente

- Errores frecuentes como:
  - SQLITE_ERROR: incomplete input
  - SQLite es estricto con los nombres de columnas, por lo que fue necesario normalizarlos.

#### 2.2 Limpieza del dataset en Python
Se creó un script para normalizar los nombres de columnas y generar un CSV compatible con SQLite.

```bash 
import pandas as pd
import os

base_path = os.path.dirname(os.path.abspath(__file__))
input_file = os.path.join(base_path, "dataset_2_limpio.csv")

df = pd.read_csv(input_file)

df.columns = (
    df.columns
    .str.strip()
    .str.lower()
    .str.replace(" ", "_")
    .str.replace(".", "_")
    .str.replace("-", "_")
)

output_file = os.path.join(base_path, "dataset_2_sqlite_ready.csv")
df.to_csv(output_file, index=False)

print("Archivo guardado en:", output_file)
```

- Este proceso garantiza:
  - Importación sin errores
  - Compatibilidad total con SQLite
  - Estructura de tabla generada automáticamente
  - Flujo de trabajo reproducible

### 2.3 Conversión del CSV a base de datos SQLite
Debido a limitaciones de las extensiones de VS Code y la ausencia del comando sqlite3 en Windows, se utilizó Python para crear la base de datos.

- ![](imagenes/18.png)


## 3. Descripción del Dataset
- ![](imagenes/19.png)
- Total de registros: 123.117

---
- Tabla: datos
- Columnas principales:
- id_orig_p (puerto origen)
- id_resp_p (puerto destino)
- proto (protocolo)
- service (servicio)
- Métricas de flujo (flow_, fwd_, bwd_*)
- attack_type (etiqueta de ataque)
- Este dataset fue generado por herramientas de análisis de flujo como CICFlowMeter, Zeek o Argus.
- ![](imagenes/20.png)

## 4. Análisis del Tráfico IoT Normal
### 4.1 Servicios más usados
Consulta SQL:

```sql
SELECT service, COUNT(*) AS total
FROM datos
GROUP BY service
ORDER BY total DESC;
```

- - ![](imagenes/21.png)
- Hallazgos:
  - dns, mqtt, http, ssl → tráfico IoT normal
  - "-" → tráfico no clasificado (común en capturas reales)

- Interpretación:
- MQTT (1883) confirma comunicación IoT
- DNS (53/5353) es esencial para resolución de nombres
- HTTP/HTTPS (80/443) corresponde a servicios web

### 4.2 Protocolos
Consulta:

```sql
SELECT proto, COUNT(*) AS total
FROM datos
GROUP BY proto
ORDER BY total DESC;
```
- - ![](imagenes/22.png)
- Hallazgos:
  - Predomina TCP
  - UDP aparece por DNS
  - ICMP es mínimo

- Interpretación:
  - El tráfico IoT suele ser TCP por MQTT, HTTP y SSL

### 4.3 Puertos destino
Consulta:

```sql
SELECT id_resp_p, COUNT(*) AS total
FROM datos
GROUP BY id_resp_p
ORDER BY total DESC
LIMIT 20;
```

- Hallazgos:
  - 1883 (MQTT), 53/5353 (DNS), 80/443 (web) → normal
  - 21 (FTP) → tráfico anómalo masivo

- Interpretación:
  - El puerto 21 no es habitual en IoT
  - Su volumen sugiere escaneo o ataque

## 5. Análisis del Tráfico Malicioso
### 5.1 Tipos de ataque
Consulta:

```sql
SELECT attack_type, COUNT(*) AS total
FROM datos
GROUP BY attack_type
ORDER BY total DESC;

```
- - ![](imagenes/23.png)

- DOS_SYN_Hping
- ARP_poisoning
- NMAP scans (UDP, TCP, XMAS, FIN, OS detection)
- Slowloris
- SSH brute force
- MQTT_Publish

### 5.2 Indicadores de ataque
- SYN alto → DoS
- ACK alto → flooding o escaneo
- Muchos puertos destino → NMAP
- Duración extrema → Slowloris
- Puerto 21 → actividad sospechosa

## 6. Comparación: Tráfico IoT Normal vs Malicioso
| Comportamiento |	Normal	| Malicioso |
|:--|:--|:--|
|Servicios|	MQTT, DNS, HTTP/HTTPS |	FTP masivo, puertos inusuales|
|Protocolos	|TCP/UDP estables|	TCP con flags anómalos |
|Flujo	|Estable, predecible |	SYN/ACK altos, duración extrema|
|Patrones	|Puertos destino fijos |	Escaneos múltiples|
|Etiquetas	| Benign	|DoS, ARP, NMAP, Slowloris|
---
- ![](imagenes/24.png)
- ![](imagenes/25.png)
- ![](imagenes/26.png)
- ![](imagenes/27.png)
  
## 7. Conclusión del Dataset 2
El análisis del Dataset 2 muestra que la red IoT combina tráfico legítimo con una presencia significativa de actividades maliciosas. El tráfico normal se concentra en servicios propios del entorno IoT, como MQTT (1883), DNS (53/5353) y HTTP/HTTPS (80/443), lo que refleja un funcionamiento estable y predecible de los dispositivos conectados.
Sin embargo, el campo attack_type revela que el dataset contiene múltiples ataques reales, con una distribución claramente dominada por ciertos tipos. Los ataques más frecuentes fueron:
- DOS_SYN_Hping: aproximadamente 94.659 registros, convirtiéndose en el ataque más predominante. Este volumen indica una campaña de denegación de servicio basada en paquetes SYN, dirigida a saturar servicios críticos.
- Thing_Speak: alrededor de 8.108 registros, asociado a tráfico IoT que interactúa con la plataforma ThingSpeak, aunque en este dataset se etiqueta como escenario de ataque.
- ARP_poisoning: cerca de 7.750 registros, lo que evidencia intentos de manipulación de la tabla ARP para redirigir o interceptar tráfico dentro de la red local.
- MQTT_Publish: unos 4.146 registros, relacionados con tráfico MQTT etiquetado como actividad sospechosa o parte de un escenario de ataque.
- Escaneos NMAP (UDP_SCAN, TCP_scan, XMAS_TREE_SCAN, FIN_SCAN, OS_DETECTION): miles de registros distribuidos entre diferentes técnicas de reconocimiento, lo que indica una fase activa de exploración de puertos y servicios.
- Slowloris: aproximadamente 534 registros, caracterizados por conexiones HTTP prolongadas destinadas a agotar recursos del servidor.
- SSH brute force: alrededor de 37 registros, representando intentos de acceso no autorizado mediante fuerza bruta.


La presencia de estos ataques, especialmente el volumen masivo de SYN Flood y la variedad de técnicas de escaneo, demuestra que la red no solo opera con tráfico IoT legítimo, sino que también es objetivo de múltiples campañas de ataque. La diferencia entre tráfico normal y malicioso es evidente tanto en los servicios utilizados como en los patrones de flujo, los puertos destino y los indicadores de comportamiento (SYN/ACK, duración de flujos, dispersión de puertos).
En conjunto, el Dataset 2 proporciona una visión clara de cómo se comporta una red IoT bajo condiciones normales y bajo ataque. La alta frecuencia de ciertos ataques y la diversidad de técnicas empleadas lo convierten en un recurso adecuado para el estudio de detección de intrusiones, clasificación de tráfico y análisis de anomalías. Este análisis establece una base sólida para continuar con el estudio del Dataset 3.

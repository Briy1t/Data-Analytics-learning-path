# Análisis de Logs de Servidores Linux
Proyecto de análisis de datos orientado a la detección de patrones, actividad sospechosa y comportamiento interno/externo en servidores Linux utilizando datasets públicos.

## 1. Descripción general del proyecto
Este proyecto tiene como objetivo analizar diferentes tipos de logs provenientes de servidores Linux para identificar:
- Patrones de comportamiento normal
- Actividad sospechosa
- Errores frecuentes
- Indicadores de posibles ataques
- Diferencias entre tráfico externo e interno
- Señales tempranas de intrusión
- El análisis se realiza utilizando técnicas de análisis de datos y conceptos básicos de ciberseguridad, con el fin de comprender cómo se comporta un servidor expuesto a Internet y qué eventos permiten detectar anomalías.

## 2. Pregunta principal
¿Qué patrones de comportamiento y qué señales de actividad sospechosa se pueden identificar en los logs de un servidor Linux?

## 3. Alcance del proyecto
El proyecto incluye:
- Limpieza y preparación de datos
- Análisis exploratorio
- Consultas SQL sobre grandes volúmenes de logs
- Identificación de patrones y anomalías
- Comparación entre datasets
- Documentación de hallazgos
- Herramientas utilizadas:
- Python (pandas)
- SQL (SQLite / DBeaver)
- Excel
- Tableau / Looker Studio
- Linux (contexto técnico)

### Conceptos aplicados:
- Autenticación
- Fuerza bruta
- Escaneo de puertos
- Escalada de privilegios
- Actividad interna del sistema
- Anomalías geográficas

## 4. Consideraciones éticas y de calidad de datos
Los datasets provienen de Kaggle, lo que implica:
- No se controla el sesgo original
- Se documentan inconsistencias cuando aparecen
- No se utilizan datos sensibles
- El análisis se centra en comportamiento del sistema, no en personas
- Se utilizan múltiples datasets para reducir sesgo y validar patrones

## 5. Datasets utilizados
El proyecto emplea tres fuentes principales:

### Web Server Access Logs
Tráfico web real, errores, bots, picos de tráfico.

### RT-IoT2022
Ataques reales: SSH brute force, DDoS, Slowloris, Nmap.

### linux_auth_log-anomalies
Eventos internos del sistema: autenticación, sudo, cron, escalada de privilegios.

- Cada dataset se analiza por separado y luego se comparan patrones entre ellos.

## 6. Flujo analítico (Ask → Prepare → Process → Analyze → Share → Act)
### Ask
Definición de preguntas clave:
- ¿Qué actividad es normal?
- ¿Qué actividad podría indicar un ataque?
- ¿Qué IPs generan más tráfico?
- ¿Qué usuarios fallan más autenticaciones?
- ¿Qué servicios son más atacados?

### Prepare
- Descarga de datasets
- Revisión de estructura
- Limpieza inicial
- Conversión a CSV limpio
- Creación de tablas SQL

### Process
- Parsing de logs con Python
- Extracción de columnas relevantes
- Normalización de formatos
- Eliminación de ruido

### Analyze
- Análisis exploratorio
- Consultas SQL
- Identificación de anomalías
- Comparación entre datasets

### Share
- Visualizaciones en Tableau
- Documentación por dataset

### Act
- Recomendaciones de seguridad
- Hardening básico
- Alertas basadas en patrones detectados

## 7. Project Charter
**Propósito**
- Analizar logs de servidores Linux para identificar patrones de comportamiento, actividad automatizada, escaneo masivo y señales tempranas de actividad sospechosa.

- **Actividades principales**
  - Selección de datasets

- **Limpieza y normalización**
  - Consultas SQL
  - Identificación de patrones
  - Documentación de hallazgos
  - Comparación entre datasets

- **Fuera de alcance**
  - Modelos predictivos
  - Machine learning
  - IDS reales
  - Análisis de malware
  - Logs privados o sensibles

- **Entregables**
  - CSV limpio por dataset
  - Consultas SQL documentadas
  - Informe por dataset
  - Comparación entre datasets

- **Informe final**

- **Cronograma**
  - Basado en trabajo semanal, con una duración estimada de 10 semanas.

## 8. Documentos incluidos en el repositorio
A continuación se presenta la estructura completa del repositorio, organizada por categorías y con una breve descripción de cada archivo.

---

## 1. Documentación inicial del proyecto

| Archivo | Descripción |
|--------|-------------|
| **Inicio_del_proyecto.md** | Explica el punto de partida, objetivos iniciales y alcance general. |
| **PROJECT_CHARTER_Análisis_Logs_Servidores_Linux.md** | Documento formal del proyecto: propósito, alcance, entregables, metodología y criterios de éxito. |

---

## 2. Análisis de los datasets principales

### Dataset 1 – Tráfico Web

| Archivo | Descripción |
|--------|-------------|
| **Analisis_dataset_1.md** | Análisis completo del Dataset 1: limpieza, patrones de tráfico, proveedores, rangos IP, bots y escáneres. |

---

### Dataset 2 – Tráfico IoT

| Archivo | Descripción |
|--------|-------------|
| **analisis_dataset2.md** | Análisis del Dataset 2: tráfico IoT normal vs ataques etiquetados (SYN Flood, ARP poisoning, NMAP, Slowloris, SSH brute force). |

---

###  Dataset 3 – Logs de Autenticación Linux

Este dataset se divide en tres subconjuntos (3.1, 3.2 y 3.3). Cada uno tiene su propio análisis.

| Archivo | Descripción |
|--------|-------------|
| **Dataset_3.1.md** | Análisis del subconjunto 3.1: actividad SSH, procesos internos, intentos fallidos y distribución geográfica. |
| **Dataset_3,2.md** | Análisis del subconjunto 3.2: escalada de privilegios, escaneos internos y anomalías. |
| **DataSet_3_3.md** | Análisis del subconjunto 3.3: fuerza bruta distribuida, diccionarios de usuarios, servicios críticos y protocolos inseguros. |
| **Conclusión_Consolidada_del_Dataset_3_(3.1, 3.2 y 3.3).md** | Documento que integra las conclusiones de los tres subconjuntos del Dataset 3. |

---

## 3. Integración y comparativas

| Archivo | Descripción |
|--------|-------------|
| **Comparación_Final.md** | Comparación entre los tres datasets principales (1, 2 y 3) para detección de amenazas. |
| **Informe_Final.md** | Informe final del proyecto: metodología, análisis, visualizaciones, conclusiones y trabajo futuro. |

---

## 4. Recursos adicionales

| Carpeta | Descripción |
|--------|-------------|
| **imagenes/** | Contiene los gráficos generados en Excel para los análisis del Dataset 3. |

---

## Estado actual del repositorio

### ✔ Completado
- Dataset 1  
- Dataset 2  
- Dataset 3.1  
- Dataset 3.2  
- Dataset 3.3  
- Conclusión consolidada del Dataset 3  
- Comparación final  
- Informe final  
- Documentación inicial  
- Carpeta de imágenes  




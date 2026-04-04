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
- ![Inicio_del_proyecto.md](SecLogAnalyzer:%20Multi‑Dataset%20Linux%20Threat%20Detection/Inicio_del_proyecto.md)
- ![PROJECT_CHARTER_Análisis_Logs_Servidores_Linux.md](SecLogAnalyzer:%20Multi‑Dataset%20Linux%20Threat%20Detection/PROJECT_CHARTER_Anális_Logs_Servidores_Linux.md)
- ![Imagenes](SecLogAnalyzer:%20Multi‑Dataset%20Linux%20Threat%20Detection/imagenes)
  
## 9. Estado actual del proyecto
Completado:
- ![Dataset 1](SecLogAnalyzer:%20Multi‑Dataset%20Linux%20Threat%20Detection/Analisis_dataset_1.md)
- ![Dataset 2](SecLogAnalyzer:%20Multi‑Dataset%20Linux%20Threat%20Detection/analisis_dataset2.md)
- ![Dataset 3.1](SecLogAnalyzer:%20Multi‑Dataset%20Linux%20Threat%20Detection/Dataset_3.1.md)
- ![Dataset 3.2](SecLogAnalyzer:%20Multi‑Dataset%20Linux%20Threat%20Detection/Dataset_3,2.md)

---
En progreso:
- Dataset 3.3
- Análisis de los tres datasets grandes
- Comparación final
- Informe final

## 10. Próximos pasos
- Finalizar análisis del Dataset 3.3
- Integrar conclusiones de los tres sub-datasets
- Analizar los datasets grandes
- Generar visualizaciones finales
- Redactar informe final
- Publicar dashboard



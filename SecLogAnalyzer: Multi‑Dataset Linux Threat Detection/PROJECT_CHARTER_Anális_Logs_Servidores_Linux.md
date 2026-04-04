# PROJECT CHARTER – Análisis de Logs de Servidores Linux
- **Data Analys**t: Liset
- **Cliente/Patrocinador**: Proyecto académico / investigación personal en ciberseguridad

## 1. Purpose (Propósito del proyecto)
- El propósito de este proyecto es analizar logs de servidores Linux utilizando datasets públicos para identificar patrones de comportamiento, repetición de IPs, hostnames asociados, actividad automatizada, escaneo masivo y señales tempranas de actividad sospechosa.
- El análisis se centra exclusivamente en la información disponible en los datasets (principalmente IP y hostname), con el objetivo de comprender cómo se comporta un servidor expuesto a Internet y qué indicadores permiten detectar amenazas básicas.

## 2. Scope / Major Project Activities (Alcance y actividades principales)
|Actividad|	Descripción|
|:--|:--|
|Selección de datasets	|Descarga de datasets desde Kaggle y repositorios que incluyen tráfico web, actividad SSH y escaneos (incluyendo ZMap). |
|Preparación de datos	|Limpieza básica con Python (pandas), extracción de IP y hostname, normalización y exportación a CSV. |
|Revisión manual	|Validación del CSV en Excel para confirmar consistencia y estructura.|
|Consultas SQL	|Conteo de IPs repetidas, detección de hostnames reales vs no resueltos, agrupación por proveedor y análisis de rangos.|
|Identificación de patrones |	Detección de actividad automatizada, escaneo, nodos TOR, VPS repetitivos y tráfico anómalo.|
|Documentación de hallazgos |	Registro de patrones observados en cada dataset y comparación entre ellos.|
|Revisión semanal	|Avance del proyecto una vez por semana, incorporando nuevos datasets según necesidad.|

## 3. This project does not include (Fuera de alcance)
- No se realizará análisis predictivo ni modelos de machine learning.
- No se analizarán rutas HTTP, métodos o códigos de estado cuando el dataset no los incluya.
- No se implementarán sistemas de detección de intrusos.
- No se trabajará con logs reales de empresas ni datos sensibles.
- No se hará ingeniería inversa de malware.

## 4. Deliverables (Entregables)
|Deliverable	|Descripción|
|:--|:--|
|CSV limpio por dataset |	Archivo depurado con IP y hostname listos para análisis.|
|Consultas SQL documentadas |	Consultas utilizadas para identificar repeticiones, proveedores y rangos.|
|Informe por dataset |	Documento con patrones detectados, actividad sospechosa y conclusiones preliminares.|
|Comparación entre datasets	|Identificación de coincidencias entre tráfico web, SSH y escaneos.|
|Informe final |	Resumen completo del proyecto con hallazgos y patrones generales.|

## 5. Schedule Overview / Major Milestones (Cronograma y hitos)
(Basado en trabajo una vez por semana)

|Milestone	|Fecha estimada	| Descripción|
|:--|:--|:--|
|Selección y descarga de datasets	|Semana 1	|Revisión inicial y validación de estructura.|
|Limpieza y preparación del Dataset 1	|Semana 2	|Extracción de IP y hostname, CSV limpio.|
|Análisis SQL del Dataset 1|	Semana 3|	Repeticiones, proveedores, rangos.|
|Documentación del Dataset 1|	Semana 4	|Informe preliminar.|
|Limpieza y análisis del Dataset 2 	| Semanas 5–6	|Repeticiones, patrones internos, actividad sospechosa.|
|Limpieza y análisis del Dataset 3 	|Semanas 7–8	|Identificación de escaneo masivo.|
|Comparación entre datasets	|Semana 9	|Coincidencias entre IPs, proveedores y patrones.|
|Informe final|Semana 10|	Documento completo del proyecto.|

6. Estimated date for completion (Fecha estimada de finalización)
Aproximadamente 10 semanas, considerando que el trabajo se realiza una vez por semana.
Inicio 20/03/2026
Final estimado  29/05/2026

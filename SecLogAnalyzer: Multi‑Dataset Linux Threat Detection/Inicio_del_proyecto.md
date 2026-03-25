# Inicio del Proyecto
## 1. Planteamiento inicial
Este proyecto tiene como objetivo analizar logs de servidores Linux para identificar patrones de comportamiento, actividad normal, actividad sospechosa, errores frecuentes e indicadores de posibles ataques.
El propósito es comprender cómo se comporta un servidor expuesto a Internet y qué señales permiten detectar amenazas de forma temprana.

## 2. Pregunta principal
¿Qué patrones de comportamiento y qué señales de actividad sospechosa se pueden identificar en los logs de un servidor Linux?

## 3. Alcance del proyecto
El análisis se realizará utilizando herramientas de análisis de datos y ciberseguridad:
- **Python (pandas)** para limpieza, parsing y análisis exploratorio
- **SQL** para consultas sobre grandes volúmenes de logs
- **Excel** para KPIs rápidos
- **Tableau/Looker** para visualización
- **Linux** para el contexto técnico
- Conceptos de ciberseguridad para detección de anomalías

## 4. Consideraciones éticas y de calidad de datos
Los datasets provienen de Kaggle. Esto implica:
- No se controla el sesgo original del dataset
- Sí se debe detectar, documentar y mitigar sesgos cuando sea posible
- Se evita el uso de datos sensibles
- El análisis se centra en comportamientos del sistema, no en personas
- Se utilizarán tres datasets distintos para reducir sesgo y validar patrones
- Se podran añadir mas dataset si se ve necesario a medida del desarollo del proyecto 

## 5. Selección de datasets
Para evitar conclusiones erróneas, se seleccionaron datasets con:
- Volumen suficiente
- Diversidad de fuentes
- Diferentes tipos de actividad (normal, maliciosa, interna)
- Formatos compatibles con análisis técnico

### Datasets utilizados
- Web Server Access Logs: tráfico web real, errores, bots, picos de tráfico
- RT-IoT2022: ataques reales (SSH brute force, DDoS, Slowloris, Nmap)
- linux_auth_log-anomalies: eventos internos del sistema

## 6. Flujo analítico (Ask → Prepare → Process → Analyze → Share → Act)
1. **Ask**
- Definir preguntas clave:
  - ¿Qué actividad es normal en el servidor?
  - ¿Qué actividad podría indicar un ataque?
  - ¿Qué IPs generan más tráfico?
  - ¿Qué rutas generan más errores?

2. **Prepare**
- Descargar datasets
- Revisar estructura
- Detectar inconsistencias
- Convertir a CSV limpio
- Crear tablas SQL

3. **Process**
- Parsear logs con Python
- Extraer columnas (IP, fecha, método, código, recurso, user agent)
- Limpiar datos
-  Normalizar formatos

4. **Analyze**
- Python para análisis exploratorio
- SQL para consultas sobre patrones
- Excel para KPIs
- Detección de anomalías

5. **Share**
- Dashboard en Tableau

6. **Act**
- Recomendaciones de seguridad
- Hardening
- Alertas

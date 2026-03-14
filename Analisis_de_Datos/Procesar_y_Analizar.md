# PROCESAR DATOS
El objetivo de este paso es limpiar, validar, transformar y preparar los datos para que puedan analizarse sin errores.

1.1. Limpieza de datos
Errores más comunes
Valores nulos

Duplicados

Tipos de datos incorrectos

Formatos inconsistentes

Datos incompletos

Datos desactualizados

Espacios invisibles

Categorías mal escritas

Técnicas de limpieza
Eliminación de duplicados

Corrección de tipos de datos

Normalización de texto (mayúsculas/minúsculas)

Eliminación de espacios (TRIM)

Reemplazo de valores (REPLACE)

Conversión de formatos (fechas, números)

Detección de outliers

1.2. Validación de datos
Qué validar
Rango de valores

Campos obligatorios

Formatos correctos

Relaciones entre columnas

Coherencia entre tablas

Unicidad de claves

Existencia de claves foráneas

Ejemplos
Edad entre 0 y 120

Fechas válidas y no futuras

Porcentajes que suman 100%

ID único por fila

Estado que exista en tabla de referencia

1.3. Transformación de datos
Transformaciones comunes
Crear columnas derivadas

Convertir tipos (texto → número, número → fecha)

Agrupar categorías

Mapear valores entre sistemas

Unificar formatos

Reordenar columnas

Fusionar datasets

Ejemplos
Extraer año, mes, día de una fecha

Calcular total = precio × cantidad

Normalizar nombres de ciudades

Crear rangos de edad

1.4. Procesamiento con Excel
Funciones útiles
TRIM

LEFT, RIGHT, MID

LEN

COUNTIF

CONCATENATE

SPLIT

Formato condicional

Validación de datos

1.5. Procesamiento con SQL
Limpieza
sql
SELECT *
FROM tabla
WHERE columna IS NOT NULL;
Normalización
sql
UPDATE tabla
SET nombre = LOWER(nombre);
Detección de duplicados
sql
SELECT columna, COUNT(*)
FROM tabla
GROUP BY columna
HAVING COUNT(*) > 1;
Validación de claves foráneas
sql
SELECT *
FROM ventas v
LEFT JOIN clientes c
ON v.id_cliente = c.id
WHERE c.id IS NULL;
Transformación
sql
SELECT *,
       precio * cantidad AS total
FROM ventas;
2. ANALIZAR DATOS
El objetivo de este paso es explorar, identificar patrones, encontrar relaciones y responder preguntas.

2.1. Exploración inicial
Acciones típicas
Revisar estadísticas descriptivas

Identificar valores extremos

Analizar distribuciones

Explorar correlaciones

Revisar tendencias temporales

Herramientas
Tablas dinámicas

Gráficos básicos

Consultas SQL

Funciones estadísticas

2.2. Análisis descriptivo
Métricas comunes
Media

Mediana

Moda

Mínimo y máximo

Desviación estándar

Percentiles

Ejemplo en SQL
sql
SELECT 
    AVG(importe) AS media,
    MIN(importe) AS minimo,
    MAX(importe) AS maximo
FROM ventas;
2.3. Análisis de relaciones
Tipos de relaciones
Correlaciones entre variables numéricas

Comparaciones entre grupos

Relación entre categorías

Relación entre tiempo y valor

Ejemplos
Ventas por región

Ingresos por mes

Satisfacción por tipo de cliente

2.4. Análisis con Excel
Técnicas
Tablas dinámicas

Segmentaciones

Gráficos de líneas, barras, dispersión

Funciones estadísticas

Filtros avanzados

2.5. Análisis con SQL
Agrupaciones
sql
SELECT categoria, COUNT(*)
FROM productos
GROUP BY categoria;
Tendencias
sql
SELECT fecha, SUM(ventas)
FROM ventas
GROUP BY fecha
ORDER BY fecha;
Comparaciones
sql
SELECT region, AVG(importe)
FROM ventas
GROUP BY region;
2.6. Interpretación de resultados
Preguntas clave
¿Qué patrones aparecen?

¿Qué valores destacan?

¿Qué grupos se comportan diferente?

¿Qué tendencia sigue la serie temporal?

¿Qué relación existe entre variables?

Buenas prácticas
No asumir causalidad

Verificar datos antes de concluir

Comparar con periodos anteriores

Revisar valores atípicos

Documentar cada hallazgo

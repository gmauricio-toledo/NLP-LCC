# ANÁLISIS DE NOTICIAS UNIVERSITARIAS

## OBJETIVO

Desarrollar un pipeline completo de recolección, procesamiento y análisis de texto aplicado a las noticias de la Universidad de Sonora. Construir un corpus representativo y extraer insights sobre actividad institucional, departamentos más activos, colaboraciones entre unidades académicas y patrones temporales de publicación.

## INSTRUCCIONES GENERALES

1. Trabajarán en los equipos ya asignados.
2. Desarrollen el pipeline completo siguiendo los pasos descritos.
3. Documenten todas las decisiones técnicas y metodológicas.
4. Entreguen un solo Jupyter Notebook por equipo, sin errores, completamente ejecutado y comentado.
5. Incluir una conclusión sobre limitaciones y mejoras posibles.

---

## PASOS DE LA ACTIVIDAD

### 1. WEB SCRAPING Y CONSTRUCCIÓN DEL CORPUS

**Objetivo:** Recolectar un conjunto representativo de noticias del portal institucional.

**Especificaciones:**

a) Identificación del patrón URL
   - Fuente: https://www.unison.mx/noticias-anteriores/
   - Obtener el URL base y con ese, iterar para obtener todas las noticias usando IDs
   - Implementen manejo de errores para IDs inexistentes.
   - **IMPORTANTE**: Implementar una pausa de AL MENOS 1 segundo entre cada petición (time.sleep(1)). Esto evita saturar el servidor y que bloqueen su IP. Ejemplo básico:

      ```python
         import time
         import requests

         for id in range(id_inicio, id_fin):
            url = ...
            response = requests.get(url)
            
            # Procesar la página...
            
            time.sleep(1)  # PAUSA OBLIGATORIA
   - Si el sitio tiene robots.txt, revísenlo

b) Campos a extraer por cada noticia:
   - url: URL completa
   - titulo: Prueba con el texto dentro de <h1>. **Considerar usar beautiful soup**
   - fecha
   - autor: nombre del autor
   - texto: cuerpo completo de la noticia

c) Almacenamiento:
   - Guardar en un archivo CSV con columnas: url, titulo, fecha, autor, texto
   - El corpus final debe tener al menos 500 noticias (o justificar el tamaño alcanzado). Crédito extra si se obtienen todas las noticias.

d) Limpieza inicial:
   - Limpiar texto en caso de ser necesario
   - Estandarizar formato de fechas

---

### 2. ANÁLISIS EXPLORATORIO DEL CORPUS

**Especificaciones:**

a) Estadísticas básicas:
   - Número total de noticias
   - Rango de fechas cubierto
   - Número total de tokens (palabras)
   - Mostrar la gráfica de barras de la frecuencia de las palabras más frecuentes para verificar la ley de Zipf
 
b) Nube de palabras:
   - Generar una nube de palabras del corpus completo
   - Preprocesamiento mínimo: minúsculas, eliminar puntuación, eliminar stopwords en español
   - Añade palabras a la lista de stopwords de acuerdo a tu criterio

c) Palabras más frecuentes:
   - Top 20 palabras más frecuentes (sin stopwords)
   - Visualizar la gráfica de barras
   - Comparar con la nube de palabras

---

### 3. ANÁLISIS DE DEPARTAMENTOS

**Objetivo:** Identificar qué unidades académicas tienen mayor presencia en las noticias.

**Especificaciones:**

a) Patrón de búsqueda:
   - Identificar menciones a "Departamento de X", "Facultad de Y", "División de Z", "Licenciatura en W"
   - Usar expresiones regulares para capturar estas estructuras

b) Normalización:
   - Unificar variantes (ej. "Depto. de", "Departamento de", "Dpto.")
   - Crear una lista estandarizada de departamentos/unidades

c) Métricas:
   - Número de noticias que mencionan a cada departamento y a cada licenciatura
   - Top 5 departamentos más mencionados y licenciaturas más mencionadas

d) Visualización:
   - Gráfica de barras horizontales con los departamentos más activos/populares
   
---

### 4. ANÁLISIS DE LUGARES MENCIONADOS

**Objetivo:** Extraer y contabilizar referencias geográficas en las noticias.

**Especificaciones:**

a) Extracción de lugares:
   - Identificar menciones a: ciudades, campus, edificios
   - Hay dos opciones: Lista predefinida de lugares conocidos (Hermosillo, Caborca, Navojoa, Santa Ana, Nogales, etc.) o NER

b) Normalización:
   - Unificar variantes ("Hermosillo, Sonora", "Cd. de Hermosillo" → "Hermosillo")
   - Clasificar por tipo: campus, ciudad, instalación, etc

c) Visualización:
   - Top 10 lugares más mencionados
   - Gráfica de barras o treemap
   
---

### 5. ANÁLISIS TEMPORAL

**Objetivo:** Identificar patrones de publicación en el tiempo.

**Especificaciones:**

a) Preparación de datos:
   - Usar la columna de fecha en formato YYYY-MM-DD
   - Extraer: año, mes, día de la semana, semana del año

b) Análisis por época del año:
   - Agrupar por mes
   - Identificar meses con mayor/menor producción de noticias
   - Relacionar con el calendario académico (inicio de semestres, periodos vacacionales, exámenes, aniversarios)

c) Análisis por día de la semana:
   - Agrupar por día de la semana (lunes a domingo)
   - Determinar qué días se publican más noticias
   - ¿Hay publicación los fines de semana?
   - Sugerencia: puedes usar el módulo datetime

d) Visualizaciones:
   - Serie de tiempo: noticias por mes (gráfica de líneas)
   - Barras: noticias por día de la semana

---



## ENTREGABLES

### 1. Código (Jupyter Notebook completamente ejecutado)

El notebook debe incluir:

- Scraping y obtención corpus
- Pipeline de limpieza y preprocesamiento
- Implementación de cada análisis (puntos 2 al 5)
- Visualizaciones claras y bien etiquetadas
- Comentarios explicativos en celdas de código y celdas markdown
- La notebook debe poder ejecutarse de principio a fin sin errores

### 2. Archivo CSV del corpus

- Entregar el archivo CSV generado con todas las noticias recolectadas
- Incluir las columnas especificadas (url, titulo, fecha, autor, texto)

### 3. Reporte de análisis (dentro del mismo notebook)

Para cada sección (2 a 5) incluir:

- Breve descripción de la metodología empleada
- Resultados (tablas, gráficas)
- Interpretación de los resultados
- Hallazgos interesantes o inesperados

### 4. Reflexión crítica

Al final del notebook, incluir una sección de reflexión que aborde:

- Limitaciones del enfoque utilizado (scraping incompleto, errores en extracción, sesgos del corpus)
- Dificultades encontradas y cómo las resolvieron
- Qué mejorarían con más tiempo o recursos
- Qué otros análisis se podrían agregar

---

## CRITERIOS DE EVALUACIÓN

| Criterio | Porcentaje | Descripción |
|----------|------------|-------------|
| Web scraping y corpus | 15% | Rango adecuado, manejo de errores, campos completos, tamaño suficiente |
| Análisis exploratorio | 10% | Nube de palabras, frecuencias, visualizaciones correctas |
| Análisis de departamentos | 15% | Extracción correcta, normalización, top departamentos |
| Análisis de lugares | 15% | Extracción de ubicaciones, top lugares, visualización |
| Análisis temporal | 10% | Procesamiento de fechas, patrones por mes y día, visualizaciones |
| Análisis de colaboraciones | 20% | Construcción del grafo, métricas, visualización, interpretación |
| Documentación y reflexión | 15% | Código comentado, interpretaciones claras, reflexión crítica |

---

## NOTAS IMPORTANTES

- **No hacer scraping en cada ejecución**. Guardar el CSV y cargarlo directamente para los análisis.
- Para el análisis de lugares, pueden comenzar con una lista manual de ubicaciones conocidas y después expandir.
- NO olvidar implementar una pausa de AL MENOS 1 segundo entre cada petición.
- Documenten TODAS las decisiones de diseño y preprocesamiento.
- La reflexión crítica es tan importante como los resultados. No la omitan.

---
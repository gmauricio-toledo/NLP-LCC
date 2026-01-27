# PRÁCTICA: ANALIZADOR DE RESEÑAS CON TÉCNICAS DE PREPROCESAMIENTO

## OBJETIVO
Realizar un análisis de reseñas que integre las técnicas de preprocesamiento de texto vistas en clase (expresiones regulares, tokenización, normalización, stopwords, lematización, POS tagging, NER y pattern matching). El objetivo es extraer información estructurada y útil de textos no estructurados, simulando una aplicación real de NLP. Concretamente, queremos reportar los aspectos más asociados a los productos evaluados en un dataset de reseñas de Amazon.

## INSTRUCCIONES
1. Trabajarán en las parejas asignadas.
2. Dataset: https://drive.google.com/file/d/1NHyyALe8L-drfwTWeE_KK5bsHfzVF8jI/view?usp=sharing.
3. Desarrollen un pipeline completo de análisis siguiendo los detalles descritos abajo.
4. Documenten su código con comentarios explicativos.
5. Preparen los entregables especificados más adelante.

## DETALLES DE LA ACTIVIDAD

1. **Exploración inicial**
   - Carguen el dataset y examinen su contenido
   - Consideren el texto en las columnas apropiadas
   - Identifiquen problemas de calidad (textos vacíos, duplicados, caracteres extraños)
   - Realicen la limpieza necesaria: Remuevan URLs, caracteres especiales innecesarios, normalicen espacios en blanco
   - IMPORTANTE: Pueden auxiliarse de las columnas adicionales para obtener información valiosa

2. **Análisis exploratorio básico**
   - Distribución de longitudes de reseñas
   - Palabras más frecuentes
   - Sustantivos más frecuentes
   - Nube de palabras de sustantivos
   - Guarda una lista de sustantivos que sean productos o aspectos importantes de productos (ej: "batería", "pantalla", "teléfono", "computadora")
   - Creen una lista definitiva de aspectos a analizar (entre 20-30 aspectos)
   - Justifiquen brevemente su selección

4. **Extracción de opiniones asociadas a aspectos**
   
   Para cada aspecto identificado, recorran las reseñas y extraigan:
   
   a) **Adjetivos modificadores directos**
      - Identifiquen adjetivos que modifiquen directamente al sustantivo
      - Ejemplo: en "la pantalla es hermosa", extraer "hermosa" para el aspecto "pantalla"
   
   b) **Patrones de intensificación**
      - Busquen construcciones: Adverbio + Adjetivo cerca del aspecto
      - Ejemplo: "muy bueno", "bastante malo", "demasiado caro", "poco resistente"
   
   c) **Construcciones verbo + adverbio/adjetivo**
      - Identifiquen cuando el aspecto es sujeto u objeto de un verbo seguido de adverbio o adjetivo
      - Ejemplo: "la batería dura poco", "funciona perfectamente", "se calienta mucho"

5. **Recopilación y estructuración de resultados**
   
   Para cada aspecto identificado, generen un resumen que incluya:
   - Frecuencia de mención del aspecto
   - Top 10 adjetivos/descriptores más asociados (con frecuencias)
   - Conteo de menciones positivas vs negativas (basado en polaridad de adjetivos)
   - 3-5 ejemplos de fragmentos de texto representativos **en lenguaje natural** para algunos aspectos
   - Para 3-5 aspectos principales: haz una nube de palabras de todos los textos que mencionen estos aspectos (quita stopwords y lematiza)
   - Hallazgos interesantes o patrones inesperados

## ENTREGABLES

### Código (Jupyter Notebook)
Debe incluir:
- Pipeline de preprocesamiento completo y modular
- Funciones para extracción de patrones
- Análisis y visualizaciones
- Comentarios explicativos en el código





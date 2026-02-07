# PRÁCTICA: MODELO DE LENGUAJE CON N-GRAMAS

## OBJETIVO
Implementar un modelo de lenguaje basado en n-gramas y evaluar el impacto de diferentes decisiones de preprocesamiento en la calidad del texto generado. Esta práctica integra técnicas de web scraping, preprocesamiento de texto, construcción de modelos probabilísticos y generación de lenguaje natural.

## INSTRUCCIONES
1. Trabajarán en los equipos asignados.
2. Cada equipo tiene asignada una configuración específica (ver tabla de ASIGNACIONES).
3. Desarrollen el pipeline completo siguiendo los pasos descritos.
4. Comparen los resultados de su configuración (on vs off) y documenten las diferencias.
5. Preparen los entregables especificados.

## PASOS DE LA ACTIVIDAD

### 1. OBTENCIÓN DEL CORPUS

Recopilen texto de las siguientes tres fuentes:

a) **Wikipedia (scraping)**: Extraigan texto de al menos 3-5 artículos relacionados con un tema específico (justificar la elección del tema/artículos)

b) **Conversaciones de WhatsApp**
   - Exporten una o varias conversaciones
   - Pueden ser conversaciones personales o de grupos (recuerden la discusión sobre la privacidad)
   - Asegúrense de limpiar información personal sensible

c) **Textos propios**
   - Incluyan textos de trabajos académicos, ensayos, o documentos propios (es muy importante que sean documentos que hayan redactado ustedes)
   - Al menos 3 documentos

**Nota:** El corpus combinado debe tener al menos 10,000 tokens (palabras) para resultados razonables.

### 2. PREPROCESAMIENTO Y LIMPIEZA

Implementen un pipeline de preprocesamiento con las siguientes opciones:

- **Stopwords:** mantener o eliminar
- **Dígitos:** mantener, reemplazar por token especial (ej: `<NUM>`), o eliminar
- **Puntuación:** mantener o eliminar
- **Lowercase:** convertir todo a minúsculas o mantener mayúsculas/minúsculas originales
- **Tokens de inicio/fin:** agregar tokens especiales `<START>` y `<END>` al inicio y fin de cada oración/documento

**IMPORTANTE:** Según su asignación, deberán probar su variable asignada en modo ON y OFF, manteniendo el resto de opciones con valores fijos (ustedes deciden cuáles). Documenten claramente qué configuración fija usaron.

**Ejemplo:** Si les tocó "stopwords", probarán:
- Configuración A: stopwords=OFF (eliminadas)
- Configuración B: stopwords=ON (mantenidas)
- Resto: lowercase=ON, puntuación=OFF, dígitos=eliminar, tokens inicio/fin=ON (fijos a decisión de ustedes)

### 3. ENTRENAMIENTO DEL MODELO DE N-GRAMAS

Implementen un modelo de n-gramas con las siguientes características:

a) **Construcción del modelo**
   - Generen todos los n-gramas del corpus preprocesado
   - Calculen las probabilidades de transición
   - Usen el valor de n asignado en la tabla (n=2, 3, o 4).
   - Pueden usar de base las funciones de clase, sin embargo, sientanse en toda la libertad de hacer las modificaciones que prefieran y necesiten.

### 4. GENERACIÓN DE TEXTO

Generen texto usando su modelo entrenado:

a) **Semillas de generación**
   - **Semilla fija (obligatoria):** "ayer fue"
   - **4 semillas libres:** elijan 4 semillas diferentes relacionadas con su corpus

b) **Proceso de generación**
   - Empiecen con la semilla
   - Generen entre 50-100 tokens (palabras) por semilla. Escojan este valor.

c) **Experimentos**
   - Generen texto con ambas configuraciones (ON y OFF de su variable asignada)
   - Anoten diferencias cualitativas en coherencia, fluidez, y naturalidad

### 5. ANÁLISIS Y COMPARACIÓN

Para cada configuración (ON y OFF), reporten:

a) **Estadísticas del modelo**
   - Número total de n-gramas únicos generados
   - Tamaño del vocabulario (palabras únicas)
   - Top 10 n-gramas más frecuentes

b) **Calidad del texto generado**
   - Presentar los 5 textos generados (1 fijo + 4 libres) para cada configuración
   - Evaluación subjetiva de coherencia (escala 1-5)
   - Identificar patrones interesantes o errores comunes

c) **Comparación ON vs OFF**
   - ¿Cuál configuración genera texto más coherente?
   - ¿Cómo afecta la naturalidad del texto?

## ENTREGABLES

### 1. Código (Jupyter Notebook **ejecutada**)
Debe incluir:
- Scripts de scraping o carga de datos
- Pipeline de preprocesamiento (claramente documentado)
- Implementación del modelo de n-gramas
- Función de generación de texto
- Análisis y visualizaciones
- Comentarios explicativos en cada sección
- Reflexión crítica (10%)**
   - Limitaciones del modelo
   - ¿Qué mejorarían con más tiempo?



## ASIGNACIONES

| Equipo | Variable experimental | Valor de n | Notas |
|--------|----------------------|------------|-------|
| Equipo 1 | Puntuación (on/off) | n=2 | |
| Equipo 2 | Tokens inicio/fin (on/off) | n=3 | Generación con top-k sampling |
| Equipo 3 | Stopwords (on/off) | n=4 | Generación con top-k sampling |
| Equipo 4 | Dígitos (mantener/eliminar) | n=2 | Generación con top-k sampling |
| Equipo 5 | Lowercase (on/off) | n=3 | |
| Equipo 6 | Dígitos (mantener/eliminar) | n=4 | |
| Equipo 7 | Puntuación (on/off) | n=2 | |
| Equipo 8 | Stopwords (on/off) | n=3 | |
| Equipo 9 | Puntuación (on/off) | n=4 | |
| Equipo 10 | Dígitos (mantener/eliminar)  | n=2 | |
| Equipo 11 | Lowercase (on/off) | n=3 | |
| Equipo 12 | Lowercase (on/off) | n=4 | |
| Equipo 13 | Stopwords (on/off) | n=2 | |
| Equipo 14 | Tokens inicio/fin (on/off) | n=3 | |
| Equipo 15 | Tokens inicio/fin (on/off) | n=4 | |

## CRITERIOS DE EVALUACIÓN

- **Recopilación del corpus (10%)**: Diversidad de fuentes, tamaño adecuado, limpieza de datos sensibles
- **Preprocesamiento (20%)**: Pipeline completo, configuraciones claras y bien documentadas
- **Implementación del modelo (20%)**: Correcta construcción de n-gramas, cálculo de probabilidades
- **Generación de texto (20%)**: Funcionalidad correcta, variedad de semillas
- **Análisis comparativo (20%)**: Comparación ON vs OFF bien fundamentada, insights relevantes
- **Documentación (10%)**: Código comentado, presentación clara y bien estructurada


## NOTAS IMPORTANTES

- Asegúrense de limpiar información personal sensible de las conversaciones de WhatsApp
- NO usen librerías que implementen n-gramas automáticamente (nltk.ngrams está bien para generar n-gramas, pero calculen probabilidades ustedes)
- Documenten todas las decisiones importantes
- Si tienen dudas sobre su asignación o implementación, preguntar en clase o por mensaje
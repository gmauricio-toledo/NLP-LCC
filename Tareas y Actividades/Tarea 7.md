### Clasificación con modelos neuronales clásicos

**Objetivo**: Implementar un clasificador de sentimientos usando representaciones vectoriales densas y comparar clasificadores de Machine Learning.

**Corpus**: 
- https://drive.google.com/file/d/17W3bObZBL6XQVsVMSvkNildhsFSjsmhV/view?usp=sharing

**Instrucciones**:
1. Análisis Exploratorio, Limpieza, Normalización, Balance de clases.
2. División Train/Test (prestar atención a la distribución de clases) y Preprocesamiento
3. Crear features con embeddings densos a partir de 
   1. Modelo entrenado en el corpus, escoger word2vec o fasttext.
   2. Modelo preentrenado, escoger modelos de gensim
   3. Doc2vec  
4. Entrenar y evaluar. Escoger 3 clasificadores y usarlos en cada una de las 3 estrategias del punto anterior. En total son 9 modelos 
5. Optimizar hiperparámetros. 
6. ¿Es posible obtener la importancia de las palabras? Piensa tu respuesta y comentala en clase, no es necesario implementarlo.
7. En tu mejor modelo (respecto a F1-score), muestra dos ejemplos de falsos positivos y falsos negativos, ¿qué notas en ellos?
8. Llena las entradas correspondientes en la tabla de resultados del excel de la sección de archivos de Teams.

**Métricas**:
- Accuracy, F1-score
- Matriz de confusión

En la presentación en clase incluir limitaciones del modelo, además, averiguar posibles estrategias para abordar estas limitaciones que se podrán usar. También incluir cualquier aspecto relevante que hayan encontrado o entendido durante el desarrollo del proyecto.

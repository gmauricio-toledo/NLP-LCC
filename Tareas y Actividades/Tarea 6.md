### Proyecto 2: Clasificación de Sentimiento con BOW/TF-IDF

**Objetivo**: Implementar un clasificador de sentimientos usando representaciones BOW/TF-IDF con diferentes n-gram ranges y comparar clasificadores de Machine Learning.

**Corpus**: 
- https://drive.google.com/file/d/17W3bObZBL6XQVsVMSvkNildhsFSjsmhV/view?usp=sharing

**Instrucciones**:
1. Análisis Exploratorio, Limpieza, Normalización, Balance de clases.
2. División Train/Test (prestar atención a la distribución de clases) y Preprocesamiento
3. Crear features con CountVectorizer y TfidfVectorizer (probar ngram_range=(1,1), (1,2), (1,3)). Ajustar el hiperparámetro `max_features`.
4. Entrenar y evaluar. Escoger 3 modelos: Logistic Regression (LR), Naive Bayes Multinomial (NB), SVC, Red MLP, Decision Tree (DT), Random Forest (RF), Vecinos más cercanos.
5. Optimizar hiperparámetros. 
6. Analizar features más importantes para cada modelo (LR, DT, RF y NB), presentar a qué n-gramas/tokens se refieren. 
7. Crea un modelo tomando en cuenta alguna combinación de: sustantivos, verbos, adjetivos, adverbios.
8. En tu mejor modelo, muestra dos ejemplos de falsos positivos y falsos negativos, ¿qué notas en ellos?

**Métricas**:
- Accuracy, F1-score
- Matriz de confusión

En la presentación incluir limitaciones del modelo, además, averiguar posibles estrategias para abordar estas limitaciones y estrategias más avanzadas que se podrán usar. También incluir cualquier aspecto relevante que hayan encontrado o entendido durante el desarrollo del proyecto.
## Ana, Georgina, Denisse

### 1. Implementar la métrica del concurso (RP Score)

La métrica es una F1 ponderada, hay que modificar esta función para que los pesos ya estén fijos, son los del nuestro corpus de entrenamiento, y no los calcule cada vez (por varias razoneS):

```python
from sklearn.metrics import f1_score
import numpy as np

def rp_score(y_true, y_pred):
    classes = ...
    total = len(y_true)
    counts = {c: np.sum(np.array(y_true) == c) for c in classes}
    
    weights = {c: 1 - counts[c] / total for c in classes}
    f1_per_class = f1_score(y_true, y_pred, labels=classes, average=None, zero_division=0)
    
    numerator = sum(weights[c] * f1_per_class[i] for i, c in enumerate(classes))
    denominator = sum(weights[c] for c in classes)
    
    return numerator / denominator
```

De ahora en adelante esta es la métrica para seleccionar el mejor clasificador.

---

### 2. Finetuning de modelos BERT

Continuar con modelos BERT. Probar dos condiciones:

**Sin pesos en la loss:**
```python
loss_fn = CrossEntropyLoss()
```

**Con pesos inversos a la frecuencia de clases en el corpus:**
```python
import torch
import numpy as np

counts = np.array([n1, n2, n3, n4, n5])  # frecuencias reales de cada clase
weights = 1 / counts
weights = weights / weights.sum()
weights = torch.tensor(weights, dtype=torch.float)

loss_fn = CrossEntropyLoss(weight=weights)
```

Comparar ambas condiciones siempre con `rp_score`. Re-evaluar también con
esta métrica algunos de los modelos ya entrenados previamente.

---

## Braulio

### 1. Histograma de longitudes por clase de polaridad

Para cada clase de polaridad (1–5) graficar la distribución de longitudes. Graficar por clase: media, desviación estándar y cuartiles (Q1, Q2, Q3).

### 2. Top-100 palabras por clase de polaridad (TF-IDF)

Para cada clase de polaridad:
- Preprocesar: eliminar stopwords, signos de puntuación y normalizar
- Construir la matriz TF-IDF con todos los documentos de esa clase
- Sumar por `axis=0` para obtener el peso acumulado de cada término
- Ordenar de mayor a menor y extraer los 100 primeros términos

El resultado es una lista de los 100 términos más representativos
por clase de polaridad.

---

## Jorge

### 1. Distribución de polaridad por Type

Para cada tipo (Hotel, Restaurant, Attractive) graficar la distribución
de clases de polaridad (pie chart).

### 2. Topic modeling LSA por combinación Type × Polaridad

Son 15 combinaciones en total (3 types × 5 clases de polaridad).

**Condición:** solo aplicar LSA si la celda tiene al menos 50 documentos.

**Procedimiento por celda:**
- Preprocesar el texto (stopwords, puntuación, normalización)
- Aplicar TF-IDF + TruncatedSVD con máximo 10 tópicos
- Extraer las palabras principales de cada tópico

El objetivo aquí es identificar qué aspectos turísticos dominan en cada combinación. Por ejemplo, ¿en Hotels la polaridad 2 concentra quejas de servicio? ¿en Restaurants la polaridad 2 concentra quejas de precio?
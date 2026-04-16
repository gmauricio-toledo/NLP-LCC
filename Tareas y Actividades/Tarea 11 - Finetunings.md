### Tarea 11: Fine-tuning de Modelos (BERT, LLM, PEFT)

**Objetivo**: Implementar un clasificador de sentimientos usando tres enfoques de fine-tuning y comparar su rendimiento, tiempo de entrenamiento y eficiencia paramétrica.

**Corpus**: 
- https://drive.google.com/file/d/17W3bObZBL6XQVsVMSvkNildhsFSjsmhV/view?usp=sharing

**Referencias**:
- Tutorial oficial PEFT (configuraciones y modelos): https://huggingface.co/docs/peft/tutorial/peft_model_config

---

## Instrucciones generales

Para cada enfoque (BERT fine-tuning, LLM fine-tuning completo, PEFT con LoRA), deberán documentar:
- **Tiempo de entrenamiento** (en segundos o minutos)
- **Métricas**: Accuracy, F1-score, matriz de confusión
- **Hiperparámetros principales** usados (learning rate, batch size, épocas, etc.)
- **Número de parámetros entrenables** (absoluto y porcentaje respecto al total)

Al final, llenarán la tabla de resultados en el archivo Excel `IMDB50K Scores.xlsx` de la sección de archivos del TEAMS con la información correspondiente para cada enfoque.

---

## Parte 1: Fine-tuning de BERT

Usar un modelo BERT preentrenado (tomar en cuenta el idioma) y hacer fine-tuning.

**Pasos**:
1. Cargar y preprocesar el dataset.
2. Dividir en train/test (estratificado por clases), usa las mismas proporciones de las iteraciones pasadas de esta actividad.
3. Hacer finetuning con las 3 estrategias usando HuggingFace. Para el finetuning de LLM usando un modelo de más de 1B de parámetros y menos de 10B.
4. Registrar tiempo de entrenamiento (desde el inicio hasta el final del entrenamiento). **Sólo el tiempo de entrenamiento**
5. Evaluar en test set.

**Entregables**:
- Registro de Métricas (accuracy, F1, matriz de confusión), hiperparámetros y tiempo de entrenamiento en el archivo excel.
- Notebook
- Presentación breve comparando los resultados de todos los enfoques para este dataset: BOW/TFIDF, W2V/D2V, BERT, LLMs full finetuning & PEFT. Comparar interpretabilidad de resultados, métricas de rendimiento, tiempo de entrenamiento.

---

## PEFT con LoRA (Parameter-Efficient Fine-Tuning)

Aplicar **LoRA** al mismo LLM usado en la Parte 2. Seguir la guía oficial de PEFT.

**Referencia obligatoria**: https://huggingface.co/docs/peft/tutorial/peft_model_config

**Configuración típica de LoRA para clasificación**:

```python
from peft import LoraConfig, get_peft_model, TaskType
from transformers import AutoModelForSequenceClassification

# Cargar modelo base (mismo que en Parte 2)
model = AutoModelForSequenceClassification.from_pretrained(model_id, num_labels=...)

# Configurar LoRA
lora_config = LoraConfig(
    task_type=TaskType.SEQ_CLS,  # Clasificación de secuencias
    r=8,                         # Rank, puedes subirlo para un modelo más complejo y pesado 
    lora_alpha=32,               # Escalamiento
    target_modules=["q_proj", "v_proj"],  # Módulos a adaptar (varía según modelo)
    lora_dropout=0.1
)

# Aplicar LoRA
model = get_peft_model(model, lora_config)
model.print_trainable_parameters()  # Debe mostrar <1% de parámetros entrenables

# A partir de este momento, el finetuning se hace igual a los casos estudiados
### Actividad: Construcción de Corpus de Normativa Universitaria

**Objetivo**: Construir un corpus de textos a partir de documentos normativos de la universidad, segmentados por artículo, que será utilizado posteriormente en un proyecto de construcción de corpus para la predicción de dificultad de lectura.

**Documentos**:
- Ingresar al [sitio de normativa de la universidad](https://www.unison.mx/marco-normativo/) y descargar al menos dos documentos PDF (reglamentos, estatutos, lineamientos). Registrar la URL de cada archivo descargado.

**Instrucciones**:
1. Leer el PDF con la biblioteca `pdfplumber` (recomendada por su precisión en la extracción de texto con formato). Como alternativa puede usarse `PyMuPDF` (`fitz`) o `PyPDF2`.
2. Extraer el texto completo y segmentarlo en artículos. Cada artículo usualmente comienza con la palabra "Artículo" seguida de un número (explorar los archivos para extraer el patrón exacto). Se pueden usar una expresiones regulares para realizar la separación.
3. Conservar al inicio de cada segmento la mención al artículo correspondiente (por ejemplo, "Artículo 5. ..."). No eliminar esa línea.
4. Descartar artículos con menos de 50 palabras, ya que suelen ser artículos de forma, transitorios o remisiones a otros documentos.
5. Construir un archivo CSV con una fila por artículo y las siguientes columnas:

| columna | descripción |
|---|---|
| url | URL del PDF original |
| titulo | Nombre del documento (por ejemplo, "Reglamento de Servicio Social") |
| texto | Texto del artículo, incluyendo la línea "Artículo N. ...", **No quitar stopwords ni normalizar** |

6. Verificar que el CSV no tenga filas con texto vacío. 
7. Entregar un solo archivo CSV por equipo, nombrado `corpus_[nombres_docs].csv`.
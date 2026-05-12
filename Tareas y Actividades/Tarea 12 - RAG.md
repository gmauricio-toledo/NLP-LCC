# RAG

El objetivo de esta practica es realizar un sistema RAG para responder querys a partir solamente de la informacion presente en algunos archivos.

## Instrucciones

Cada equipo partira de una combinacion de distintos componentes y podran mejorar sobre esta.

* Escoger 7 archivos PDF sobre la misma tematica libre, mas 1 documento trampa sobre una tematica completamente diferente.
* Definir 3 querys sobre informacion presente en los textos, manualmente definir las respuestas ground-truth con k=3 (ser lo mas precisos posibles con estos).
* Definir 2 querys con informacion no presente explicitamente en los PDF, una sobre la misma tematica y otra sobre una tematica muy diferente.

## Requisitos para todos los equipos

* Probar al menos 2 modelos de embeddings y reportar comparativa.
* Probar al menos 2 LLMs para la generacion y reportar comparativa.
* Evaluar con recall@k para el retrieval.
* Evaluar con RAGAS para la generacion.
* Incluir evaluacion humana de las respuestas.
* El documento trampa debe estar incluido en la base de conocimiento de todos los equipos.

## Equipos

| Pareja | Foco de exploracion | Chunking | Embeddings | Vector DB | Retrieval / Reranking | Generation |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Equipo 1 | Estrategias de chunking | CharacterTextSplitter, SemanticChunker, RecursiveCharacterTextSplitter (estructural por headers) | all-MiniLM-L6-v2 | ChromaDB | Similitud densa basica | LLM |
| Equipo 2 | Framework LlamaIndex | RecursiveCharacterTextSplitter | all-MiniLM-L6-v2 | VectorStoreIndex (LlamaIndex) | Similaridad densa nativa de LlamaIndex | LLM via LlamaIndex |
| Equipo 3 | Estrategias de retrieval | RecursiveCharacterTextSplitter | BAAI/bge-small-en | FAISS | Solo similitud densa vs BM25 solo vs Ensemble BM25 + similitud | LLM |
| Equipo 4 | Estrategias de reranking | RecursiveCharacterTextSplitter | BAAI/bge-large-en | LanceDB | Sin reranker vs Cross-encoder (HF) vs LLM como reranker | LLM |
| Equipo 5 | Bases de datos vectoriales | RecursiveCharacterTextSplitter | intfloat/e5-large-v2 | ChromaDB vs FAISS vs LanceDB vs Qdrant | Similitud densa | LLM |
| Equipo 6 | Tipos de documentos y preprocesamiento | Dependiente del tipo de documento | all-MiniLM-L6-v2 | ChromaDB | Similitud densa | LLM |

## Descripcion por equipo

Equipo 1 - Estrategias de chunking: Comparar al menos 3 estrategias de chunking distintas. Ejemplos: CharacterTextSplitter con tamano fijo, SemanticChunker que divide por oraciones/parrafos usando criterios semanticos, RecursiveCharacterTextSplitter configurado para respetar la estructura de headers del documento (chunking estructural). Reportar impacto en calidad de retrieval y generacion.

Equipo 2 - Framework LlamaIndex: Replicar un pipeline basico de RAG usando exclusivamente LlamaIndex en lugar de LangChain. Comparar la experiencia de desarrollo, la API, y los resultados contra un equivalente en LangChain. Documentar ventajas y limitaciones encontradas del framework.

Equipo 3 - Estrategias de retrieval: Comparar 3 aproximaciones de retrieval: unicamente similitud densa con embeddings, unicamente BM25 (sparse retrieval), y ensemble que combina ambos con distintos pesos (ej. 0.3/0.7, 0.5/0.5, 0.7/0.3). Reportar recall@k para cada configuracion.

Equipo 4 - Estrategias de reranking: Comparar 3 configuraciones: sin reranker (baseline), reranking con cross-encoder de HuggingFace (ej. BAAI/bge-reranker-base o cross-encoder/ms-marco-MiniLM-L-6-v2), y reranking usando un LLM para reordenar los chunks por relevancia. Reportar impacto en precision del retrieval y calidad de la generacion.

Equipo 5 - Bases de datos vectoriales: Implementar el mismo pipeline de RAG sobre al menos 3 bases de datos vectoriales distintas (ChromaDB, FAISS, LanceDB, Qdrant). Comparar facilidad de uso, velocidad de indexacion, velocidad de query, y capacidad de filtrado por metadata. Milvus esta explicitamente excluida por problemas de estabilidad reportados en semestres anteriores.

Equipo 6 - Tipos de documentos y preprocesamiento: Comparar al menos 3 tipos de documento: PDF nativo/extraible (texto plano), PDF escaneado o imagen que requiere OCR (usar pymupdf4llm, marker, o unstructured), y documento estructurado como Markdown o HTML con jerarquia de headers clara. Reportar como el tipo de documento afecta la calidad del chunking, retrieval, y generacion. El documento trampa debe ser del mismo formato que los demas para no sesgar por preprocesamiento.

## Presentacion

- Mostrar capturas donde muestren la(s) linea(s) especifica(s) donde se realiza cada paso: chunking / embeddings / vector DB / retrieve / re-ranking (si aplica) / generation.
- Mostrar los resultados con evaluacion:
    * Humana para evaluar en general.
    * Recall@k para evaluar el retrieval.
    * RAGAS para evaluar la generacion.
- Hablar sobre las variantes probadas, principales dificultades y retos encontrados, asi como cualquier aspecto relevante que hayan encontrado o entendido durante el desarrollo del proyecto.
- Considerando este sistema como un proof of concept responder a detalle las siguientes preguntas:
    * Como podrian hacer el deployment? Que servicio usarian para el LLM? Como accederian a la Vector DB?
    * Que tan escalable es? Que componente creen que es el principal cuello de botella al escalar?

## Fecha de entrega

Las presentaciones seran el jueves 27 de noviembre (fase 1) y jueves 4 de diciembre (fase 2, por definir).

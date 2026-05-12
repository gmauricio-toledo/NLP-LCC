# RAG

El objetivo de esta practica es realizar un sistema RAG para responder querys a partir **solamente** de la informacion presente en algunos archivos.

## Instrucciones

Cada equipo partira de una combinacion de distintos componentes y podran mejorar sobre esta.

* Escoger 7 archivos (PDF o texto libre) sobre la misma tematica libre, incluyendo 1 documento *trampa* sobre una tematica completamente diferente.
* Definir 3 querys sobre informacion presente en los textos, manualmente definir 3 respuestas ground-truth (ser lo mas precisos posibles con estos).
* Definir 2 querys con informacion no presente explicitamente en los PDF, una sobre la misma tematica y otra sobre una tematica muy diferente.

## Requisitos para todos los equipos

* Probar al menos 2 modelos de embeddings y reportar comparativa.
* Probar al menos 2 LLMs para la generacion y reportar comparativa.
* Evaluar con recall@k para el retrieval.
* Evaluar con RAGAS para la generacion.
* Incluir evaluacion humana de las respuestas. 


## Descripcion por equipo

**Equipo 3 y 5** - Estrategias de chunking: Comparar al menos 3 estrategias de chunking distintas. Ejemplos: CharacterTextSplitter con tamano fijo, SemanticChunker que divide por oraciones/parrafos usando criterios semanticos, RecursiveCharacterTextSplitter configurado para respetar la estructura de headers del documento (chunking estructural). Reportar impacto en calidad de retrieval y generacion.

**Equipo 4 y 9** - Framework LlamaIndex: Replicar un pipeline basico de RAG usando exclusivamente LlamaIndex en lugar de LangChain. Comparar la experiencia de desarrollo, la API, y los resultados contra un equivalente en LangChain. Documentar ventajas y limitaciones encontradas del framework.

**Equipo 6** - Estrategias de retrieval: Comparar 3 aproximaciones de retrieval: unicamente similitud densa con embeddings, unicamente BM25 (sparse retrieval), y ensemble que combina ambos con distintos pesos (ej. 0.3/0.7, 0.5/0.5, 0.7/0.3). Reportar recall@k para cada configuracion.

**Equipo 1 y 2** - Estrategias de reranking: Comparar 3 configuraciones: sin reranker (baseline), reranking con cross-encoder de HuggingFace/sentence-transformers, y reranking usando un LLM para reordenar los chunks por relevancia. Reportar impacto en precision del retrieval y calidad de la generacion.

**Equipo 8** - Bases de datos vectoriales: Implementar el mismo pipeline de RAG sobre al menos 3 bases de datos vectoriales distintas (ChromaDB, FAISS, LanceDB, Qdrant, etc). Comparar facilidad de uso, velocidad de indexacion, velocidad de query, y capacidad de filtrado por metadata. 

**Equipo 7** - Tipos de documentos y preprocesamiento: Comparar al menos 3 tipos de documentos: PDF nativo/extraible, PDF escaneado o imagen que requiere OCR, y documento estructurado como Markdown o HTML con jerarquia de headers clara, documentos con tablas, etc. Reportar como el tipo de documento afecta la calidad del chunking, retrieval, y generacion. El documento trampa debe ser del mismo formato que los demas para no sesgar por preprocesamiento.

Los partes del pipeline de RAG que no están especificadas, elegir componentes.

## Equipos

| **Equipo** |  |  |  |
|--------|--------------|--------------|--------------|
| Equipo 1 | Medina Lugo Fausto Misael | Alan David Torres Flores | |
| Equipo 2 | Denisse Antunez Lopez | Georgina Salcido Valenzuela | Ana Laura Chenoweth Galaz |
| Equipo 3 | Caro Perez Horacio | Joan Antonio Lázaro Silva | Joaquín Alfredo Castro Córdova |
| Equipo 4 | Flor María Machado Felix | Ángel Fernando Bórquez Guerrero | |
| Equipo 5 | Mirka Galilea Dennis Vargas | José Emilio Angulo Bermudez | |
| Equipo 6 | Braulio Alessandro Sanchez Bermudez | Manuel Eduardo Gortarez Blanco | |
| Equipo 7 | Luis Mario Sainz Peñufiuri | Manuel Alejandro Heredia Nogales | |
| Equipo 8 | Francisco Mario González Bórquez | Luis Enrique Jácome Toro | Miguel Cruz Duarte |
| Equipo 9 | Jorge Guerrero | | |

## Presentacion

Abordar cada uno de los siguientes puntos:
- Mostrar capturas donde muestren la(s) linea(s) especifica(s) donde se realiza cada paso: chunking / embeddings / vector DB / retrieve / re-ranking (si aplica) / generation.
- Mostrar los resultados con evaluacion:
    * Humana para evaluar en general.
    * Recall@k para evaluar el retrieval.
    * RAGAS para evaluar la generacion.
- Hablar sobre las variantes probadas, principales dificultades y retos encontrados, asi como cualquier aspecto relevante que hayan encontrado o entendido durante el desarrollo del proyecto.
- Considerando este sistema como un proof of concept responder a detalle las siguientes preguntas:
    * ¿Cómo podrian hacer el deployment? ¿Qué servicio usarian para el LLM? ¿Cómo accederian a la Vector DB?
    * ¿Qué tan escalable es? ¿Qué componente creen que es el principal cuello de botella al escalar?

## Fecha de entrega

Las presentaciones y entrega seran el lunes 18 de mayo (fase 1).

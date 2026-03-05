# Ejercicio: Coherencia de Tópicos con U-Mass

## Contexto

La coherencia U-Mass mide qué tan seguido aparecen juntas las palabras más importantes de un tópico. La idea es simple: si un tópico es bueno, sus palabras deberían co-ocurrir frecuentemente en los documentos.

La fórmula para un par de palabras `(i, j)` es:

```
U-Mass(i, j) = log( (D(i,j) + 1) / D(i) )
```

Donde:
- `D(i)` = número de documentos donde aparece la palabra `i`
- `D(i,j)` = número de documentos donde aparecen **ambas** palabras `i` y `j`
- `+1` evita `log(0)` cuando las palabras nunca co-ocurren

La coherencia de un tópico es la **suma de U-Mass sobre todos los pares** de sus top words.

---

## Corpus

```
D1: "el perro y el gato juegan"
D2: "el perro corre con el gato"
D3: "el gato duerme con el perro"
D4: "la computadora y el teclado son rápidos"
D5: "el teclado y la pantalla de la computadora"
D6: "la pantalla de la computadora es grande"
```

---

## Paso 1: Construir la matriz BOW binarizada

Completa la tabla. Cada celda vale **1** si la palabra aparece en el documento, **0** si no.

| Doc | perro | gato | corre | computadora | teclado | pantalla |
|-----|-------|------|-------|-------------|---------|----------|
| D1  |       |      |       |             |         |          |
| D2  |       |      |       |             |         |          |
| D3  |       |      |       |             |         |          |
| D4  |       |      |       |             |         |          |
| D5  |       |      |       |             |         |          |
| D6  |       |      |       |             |         |          |

---

## Paso 2: Calcular D(i) para cada palabra


| Palabra     | D(i) |
|-------------|------|
| perro       |      |
| gato        |      |
| corre       |      |
| computadora |      |
| teclado     |      |
| pantalla    |      |

---

## Paso 3: Calcular coherencia del Tópico A — Animales

Top words: `perro`, `gato`, `corre`

Para cada par, cuenta en cuántos documentos **ambas palabras aparecen juntas** `D(i,j)` y calcula U-Mass.

**Par (perro, gato):**
- ¿En qué documentos aparecen juntos? ___________
- D(perro, gato) = ___
- D(perro) = ___
- U-Mass = log( (___ + 1) / ___ ) = ___

**Par (perro, corre):**
- ¿En qué documentos aparecen juntos? ___________
- D(perro, corre) = ___
- D(perro) = ___
- U-Mass = log( (___ + 1) / ___ ) = ___

**Par (gato, corre):**
- ¿En qué documentos aparecen juntos? ___________
- D(gato, corre) = ___
- D(gato) = ___
- U-Mass = log( (___ + 1) / ___ ) = ___

**Coherencia Tópico A = suma de los tres pares = ___**

---

## Paso 4: Calcular coherencia del Tópico B — Tecnología

Top words: `computadora`, `teclado`, `pantalla`

**Par (computadora, teclado):**
- D(computadora, teclado) = ___
- D(computadora) = ___
- U-Mass = log( (___ + 1) / ___ ) = ___

**Par (computadora, pantalla):**
- D(computadora, pantalla) = ___
- D(computadora) = ___
- U-Mass = log( (___ + 1) / ___ ) = ___

**Par (teclado, pantalla):**
- D(teclado, pantalla) = ___
- D(teclado) = ___
- U-Mass = log( (___ + 1) / ___ ) = ___

**Coherencia Tópico B = suma de los tres pares = ___**

---

## Paso 5: Calcular coherencia de un tópico mezclado

Ahora imagina que el modelo confundió los tópicos y generó este tópico:

Top words: `perro`, `gato`, `computadora`

**Par (perro, gato):** ya calculado = ___

**Par (perro, computadora):**
- D(perro, computadora) = ___
- D(perro) = ___
- U-Mass = log( (___ + 1) / ___ ) = ___

**Par (gato, computadora):**
- D(gato, computadora) = ___
- D(gato) = ___
- U-Mass = log( (___ + 1) / ___ ) = ___

**Coherencia Tópico mezclado = ___**

---

## Paso 6: Preguntas y conclusiones

1. ¿Qué tópico tiene mayor coherencia, A o B? ¿Por qué?
2. ¿Qué pasó con el tópico mezclado? ¿Cómo se compara con A y B?
3. ¿Qué rol cumple el `+1` en la fórmula? ¿Qué pasaría sin él?
4. ¿Un score más cercano a 0 es mejor o peor? ¿Por qué?

---
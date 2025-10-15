# Api de deteccion de palabras  repetidas

## Definicion

La repetición léxica ocurre cuando una misma palabra o sus variantes morfológicas aparecen varias veces dentro de una oración o párrafo.
Aunque la repetición puede tener valor retórico o estilístico, en la redacción técnica y académica suele considerarse un indicador de pobreza léxica o falta de precisión.
Por ejemplo: “El sistema procesa los datos y procesa las respuestas.”

Repeticiones de este tipo pueden detectarse automáticamente mediante análisis lingüístico.

## Objetivo de la api

El objetivo de ApiWordRepetition consiste en detectar palabras repetidas dentro de una oración o texto en español, considerando aspectos morfológicos y gramaticales.
El servicio permite además ignorar palabras frecuentes o funcionales (como artículos, preposiciones, pronombres y conjunciones) para centrarse en los términos realmente relevantes. De esta forma, ayuda a identificar redundancias y mejorar la variedad léxica y claridad del texto.


## Estrategia

1. **Entrada:**

Un texto en español (String), que puede corresponder a una o varias oraciones.

2. **Procesamiento:**

3. **Análisis lingüístico:**

 Se procesa el texto con spaCy para obtener los lemas (formas base de las palabras) y sus categorías gramaticales.

4. **Normalización:**
 Las palabras se convierten a minúsculas y se reducen a su lema para detectar coincidencias entre formas singulares/plurales o verbos conjugados.
Ejemplo: “niños” y “niño” → niño.

5. **Filtrado opcional:**
Se eliminan palabras vacías o frecuentes (stopwords) como el, de, y, que, etc.

6. **Conteo de repeticiones:**
Se construye un diccionario donde cada clave es una palabra repetida y su valor es la cantidad de apariciones.

7. **Salida estructurada:**
Devuelve un diccionario con las palabras repetidas detectadas y su frecuencia.

## Salida 

  Un diccionario donde:
    1) cada clave representa una palabra repetida, y su valor indica el número de veces que aparece.
    
    2) Si no hay repeticiones, devuelve un diccionario vacío.


## Ejemplos comunes

| Oración                                                   | Resultado esperado                             |
| --------------------------------------------------------- | ---------------------------------------------- |
| “El sistema procesa los datos y procesa las respuestas.”  | `{"procesa": 2}`                               |
| “Los niños juegan con otros niños en el parque.”          | `{"niño": 2}`                                  |
| “El sol brilla sobre el mar y el cielo.”                  | `{}` *(sin repeticiones)*                      |
| “Corre, corre, que te alcanza.”                           | `{"corre": 2}`                                 |
| “El software y el hardware del sistema están integrados.” | `{}` *(“software” y “hardware” no se repiten)* |


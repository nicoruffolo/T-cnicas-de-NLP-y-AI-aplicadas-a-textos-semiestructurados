# Api de deteccion de puntuaciones  inusuales 

## Definicion

La puntuación es un conjunto de signos gráficos que estructuran un texto escrito, indican pausas, entonación y delimitan unidades de sentido.
El uso incorrecto de la puntuación como la falta de signos de apertura, repeticiones excesivas o errores de espaciado puede alterar significativamente la claridad, coherencia y legibilidad de una oración.

El servicio ApiUnusualPunctuation analiza textos en español para detectar patrones anómalos o inconsistentes en la puntuación y el uso de mayúsculas/minúsculas, con el fin de identificar errores formales que afectan la calidad del texto.

## Objetivo de la api

El objetivo de ApiUnusualPunctuation es detectar errores o usos inusuales de la puntuación y capitalización en oraciones escritas en español.
A través de un análisis automático, el servicio identifica casos como:

1) Falta o exceso de signos de apertura/cierre (¡!, ¿?, (), [], {}).

2) Repetición innecesaria de signos de puntuación (por ejemplo, “??”, “!!!”).

3) Uso incorrecto de mayúsculas o minúsculas después de los signos.

4) Espaciado inadecuado antes o después de los signos de puntuación.

5) El servicio no altera el texto original, sino que devuelve una lista estructurada con los errores detectados, su posición y descripción.

## Estrategia

1. **Entrada:** 

Una oración o texto corto en español como cadena de texto (String).

2. **Procesamiento:**

**Análisis de estructura:**
Se recorren los caracteres del texto y se evalúa la secuencia de signos de puntuación y letras mayúsculas/minúsculas.

**Verificación de apertura/cierre:**
Se comprueba que los signos como paréntesis, llaves o signos de interrogación/exclamación estén correctamente balanceados.

**Detección de repeticiones o exceso de signos:**
Se buscan patrones como !!, ???, ,,, ...!, que indican uso excesivo.

**Control de capitalización:**
Se valida si después de un punto o signo de cierre la siguiente palabra comienza correctamente con mayúscula.

**Revisión de espaciado:**
Se detectan espacios duplicados, ausencia de espacio después de signos o espacio antes de ellos.

**Registro estructurado:**
Cada error identificado se almacena como un diccionario con:

  1) posición: tupla (inicio, fin) indicando el rango del error,

  2) texto: fragmento afectado,

  3) descripción: tipo de error detectado.

3. **Salida**
 Una lista de diccionarios con la información de cada error de puntuación inusual. Si no se detectan errores, se devuelve una lista vacía.

## Ejemplos comunes

 | Oración                            | Error detectado   | Descripción                                  |
| ---------------------------------- | ----------------- | -------------------------------------------- |
| “¡Qué lindo día!!”                 | `!!`              | Repetición excesiva de signos de exclamación |
| “Cómo estas?”                     | `estas`           | Falta signo de apertura “¿”                  |
| “(Hola, qué tal?”                  | `(Hola, qué tal?` | Paréntesis sin cierre                        |
| “El  texto tiene  doble  espacio.” | ` " " `              | Espaciado inadecuado                         |
| “terminó la frase. ahora sigue.”   | `ahora`           | Falta mayúscula tras punto                   |


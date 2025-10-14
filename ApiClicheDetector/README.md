# Api de deteccion de cliches
## Definicion
Un cliché en requerimientos es una expresión vaga o genérica que parece describir un requisito, pero que en realidad no comunica nada concreto ni permite validación objetiva.
Estos clichés suelen dar una falsa sensación de claridad o calidad, pero son peligrosos porque introducen ambigüedad, interpretaciones múltiples y conflictos durante el desarrollo del sistema.

## Ejemplos comunes

| Cliché | Problema | Ejemplo mejorado |
|--------|-----------|------------------|
| “El sistema debe ser **fácil de usar**.” | “Fácil” es subjetivo. | “El usuario podrá completar una transacción en menos de 3 pasos.” |
| “La aplicación será **rápida**.” | “Rápida” no se puede medir. | “El tiempo de respuesta no debe superar los 2 segundos en el 95% de las consultas.” |
| “El software debe ser **seguro**.” | No indica qué tipo de seguridad. | “El sistema requerirá autenticación de dos factores para todos los usuarios administradores.” |
| “El sistema debe ser **flexible**.” | Ambigua: no especifica en qué aspecto. | “El sistema permitirá configurar nuevos tipos de usuario sin modificar el código fuente.” |
| “El producto tendrá una **interfaz amigable**.” | “Amigable” es subjetivo. | “La interfaz cumplirá con las pautas WCAG 2.1 nivel AA de accesibilidad.” |
| “El sistema debe ser **eficiente**.” | No es cuantificable. | “El uso promedio de CPU no superará el 60% con 100 usuarios concurrentes.” |

## Objetivo de la api

El objetivo de ApiClicheDetector consiste en analizar una oración en español para detectar la presencia de clichés, es decir, expresiones comunes o predecibles que se repiten con frecuencia en el lenguaje. Durante el análisis, el texto recibido se compara con una lista predefinida de clichés pertenecientes al dominio de interés. Se calcula un porcentaje de similitud semántica entre la oración y los clichés conocidos; aquellos que superan un umbral mínimo son agregados a una lista de coincidencias. En caso correcto devuelve los fragmentos encontrados y si no se detectan clichés, retorna el mensaje, No se detectaron clichés.

## Estrategia

1. **Entrada:**  
   El usuario envía un texto (por ejemplo, un requerimiento funcional o no funcional).

2. **Preprocesamiento lingüístico (lemmatización):**  
   - Se usa **spaCy** (`es_core_news_sm`) para convertir las palabras a su forma base o *lema*.  
   - Esto permite comparar frases equivalentes aunque estén escritas de manera diferente.  
     - Ejemplo: “quiero poder usar” ≈ “queremos poder utilizar”.

3. **Comparación con lista de clichés conocidos:**  
   - Se define una lista de expresiones vagas, típicas o subjetivas (por ejemplo, *“que sea fácil de usar”*, *“que funcione bien”*, *“para mejorar la productividad”*).  
   - Cada cliché se lematiza igual que el texto de entrada.

4. **Cálculo de similitud difusa:**  
   - Se usa la función `fuzz.token_set_ratio()` de **RapidFuzz** para comparar los lemas del texto con los lemas de cada cliché.  
   - Esta métrica devuelve un valor entre **0 y 100**, donde 100 significa coincidencia perfecta.  
   - Si la similitud supera un **umbral (por defecto 70)**, el cliché se considera **detectado**.

5. **Salida:**  
   - Devuelve una lista de clichés detectados en formato JSON.

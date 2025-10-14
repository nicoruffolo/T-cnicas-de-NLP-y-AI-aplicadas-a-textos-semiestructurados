# Tecnicas-de-NLP-y-AI-aplicadas-a-textos-semiestructurados

"El servicio de apiTenses consite en implementar un detector automático de tiempos verbales en español utilizando el modelo lingüístico de spaCy. Su objetivo es identificar y clasificar los tiempos verbales presentes en un texto, tanto simples como compuestos, devolviendo una lista estructurada con los verbos encontrados y su respectiva categoría temporal.

El funcionamiento consiste en: 
    1) Recibe una cadena de texto como entrada.
    2) Procesa el texto con spaCy para analizar su estructura morfosintáctica.
    3) Detecta y etiqueta los verbos según su tiempo verbal, diferenciando entre:
         . Tiempos simples: presente, pasado, futuro.
         . Tiempos compuestos: pretérito perfecto compuesto, pluscuamperfecto, futuro compuesto.
    4) Elimina duplicados, evitando contar participios o auxiliares sueltos como tiempos simples.
    5) Devuelve una lista de tuplas con cada verbo y su tiempo verbal identificado.    "

# Tecnicas-de-NLP-y-AI-aplicadas-a-textos-semiestructurados

"El servicio de ApiReadabilityMetric consiste en calcular el indice legibilidad por medio de la formula de Fernández Huerta, consiste en
una metrica cuantitativa que estima el grado de facilidad o dificultad para comprender un texto en español.
El índice se basa en el promedio de sílabas por cada 100 palabras y el promedio de palabras por oración, produciendo un puntaje de legibilidad que luego se clasifica en niveles cualitativos.
 El funcionamiento consiste en: 
   1) Recibe el texto a analizar.

   2) Calcula el número total de palabras.

   3) Calcula el número total de sílabas, utilizando la librería pyphen para una segmentación precisa.

   4) Determina la cantidad de oraciones contando signos de puntuación finales (., !, ?).
   
   5) Sílabas por cada 100 palabras. Promedio de palabras por oración. 
     
    El resultado final devuelve un puntaje que determina la escala de nivel de dificultad: ≥ 90 muy facil; 80 – 89 facil;
    70 – 79 Algo fácil; 60 – 69 normal;  50 – 59 algo dificil;  30 – 49 dificil; ≤ 29 muy dificil.

    Devuelve como valor de salida resultante un puntaje que determina el valor numerico del indice. Ademas devuelve un valor
    en string que determina la clasificación cualitativa del texto según el puntaje obtenido.
   "

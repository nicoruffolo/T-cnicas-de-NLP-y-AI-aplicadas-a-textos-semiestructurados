# Api de legibilidad

## Definicion
La **métrica de Fernández Huerta** es una fórmula diseñada para **medir la facilidad de lectura de textos en español**, adaptada de la conocida escala de Flesch Reading Ease usada en inglés.  
Su propósito es cuantificar **qué tan comprensible** resulta un texto, especialmente en contextos educativos, académicos o técnicos.

### 🧮 Fórmula

\[
\text{Índice de Fernández Huerta} = 206.84 - (0.60 \times P) - (1.02 \times F)
\]

Donde:

- **P** = Promedio de sílabas por cada 100 palabras.  
- **F** = Promedio de oraciones por cada 100 palabras.

### 📖 Interpretación del resultado

El resultado es un número que indica el **grado de facilidad de lectura** del texto.  
Cuanto **mayor sea el índice**, **más fácil** es de leer.

| **Rango del índice** | **Nivel de legibilidad** | **Descripción** |
|-----------------------|--------------------------|-----------------|
| 90 – 100 | Muy fácil | Lenguaje infantil o muy básico. |
| 80 – 89 | Fácil | Apto para lectores jóvenes. |
| 70 – 79 | Algo fácil | Nivel de lectura medio. |
| 60 – 69 | Normal | Comprensible para la mayoría de adultos. |
| 50 – 59 | Algo difícil | Requiere concentración. |
| 30 – 49 | Difícil | Propio de textos técnicos o académicos. |
| 0 – 29 | Muy difícil | Lenguaje especializado o denso. |

## Objetivo de la api
El servicio de ApiReadabilityMetric consiste en calcular el indice legibilidad por medio de la formula de Fernández Huerta, consiste en
una metrica cuantitativa que estima el grado de facilidad o dificultad para comprender un texto en español.
El índice se basa en el promedio de sílabas por cada 100 palabras y el promedio de palabras por oración, produciendo un puntaje de legibilidad que luego se clasifica en niveles cualitativos.

## Estrategia

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
   

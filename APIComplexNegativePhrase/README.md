# Api de deteccion de Frases negativas complejas
## Definicion
Una *Complex Negative Phrase* (“frase negativa compleja”) es una oración en la que no basta con tener una sola negación, sino que esa negación se ve reforzada o propagada por la estructura sintáctica de la oración. En otras palabras:

1. Contiene **negación explícita** — por ejemplo: “no”, “nada”, “nadie”, “nunca”, “ninguno”, etc.  
2. Tiene una **estructura compleja** — puede incluir cláusulas subordinadas, modificadores, dependientes (objetos, adverbios, oraciones relativas, etc.).  
3. La negación **“viaja” o se hereda** a través de la estructura: los componentes dependientes de verbos o adjetivos también pueden contener o propagar negaciones (“refuerzos negativos”), de modo que la carga negativa se acumula en el análisis sintáctico.

## Ejemplos

### Frases que **sí** podrían considerarse *Complex Negative Phrases*

- “No creo que nadie haga nada para evitarlo.”  
  → “no” + “nadie” + “nada” y hay cláusula subordinada, propagación.  
- “No es imposible que no veas lo que ha sucedido.”  
  → “no” + “imposible” + “no” — varios niveles de negación en jerarquía de cláusulas.  
- “No hubo ninguno que no lo advirtiera primero.”  
  → “no” + “ninguno” + “no” en cláusula relativa.  
- “Nunca me ha dicho que no estaría dispuesto.”  
  → “nunca” + “no” en la subordinada.
  
### Frases que **no** serían *Complex Negative Phrases*

- “No quiero ir al cine.”  
  → Solo una negación directa; no estructura compleja.  
- “Nadie vino.”  
  → Sólo “nadie”, sin otras capas sintácticas de herencia de negación.  
- “Nunca estudia.”  
  → Sólo “nunca”, sin cláusulas subordinadas ni dependientes con más negaciones.

## Objetivo de la api
El objetivo de APIComplexNegativePhrase es detectar frases con negaciones dobles que se cancelan entre sí. Para lograrlo, analiza la estructura sintáctica de la oración y las relaciones de dependencia entre palabras, especialmente verbos y adjetivos. De esta forma puede diferenciar si la negación se anula, se refuerza, o si es una negación simple o inexistente. El resultado es True cuando se trata de una negación compleja y False en los demás casos.


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

## Estrategia empleada
1. Detección morfológica con Spacy:
	Buscar los tokens que tengan el atributo pos_ con el valor de verbo o adjetivo.
2. Detección token negativo con diccionario de palabras negativas:
	Verificamos que el token obtenido en el paso 1 sea un token negativo para aumentar el contador de negativas,  en cualquier caso ya sea que el token sea o no un adjetivo negativo se continúa al paso 3.
3. Detección de dependencia sintáctica del token:
  Verificamos si los tokens obtenidos en el paso 1 poseen hijos con el atributo dep_ con alguno de los siguientes valores: "ccomp", "acl","csubj","advmod","nsubj",”mark”,”obj”.
  Según estos valores tengo 2 opciones, si tenemos “advmod” vamos al paso 4 pero si son  "ccomp", "acl","csubj","nsubj" vamos al paso 2 con el token hijo y repetimos hasta obtener la doble negación o que no haya más hijos y por lo tanto la frase no posee una doble negación.
  También tenemos un caso especial en el que si entre los hijos tenemos uno con pos “sconj” (conjunción subordinada) entonces podemos tener un refuerzo de negación en lugar de cancelación y de la misma forma ocurre con una dependencia “det” con carga negativa.
4. Comparación con diccionario de palabras negativas:
  Se verifica si el token cuya dep_ es “advmod” existe en la lista de palabras negativas y si ya con este es la segunda negativa que se encuentra sabemos que la frase posee una doble negación pero si no se ha conseguido aún se continúa desde el siguiente hijo del padre en el paso 3.




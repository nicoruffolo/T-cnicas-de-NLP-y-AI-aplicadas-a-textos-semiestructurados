# Tecnicas-de-NLP-y-AI-aplicadas-a-textos-semiestructurados

# 🧩 Procesamiento de Textos Semiestructurados

## 📘 Descripción general
Este repositorio reúne y documenta los **servicios de análisis lingüístico** desarrollados para el **procesamiento automático de textos semiestructurados en español**.  
Cada servicio (API) aborda un aspecto específico del lenguaje natural, permitiendo detectar patrones gramaticales, semánticos o de estilo dentro de oraciones o párrafos.

Los módulos fueron diseñados para integrarse en flujos de análisis de texto, procesamiento de lenguaje natural (NLP) y detección de estructuras.

---

## ⚙️ Estructura del repositorio
Cada carpeta o archivo del repositorio corresponde a un **servicio independiente**, acompañado de su respectiva descripción funcional, parámetros de entrada, salida y criterios de análisis.

| Servicio | Descripción breve |
|-----------|------------------|
| **ApiComplexNegativePhrase** | Detecta oraciones con **negaciones dobles** que se cancelan mutuamente. |
| **ApiAbstractWords** | Identifica **términos abstractos** entre sustantivos, adjetivos y verbos. |
| **ApiPassiveVoice** | Determina si una oración está escrita en **voz pasiva**. |
| **ApiWordRepetition** | Analiza la **repetición de palabras**, considerando equivalencias y omitiendo palabras frecuentes. |
| **ApiUnusualPunctuation** | Detecta **errores o usos inusuales de puntuación y mayúsculas**. |
| **ApiImpersonalSentences** | Identifica si una oración es **impersonal**, es decir, sin sujeto agente explícito. |
| **ApiClicheDetector** | Detecta **clichés** o expresiones comunes mediante análisis de similitud semántica. |
| **ApiLogicalConnectors** | Encuentra **conectores lógicos** en el texto (simples o compuestos) usando *spaCy* y *PhraseMatcher*. |

---

## 🧠 Objetivo general
El objetivo principal de este conjunto de servicios es **automatizar la detección y clasificación de estructuras lingüísticas complejas** dentro de textos en español, facilitando el análisis de estilo, coherencia y semántica.  

Estos módulos pueden ser utilizados de manera **independiente** o **combinada**, según la necesidad del análisis textual.

---

## 🧩 Tecnologías utilizadas
- **Python**
- **spaCy** para análisis sintáctico y semántico.
- **PhraseMatcher** para detección de patrones léxicos.
- **Modelos de embeddings** para similitud semántica (en algunos servicios).
- **Reglas morfológicas y patrones lingüísticos personalizados**.

---

## 📦 Salida esperada
Cada servicio retorna un resultado estructurado, generalmente en formato:
- `boolean`: cuando se trata de detección binaria (presencia/ausencia de un fenómeno lingüístico).  
- `listas` o `diccionarios`: cuando se devuelven múltiples elementos o coincidencias detectadas en el texto.

---

## 📚 Uso y documentación
Dentro de cada subcarpeta o archivo encontrarás:
- La **descripción funcional** del servicio.  
- Los **parámetros de entrada y salida**.  
- Resultados esperados.

Cada API está documentada de forma individual, lo que permite comprender y reutilizar fácilmente su funcionamiento en distintos contextos.


---

## 🧾 Licencia
Este repositorio se distribuye con fines académicos y de investigación.  
Podés reutilizar y adaptar los módulos con la fuente original del proyecto.

---


# Zero_Entreno_2025: Inferencia Avanzada de Tono y Tema en Noticias

Este proyecto de vanguardia se enfoca en la **clasificación automática de texto** para el **análisis de tono (sentimiento)** y la **categorización temática** de resúmenes de noticias. Ofrece una solución dual y flexible, capaz de operar tanto con un **enfoque "Zero-Shot" (sin entrenamiento explícito)** para una implementación ágil, como con un **enfoque basado en entrenamiento supervisado** utilizando datos manualmente codificados para alcanzar la máxima precisión en dominios específicos.

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1x12TMUWPBT9lgqRBlZJcZssCOSNCopQ9#scrollTo=8T0NTLANOshM)

---

## ✨ Ventajas Clave del Proceso

La implementación de este sistema de clasificación automática genera beneficios sustanciales para cualquier organización que gestione volúmenes significativos de información textual:

### 🚀 1. **Flexibilidad Estratégica: Zero-Shot y Entrenamiento Supervisado**
El proyecto capitaliza lo mejor de ambos paradigmas en el PLN:
* **Análisis "Zero-Shot":** Permite la clasificación de contenido de forma inmediata, sin la necesidad de un conjunto de datos de entrenamiento específico para cada nueva categoría. Esto es ideal para la exploración rápida de temas emergentes o la categorización en dominios desconocidos.
* **Precisión con Entrenamiento Supervisado:** Para escenarios que demandan una alta fidelidad y donde existen datos históricos etiquetados manualmente, el proyecto soporta la integración de modelos entrenados. Esto afina la capacidad del sistema para comprender las particularidades léxicas y semánticas de tu negocio o sector.

### 🎯 2. **Precisión y Consistencia Unificadas**
Independientemente del enfoque elegido, el sistema garantiza una **consistencia y precisión uniformes** en la clasificación. Supera la variabilidad y los posibles sesgos introducidos por la clasificación manual, asegurando un análisis de datos objetivo y replicable a gran escala.

### 📈 3. **Eficiencia Operativa y Escalabilidad Masiva**
Automatiza la ingente tarea de analizar miles de documentos en cuestión de minutos. Esta capacidad libera a los equipos de la clasificación manual repetitiva, permitiéndoles reorientar sus esfuerzos hacia análisis estratégicos y tareas de mayor valor añadido. El diseño del sistema está optimizado para el **aprovechamiento de Unidades de Procesamiento Gráfico (GPUs)**, lo que acelera significativamente el rendimiento computacional.

### 💰 4. **Optimización de Recursos y Reducción de Costos**
La automatización del análisis de tono y tema conlleva una **minimización sustancial de los costos operativos** asociados a la mano de obra. La inversión en esta solución se traduce en ahorros significativos a largo plazo y una asignación más eficiente de los recursos organizacionales.

### 💡 5. **Extracción de Insights Estratégicos**
Más allá de la mera clasificación, este proceso facilita la **detección de patrones, tendencias y opiniones ocultas** dentro de tus datos textuales. Permite:
* Identificar los temas de mayor impacto e interés para tu audiencia o stakeholders.
* Comprender el sentimiento predominante hacia tu marca, productos, servicios o eventos clave.
* Detectar proactivamente problemas incipientes, identificar oportunidades de mejora o validar estrategias basadas en el feedback no estructurado.

---

## 📚 Metodologías y Componentes Técnicos

Este proyecto integra dos metodologías principales para la clasificación de texto:

### 1. **Análisis "Zero-Shot" (Inferencia sin Entrenamiento Específico)**

Este enfoque se basa en el poder de los **modelos pre-entrenados de PLN** que ya han aprendido vastos patrones lingüísticos.
* **Concepto:** Se utilizan **embeddings semánticos** para representar tanto los textos de entrada como las categorías de interés (sentimientos o temas). La clasificación se realiza calculando la **similitud cosenoidal** entre el embedding del texto y los embeddings "prototipo" de cada categoría.
* **Tono (Sentimiento):**
    * **Modelo:** Se emplea `pysentimiento/robertuito-sentiment-analysis`, un modelo **Sentence-BERT** altamente robusto y público, específicamente fine-tuneado para el análisis de sentimiento en español.
    * **Funcionamiento:**
        * Los textos se preprocesan (normalización, limpieza de URLs y caracteres especiales).
        * Se definen palabras clave prototipo (`sentiment_keywords`) para "Positivo", "Neutro" y "Negativo".
        * Los textos se codifican en embeddings.
        * Se calcula la similitud cosenoidal con los embeddings de las categorías de sentimiento.
        * Se aplica una **heurística de coincidencia exacta de palabras clave** para asignaciones de alta confianza, seguida de la clasificación por similitud cosenoidal con umbrales de confianza y diferencia de puntuación.
* **Tema:**
    * **Modelo:** Se utiliza `paraphrase-multilingual-mpnet-base-v2`, otro modelo **Sentence-BERT multilingüe** público y de alto rendimiento, ideal para la comprensión semántica entre textos en español.
    * **Funcionamiento:**
        * Similar al tono, los textos se preprocesan.
        * Se definen **palabras clave para cada tema** (`predefined_keywords`).
        * Los textos y las listas de palabras clave se transforman en embeddings.
        * La clasificación se basa en la **similitud cosenoidal**, complementada con una **verificación de coincidencia exacta de palabras clave** para mayor precisión.

### 2. **Análisis con Entrenamiento Supervisado**

Este enfoque requiere un conjunto de datos previamente etiquetado para **entrenar un clasificador** que aprenda los patrones específicos de tus datos.
* **Tono (Sentimiento):**
    * **Modelo:** Se construye un pipeline con **`CountVectorizer`** para la representación de texto (conteo de palabras) y **`LogisticRegression`** como clasificador.
    * **Funcionamiento:**
        * Se carga un archivo de entrenamiento (`.xlsx`) con resúmenes y sus etiquetas de tono (`Positivo`, `Neutro`, `Negativo`), las cuales se mapean a valores numéricos.
        * El dataset se divide en conjuntos de entrenamiento y prueba.
        * El modelo aprende las relaciones entre las palabras y el tono a partir de los datos de entrenamiento.
        * Una vez entrenado, puede predecir el tono de nuevos resúmenes de noticias.
* **Tema:**
    * **Modelo:** Se utiliza una combinación de **`CountVectorizer`** para la vectorización de texto y **`MultinomialNB` (Naive Bayes Multinomial)** para la clasificación.
    * **Funcionamiento:**
        * Se carga un archivo de entrenamiento (`.xlsx`) que contiene resúmenes y sus etiquetas de tema.
        * Los textos son preprocesados (normalización, tokenización, eliminación de stopwords en español) usando NLTK y expresiones regulares.
        * El modelo se entrena para asociar patrones de palabras con temas específicos.
        * Los modelos entrenados (`modelo_naive_bayes.pkl`) y los vectorizadores (`vectorizador.pkl`) se serializan usando **`joblib`** para su posterior uso en inferencia sobre nuevos datos.

---

## 💻 Librerías Clave Utilizadas

Este proyecto se apoya en una serie de librerías de Python para su funcionamiento:

* **`pandas`**: Para la manipulación y gestión eficiente de datos tabulares (archivos `.xlsx`).
* **`openpyxl`**: Motor para leer y escribir archivos `.xlsx`.
* **`sentence-transformers`**: Fundamental para el análisis "Zero-Shot", permite cargar y usar modelos pre-entrenados para generar embeddings de texto.
* **`torch`**: (PyTorch) La librería de deep learning subyacente utilizada por `sentence-transformers` para operaciones en GPU/CPU.
* **`tqdm`**: Para mostrar barras de progreso, lo que mejora la experiencia de usuario durante procesos largos.
* **`emoji`**: Para el manejo de emojis en el preprocesamiento de texto (aunque en noticias su impacto es menor).
* **`re`**: Módulo de expresiones regulares para tareas de limpieza y preprocesamiento de texto.
* **`unicodedata`**: Para la normalización de caracteres en el preprocesamiento de texto.
* **`scikit-learn`**: Colección robusta de herramientas para aprendizaje automático, utilizada en el enfoque supervisado para `CountVectorizer`, `LogisticRegression`, `MultinomialNB`, y métricas de evaluación.
* **`nltk`**: (Natural Language Toolkit) Para el procesamiento de lenguaje natural, específicamente para el manejo de "stopwords" (palabras comunes sin significado temático) en el enfoque supervisado de tema.
* **`joblib`**: Para la serialización y deserialización de modelos entrenados y vectorizadores, permitiendo guardarlos y cargarlos eficientemente.

---

## 🛠️ Estructura del Proyecto

* `notebooks/`: Contiene los notebooks de Google Colab (`.ipynb`) con la lógica de inferencia para ambos enfoques, así como los experimentos y análisis originales.
* `data/`: Directorio centralizado para almacenar:
    * Archivos de entrada (`.xlsx`) con las noticias a analizar.
    * Archivos de entrenamiento (`.xlsx`) con noticias previamente codificadas (para el enfoque supervisado).
    * Resultados de las clasificaciones (`.xlsx`).
* `models/`: Directorio dedicado a guardar los modelos entrenados (`.pkl`) y vectorizadores serializados, cuando se utiliza el enfoque supervisado.
* `scripts/`: Scripts Python auxiliares para tareas de procesamiento o predicción que puedan ser ejecutadas fuera de los notebooks.
* `requirements.txt`: Lista de todas las dependencias del proyecto, útil para replicar el entorno localmente.
* `README.md`: Esta documentación principal.

---

## 🚀 Cómo Empezar

Para poner en marcha este proyecto en tu entorno Google Colab:

1.  **Clona el repositorio:**
    ```bash
    git clone https://github.com/tu_usuario/Zero_Entreno_2025.git
    cd Zero_Entreno_2025
    ```

2.  **Instala las dependencias:**
    * Aunque los notebooks incluyen comandos para la instalación silenciosa (`!pip install -qq ...`), si deseas un entorno local, puedes instalar todas las dependencias desde el archivo `requirements.txt`:
        ```bash
        pip install -r requirements.txt
        ```

3.  **Prepara tus datos:**
    * Para cualquier análisis, tus archivos de entrada (`.xlsx`) deben contener una columna nombrada `resumen` con el texto a procesar.
    * Si utilizas el modo con entrenamiento, los notebooks te indicarán cómo subir los archivos `.xlsx` de entrenamiento (noticias previamente analizadas) y los archivos `.xlsx` de prueba (nuevas noticias a analizar).

4.  **Ejecuta el análisis:**
    * Abre los notebooks relevantes en la carpeta `notebooks/` en Google Colab.
    * Sigue las instrucciones específicas dentro de cada notebook para ejecutar el análisis de tono o tema, y para seleccionar el enfoque (Zero-Shot o con entrenamiento) deseado.
    * Para el modo Zero-Shot, puedes personalizar las listas de "temas a inferir" o "palabras clave de sentimiento" directamente en el código del notebook.

---

## 🤝 Contribución

¡Tu contribución es muy valorada! Si tienes ideas para mejorar el proyecto, encuentras algún error o deseas añadir nuevas funcionalidades, por favor:

1.  Abre un `issue` para discutir tu propuesta.
2.  Envía un `pull request` con tus cambios.

---

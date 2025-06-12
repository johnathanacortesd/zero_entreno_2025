# Zero_Entreno_2025: Inferencia de Tono y Tema en Noticias

Este proyecto unifica la **clasificación automática de texto** para **analizar el tono (sentimiento)** y **categorizar el tema** en resúmenes de noticias. Ofrece una solución dual y flexible: puede operar en un **modo "Zero-Shot"** para un análisis rápido sin necesidad de entrenamiento previo, o aprovechar **datos manualmente codificados** para un entrenamiento supervisado que refina la precisión en dominios específicos.

---

## ✨ Ventajas Clave del Proceso

La implementación de este sistema de clasificación automática ofrece beneficios significativos para cualquier organización que maneje grandes volúmenes de información textual:

### 🚀 1. **Flexibilidad: Zero-Shot y Entrenamiento Supervisado**
El proyecto ofrece lo mejor de ambos mundos:
* **Análisis "Zero-Shot":** Clasifica contenido instantáneamente sin un entrenamiento previo, ideal para explorar temas emergentes o dominios desconocidos.
* **Precisión con Entrenamiento:** Utiliza datos previamente codificados para entrenar modelos, logrando una mayor precisión y adaptabilidad a las especificidades de tu negocio o sector.

### 🎯 2. **Precisión y Consistencia Mejoradas**
Ya sea a través de modelos predefinidos o entrenados con tus datos, el sistema garantiza una **consistencia y precisión uniformes** en la clasificación. Elimina la variabilidad y los sesgos inherentes a la clasificación manual, asegurando un análisis fiable y replicable.

### 📈 3. **Eficiencia y Escalabilidad Masiva**
Automatiza la tarea de analizar miles de documentos en cuestión de minutos. Esto libera a tu equipo de la clasificación manual repetitiva, permitiéndoles enfocarse en análisis estratégicos y tareas de mayor valor. La optimización para **uso de GPUs** acelera aún más este proceso.

### 💰 4. **Optimización de Recursos y Reducción de Costos**
Al automatizar el análisis de tono y tema, se **minimizan los costos operativos** asociados a la mano de obra. La inversión en esta solución se traduce en ahorros significativos a largo plazo y una asignación más eficiente de tus recursos.

### 💡 5. **Extracción de Insights Valiosos**
Más allá de la clasificación, este proceso facilita la **detección de patrones, tendencias y opiniones** en tus datos textuales. Permite:
* Identificar temas de impacto e interés para tu audiencia.
* Comprender el sentimiento predominante hacia tu marca, productos o eventos.
* Detectar proactivamente problemas, oportunidades o áreas de mejora basadas en el feedback no estructurado.

---

## 📚 Documentación y Flujo de Trabajo

Para una comprensión detallada de los pasos realizados, las librerías utilizadas y el flujo de trabajo para cada enfoque, consulta los siguientes documentos:

* **`Documentación modelo ZerOEntreno.docx`**: Explica el proceso cuando se utilizan **archivos de entrenamiento** (noticias previamente analizadas) para el análisis de tono y tema.
* **`Documentación modelo ZerOEntreno 2.docx`**: Detalla el proceso **"Zero-Shot"** (sin entrenamiento específico) para el análisis de tono y tema.

---

## 🛠️ Estructura del Proyecto

* `notebooks/`: Contiene los notebooks de Google Colab con la lógica de inferencia, así como los experimentos y análisis originales.
* `data/`: Directorio donde se almacenan los datos de entrenamiento, prueba y los resultados de las clasificaciones.
* `models/`: Directorio para guardar los modelos entrenados (si se utiliza el enfoque supervisado).
* `scripts/`: Scripts Python auxiliares para el procesamiento y la predicción.
* `requirements.txt`: Lista de todas las dependencias del proyecto.
* `README.md`: Esta documentación principal.

---

## 🚀 Cómo Empezar

1.  **Clona el repositorio:**
    ```bash
    git clone https://github.com/tu_usuario/Zero_Entreno_2025.git
    cd Zero_Entreno_2025
    ```

2.  **Instala las dependencias:**
    ```bash
    pip install -r requirements.txt
    ```
    *(Nota: En Google Colab, las instalaciones de librerías se realizan silenciosamente dentro de los notebooks.)*

3.  **Prepara tus datos:**
    * Para cualquier análisis, asegúrate de que tus archivos `.xlsx` de entrada contengan una columna llamada `resumen` con el texto a analizar.
    * Si usas el modo con entrenamiento, los nombres de los archivos `.xlsx` de entrenamiento y prueba (noticias previamente analizadas y nuevas noticias a analizar) deben ser ajustados en el notebook correspondiente.

4.  **Ejecuta el análisis:**
    * Abre los notebooks en `notebooks/` en Google Colab y sigue las instrucciones específicas para el enfoque (Zero-Shot o con entrenamiento) que desees utilizar.
    * Para el modo Zero-Shot, puedes cambiar los "temas a inferir" directamente en el código del notebook según tus necesidades.

---

## 🤝 Contribuir

Si deseas contribuir a este proyecto, por favor no dudes en abrir un `issue` para discutir nuevas ideas o enviar un `pull request` con tus mejoras. ¡Toda contribución es bienvenida!

---

# Inferencia de Tono y Tema en Noticias

Este proyecto tiene como objetivo automatizar el análisis de tono (sentimiento) y tema en resúmenes de noticias, utilizando archivos de entrenamiento que se obtuvieron de un proceso manual de codificación.

En el archivo de word Documentación modelo ZerOEntreno se encuentran explicados los pasos realizados, librerías utilizadas y el flujo de trabajo.

Para su ejecución en Google Colab se deja un txt con el nombre colab (Tener en cuenta que se deben cambiar los nombres de los xlsx de entreno (noticias previamente analizadas) y test (nuevas noticias a analizar).

## Estructura del Proyecto
- `notebooks/`: Contiene los notebooks originales con los experimentos y análisis.
- `data/`: Directorio donde se almacenan los datos de entrenamiento y prueba.
- `models/`: Directorio donde se guardan los modelos entrenados.
- `scripts/`: Scripts Python para el procesamiento y predicción.
- `requirements.txt`: Dependencias del proyecto.
- `README.md`: Esta documentación.

## Cómo Empezar

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu_usuario/repo-inferencia-tono-tema.git
   ```

2. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

3. Ejecuta los notebooks o scripts para entrenar los modelos o inferir tono y tema.

## Contribuir
Si deseas contribuir, por favor abre un issue o realiza un pull request.

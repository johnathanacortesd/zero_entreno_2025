# Inferencia de Tono y Tema en Noticias sin Entrenamiento

Este proyecto tiene como objetivo analizar el tono (sentimiento) y el tema de noticias a partir de resúmenes de textos, sin la necesidad de un entrenamiento previo, utilizando modelos predefinidos.

En el código importante cambiar la parte de temas_relacionados por los temas a inferir y siempre subir el xlsx con las noticias a analizar con la palabra resumen como título de la columna.

En el archivo de word Documentación modelo ZerOEntreno 2 se encuentran explicados los pasos realizados, librerías utilizadas y el flujo de trabajo.



## Estructura del Proyecto
- `notebooks/`: Contiene los notebooks donde se ejecuta el análisis.
- `data/`: Directorio donde se pueden almacenar datos de entrada o salida.
- `models/`: Carpeta opcional para guardar modelos, si decides entrenarlos en el futuro.
- `scripts/`: Scripts Python para realizar el análisis de tono y tema.
- `requirements.txt`: Dependencias del proyecto.
- `README.md`: Esta documentación.

## Cómo Usar el Proyecto

1. Clona este repositorio:
   ```bash
   git clone https://github.com/tu_usuario/tu-repo.git
   ```

2. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

3. Ejecuta los notebooks en `notebooks/` para inferir el tono y el tema.

## Contribuir
Si deseas contribuir, por favor abre un issue o envía un pull request.

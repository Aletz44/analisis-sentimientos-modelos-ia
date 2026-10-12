
# Dataset de sentimientos: origen, estructura y reproducción

## 1. Origen del dataset

Para este proyecto utilicé el conjunto de datos **Amazon Reviews Multi en español**, disponible en Hugging Face:

https://huggingface.co/datasets/SetFit/amazon_reviews_multi_es

El dataset contiene opiniones de clientes sobre productos y sus respectivas valoraciones. Para realizar el experimento seleccioné exclusivamente registros de la partición oficial de prueba (`test`).

## 2. Selección y preparación

Se seleccionaron 300 opiniones, distribuidas de manera equilibrada:

- 100 negativas.
- 100 neutrales.
- 100 positivas.

Las valoraciones originales se encuentran codificadas de 0 a 4 y se transformaron de la siguiente manera:

| Valoración original | Sentimiento asignado |
|---|---|
| 0 y 1 | NEG (Negativo) |
| 2 | NEU (Neutral) |
| 3 y 4 | POS (Positivo) |

Se utilizó `random_state=42` para facilitar la reproducción de la muestra.

Las etiquetas representan una aproximación basada en las estrellas asignadas por los usuarios y no una clasificación manual del contenido de cada opinión.

## 3. Estructura del dataset

El archivo generado se denomina `dataset_sentimientos_300.csv` y contiene cuatro campos:

| Campo | Descripción |
|---|---|
| `id_resena` | Identificador original de la reseña. |
| `comentario` | Texto de la opinión escrita en español. |
| `valoracion_original` | Valoración original codificada de 0 a 4. |
| `sentimiento` | Categoría asignada: NEG, NEU o POS. |

## 4. Reproducción del procedimiento

El código utilizado para obtener y preparar el dataset se encuentra en la primera celda del notebook:

[Actividad_4_ABG.ipynb](../notebooks/Actividad_4_ABG.ipynb)

Para reproducir el procedimiento:

1. Abrir el notebook en Google Colab.
2. Activar una GPU compatible.
3. Ejecutar la primera celda, que instala las dependencias, descarga el dataset y selecciona las 300 opiniones.
4. Verificar que se genere el archivo `dataset_sentimientos_300.csv` en la carpeta `/content/` de Google Colab.

No es necesario ejecutar un script Python independiente, ya que el procedimiento está integrado en el notebook.

## 5. Disponibilidad y condiciones de uso

Las reseñas originales proceden del conjunto de datos de Amazon. Para respetar sus condiciones de uso, el archivo CSV con las 300 opiniones no se redistribuye en este repositorio público.

Los datos pueden obtenerse desde Hugging Face mediante el procedimiento documentado en el notebook, respetando las condiciones de uso establecidas por Amazon.

Licencia original:
https://github.com/awslabs/open-data-docs/blob/main/docs/amazon-reviews-ml/license.txt

## 6. Consideraciones metodológicas

La muestra contiene 100 registros por categoría y utiliza una semilla aleatoria fija para facilitar su reproducción.

Los resultados obtenidos corresponden a las condiciones del experimento. La reproducción exacta también depende de conservar la misma versión del dataset y de las bibliotecas utilizadas.

Además, debe considerarse que el modelo BETO fue ajustado previamente con reseñas de Amazon, por lo que su desempeño podría variar al utilizar opiniones de otras fuentes.
  

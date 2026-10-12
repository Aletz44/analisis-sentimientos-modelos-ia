# Análisis comparativo de modelos preentrenados de inteligencia artificial para la clasificación de sentimientos en opiniones de clientes

## 1. Descripción del proyecto

Este proyecto tiene como objetivo comparar tres modelos preentrenados de procesamiento de lenguaje natural (PLN) para identificar sentimientos positivos, negativos y neutrales en opiniones de clientes escritas en español.

Para realizar el experimento utilicé Google Colab, la plataforma Hugging Face y un conjunto de 300 reseñas de productos de Amazon. La finalidad fue identificar qué modelo ofrece mejores resultados de clasificación y cuál requiere menos tiempo de procesamiento.

## 2. Modelos y conjunto de datos

Los modelos evaluados fueron:

- **RoBERTuito:** especializado en el procesamiento de textos en español.
- **BETO:** modelo para español, ajustado para clasificar sentimientos en reseñas de productos.
- **XLM-RoBERTa:** modelo multilingüe adaptado para el análisis de sentimientos.

El conjunto de datos utilizado fue [Amazon Reviews Multi en español](https://huggingface.co/datasets/SetFit/amazon_reviews_multi_es), disponible en Hugging Face.

Se seleccionaron 300 opiniones de la partición oficial de prueba, distribuidas en 100 negativas, 100 neutrales y 100 positivas.

## 3. Entorno de ejecución

El experimento se realizó utilizando:

- Google Colab con GPU NVIDIA Tesla T4.
- Python y PyTorch 2.11.0.
- Transformers 4.57.6.
- Datasets 4.8.5.
- Bibliotecas complementarias: Pandas, Scikit-learn y Matplotlib.

## 4. Instrucciones de ejecución

1. Descargar o abrir el notebook `Actividad_4_ABG.ipynb` desde la carpeta `notebooks/`.
2. Abrir el archivo en Google Colab.
3. Activar una GPU desde **Entorno de ejecución → Cambiar tipo de entorno de ejecución**.
4. Ejecutar las celdas en orden, comenzando por la instalación de dependencias y la carga de modelos y datos.
5. Ejecutar el pipeline de inferencia y el cálculo de métricas.
6. Revisar las tablas, matrices de confusión y gráficos de latencia generados.

Los modelos y el dataset utilizados son públicos, por lo que no es obligatorio configurar un token de Hugging Face para descargar estos recursos.

## 5. Resultados principales

| Modelo | Accuracy | F1-score macro | Tiempo promedio |
|---|---:|---:|---:|
| RoBERTuito | 61.67 % | 57.84 % | 1.5962 s |
| BETO | 73.33 % | 71.43 % | 1.8403 s |
| XLM-RoBERTa | 58.00 % | 51.58 % | 1.7516 s |

Los tiempos corresponden al procesamiento de 300 opiniones, con cinco mediciones por modelo.

## 6. Conclusiones

BETO obtuvo el mejor desempeño en la clasificación de sentimientos, mientras que RoBERTuito presentó el menor tiempo de procesamiento.

Para el caso de uso evaluado, considero que BETO es la alternativa más adecuada, ya que la calidad de clasificación tiene mayor importancia que la pequeña diferencia de tiempo observada.

Sin embargo, los tres modelos presentaron dificultades para identificar opiniones neutrales. Además, BETO fue ajustado previamente con reseñas de Amazon, por lo que sería conveniente comprobar su desempeño con opiniones de otras fuentes antes de utilizarlo en un entorno real.

## 7. Estructura del repositorio

- `README.md`: descripción, instrucciones y resultados del proyecto.
- `requirements.txt`: dependencias necesarias para ejecutar el experimento.
- `data/`: dataset de 300 opiniones y documentación de su origen.
- `notebooks/`: cuaderno de Google Colab con el código y los resultados.
- `results/`: tablas y gráficos generados durante la evaluación.
- `src/`: documentación de la ubicación del código reproducible, incluido en el notebook.

## 8. Consideraciones de reproducibilidad

El experimento utiliza una muestra equilibrada de 300 opiniones, seleccionada mediante una semilla aleatoria fija (`random_state=42`).

Las métricas y los tiempos registrados corresponden a las condiciones utilizadas durante las pruebas. Los resultados podrían variar dependiendo de la versión de las bibliotecas, la disponibilidad de GPU y las condiciones del entorno de ejecución.

El código utilizado para obtener y preparar el dataset se encuentra en la primera celda del notebook, por lo que no es necesario ejecutar un script adicional.

---

**Proyecto académico:** Gestión de Proyectos de Inteligencia Artificial — Maestría en Inteligencia Artificial, Universidad Tecmilenio.

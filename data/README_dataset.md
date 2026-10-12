# Dataset de sentimientos: origen, estructura y reproducción

## Origen
Se utiliza el dataset SetFit/amazon_reviews_multi_es, alojado en Hugging Face. Contiene reseñas de productos en español y valoraciones. La muestra del proyecto procede exclusivamente de la partición test.

## Selección
Se obtienen 300 opiniones: 100 negativas, 100 neutrales y 100 positivas. La columna original label codifica de 0 a 4 las valoraciones de 1 a 5 estrellas.

Se transforma:
- 0-1 a NEG.
- 2 a NEU.
- 3-4 a POS.

Se utiliza random_state=42 para reproducir la selección. Las etiquetas son una aproximación basada en estrellas, no una revisión manual del sentimiento.

## Estructura del CSV
Campo	Descripción
id_resena	Identificador original de la reseña.
comentario	Texto de la opinión en español.
valoracion_original	Etiqueta numérica original, de 0 a 4.
sentimiento	Clase derivada: NEG, NEU o POS.
Reproducibilidad: el README original también incluye instrucciones para instalar dependencias, generar el CSV, comprobar su integridad mediante SHA-256 y documentar las limitaciones de reproducción.

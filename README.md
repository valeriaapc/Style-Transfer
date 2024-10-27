# Style-Transfer

## Autores
Sahian P. Martinez \
Valeria Palma

## Problema y Motivación
La transferencia de estilo de imágenes consiste en transformar una imagen de contenido para que adopte las características estilísticas de otra, manteniendo su estructura principal. Este proyecto aborda este desafío aplicando redes neuronales convolucionales (CNNs) con una arquitectura de autoencoder, que emplea una red VGG16 preentrenada como codificador y decodificadores diseñados a medida. La motivación radica en el creciente interés por aplicaciones creativas en arte y diseño, utilizando redes profundas para generar imágenes visualmente únicas, además de abordar retos técnicos, como el ajuste de características y la evaluación objetiva de la transferencia de estilo.

## Objetivos del Proyecto
- Desarrollar un sistema de transferencia de estilo basado en CNNs con arquitectura de autoencoder, empleando VGG16 como codificador.
- Implementar la transferencia de estilo entre imágenes de contenido y estilo mediante una transformación de características de blanqueamiento y coloreado.
- Diseñar métricas cuantitativas para evaluar objetivamente la calidad de la transferencia de estilo.
  
## Base de Datos
Para el entrenamiento se utilizará la base de datos COCO Train 2017, debido a su amplia variedad de imágenes realistas. Es necesario un preprocesamiento que asegure la uniformidad en las dimensiones y el formato de las imágenes antes de ingresarlas a la red VGG16.

## Pre-procesamiento de Datos
El preprocesamiento incluye:

- Redimensionado de las imágenes a 224x224 píxeles.
- Conversión de formato a RGB si la imagen de la base de datos es el blanco y negro.
- Normalización de los valores de píxeles para adaptarse a los requerimientos de entrada de VGG16.

## Definición del Algoritmo
Se emplea un autoencoder con CNNs, utilizando VGG16 como codificador. La justificación de este enfoque radica en la capacidad de VGG16 para extraer características profundas de la imagen que permiten una fiel representación del contenido y el estilo. \
((((( Acá falta hablar de las capas que se usaron del encoder y por qué )))))


## Salidas Deseadas y Optimización
#### Salida deseada: 
Imagen generada que mantenga la estructura de la imagen de contenido y aplique las características estilísticas de la imagen de estilo.
#### Principio de optimización: 
Optimización basada en el método de descenso de gradiente, utilizando el optimizador Adam. Además el uso del error cuadrático medio (MSE) para minimizar la diferencia entre las imágenes reconstruidas y las de referencia.

## Criterios de Parada y Parámetros a Ajustar
Criterio de detención: Reducción estable en el MSE durante el entrenamiento.
### Parámetros:
Dimensiones y filtros de cada capa en el decodificador.\
Valor de aprendizaje del optimizador Adam.

## Software y Lenguaje de Programación
Software principal: Python, con uso de bibliotecas como PyTorch para la implementación de las redes neuronales.

## Resultados Esperados y Medidas de Desempeño
### Resultados esperados: 
Generación de imágenes que mantengan el contenido con el estilo aplicado.
### Propuesta de medidas de desempeño:
Histograma de colores para evaluar la similitud de color.\
Frechet Inception Distance (FID) para la calidad de la transferencia.\
Matriz de Gram para evaluar la fidelidad del estilo transferido.\

## Recursos computacionales:
- GPU para entrenar las redes CNN y procesar el WCT.
- Tiempo estimado: Cada simulación de entrenamiento completo toma horas.
- Simulaciones: 10-15 simulaciones para ajustar parámetros y evaluar métricas de desempeño.

## Cronograma de Actividades (Carta GANTT)
![Gráfico diagrama  carta gantt para actividades o proyectos color pastel imprimible](https://github.com/user-attachments/assets/6d33059c-05a5-4752-a98f-b0c271fad2fd)


## Referencias
Gatys, L. A., Ecker, A. S., & Bethge, M. (2016). "Image Style Transfer Using Convolutional Neural Networks". IEEE Transactions on Neural Networks and Learning Systems.
Li, Y., Fang, C., Yang, J., et al. (2017). "Universal Style Transfer via Feature Transforms". Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition.

## Resultados Preliminares
Se ha completado la fase de entrenamiento del autoencoder con una capacidad aceptable de reconstrucción de imágenes. Los primeros experimentos muestran que el modelo preserva los elementos visuales clave del contenido. Los próximos pasos incluirán la implementación completa de la técnica WCT y la evaluación de las métricas propuestas.


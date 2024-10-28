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
Para el entrenamiento se utilizará la base de datos COCO Train 2017, debido a su amplia variedad de imágenes realistas. Es necesario un preprocesamiento que asegure la uniformidad en las dimensiones y el formato de las imágenes antes de ingresarlas a la red VGG16.\
El enlace a la base de datos utilizada se presenta acontinuación: https://cocodataset.org/#download

## Pre-procesamiento de Datos
El preprocesamiento incluye:

- Redimensionado de las imágenes a 224x224 píxeles.
- Conversión de formato a RGB si la imagen de la base de datos es el blanco y negro.
- Normalización de los valores de píxeles para adaptarse a los requerimientos de entrada de VGG16.

## Definición del Algoritmo
Se emplea un autoencoder con CNNs, utilizando VGG16 como codificador. La justificación de este enfoque radica en la capacidad de VGG16 para extraer características profundas de la imagen que permiten una fiel representación del contenido y el estilo. 


## Salidas Deseadas y Optimización
#### Salida deseada: 
Imagen generada que mantenga la estructura de la imagen de contenido y aplique las características estilísticas de la imagen de estilo.
#### Principio de optimización: 
Optimización basada en el método de descenso de gradiente, utilizando el optimizador Adam. Además el uso del error cuadrático medio (MSE) para minimizar la diferencia entre las imágenes reconstruidas y las de referencia.

## Criterios de Parada y Parámetros a Ajustar
Criterio de detención: Pendiente positiva en la curva de validación de Loss.
### Parámetros:
Dimensiones y filtros de cada capa en el decodificador.\
Número de imágenes a usar en el entrenamiento.\
Número de épocas de entrenamiento.

## Software y Lenguaje de Programación
Software principal: Python, con uso de bibliotecas como PyTorch para la implementación de las redes neuronales.

## Resultados Esperados y Medidas de Desempeño
### Resultados esperados: 
Generación de imágenes que mantengan el contenido con el estilo aplicado.
### Propuesta de medidas de desempeño:
Histograma de colores para evaluar la similitud de color.\
Frechet Inception Distance (FID) para la calidad de la transferencia.\
Matriz de Gram para evaluar la fidelidad del estilo transferido.

## Recursos computacionales:
- GPU de 5.5 GB para entrenar las redes CNN.
- Tiempo estimado: Cada simulación de entrenamiento completo toma aproximadamente una hora y media.
- Simulaciones: 5 simulaciones para ajustar parámetros y evaluar métricas de desempeño y se aproximan 13 simulaciones para cumplir todos los objetivos del proyecto.

## Cronograma de Actividades (Carta GANTT)
![Gráfico diagrama  carta gantt para actividades o proyectos color pastel imprimible](https://github.com/user-attachments/assets/6d33059c-05a5-4752-a98f-b0c271fad2fd)


## Referencias
- Li, Y., Fang, C., Yang, J., Wang, Z., Lu, X., & Yang, M. H. (2017). Universal style transfer via feature transforms. In Advances in neural information processing systems (pp. 386-396). https://arxiv.org/abs/1705.08086 
- T.-Y. Lin et al., “Microsoft Coco: Common Objects in Context,” Lecture Notes in Computer Science, pp. 740–755, 2014. doi:10.1007/978-3-319-10602-1_48 
- Simonyan, K., & Zisserman, A. (2014). Very deep convolutional networks for large-scale image recognition. arXiv preprint arXiv:1409.1556 
- Gatys, L. A., Ecker, A. S., & Bethge, M. (2016). "Image Style Transfer Using Convolutional Neural Networks". IEEE Transactions on Neural Networks and Learning Systems.

## Resultados Preliminares
Se ha completado la fase de entrenamiento del autoencoder con una buena capacidad de reconstrucción de imágenes. Los primeros experimentos muestran que el modelo preserva los elementos visuales clave del contenido. Los próximos pasos incluirán la implementación completa de la técnica WCT y la evaluación de las métricas propuestas.

![resultado gato](https://github.com/user-attachments/assets/f9f15b99-1b8c-4287-98d5-d98f50849bff)


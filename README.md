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
- Matriz de Gram  y LPIPS (Learned Perceptual Image Patch Similarity) para evaluar la fidelidad del estilo transferido.\
- Perceptual Loss y SSIM (Structural Similarity Index) para evaluar la fidelidad con la imagen de contenido.\
- Tradeoff Content-Style para evaluar el equilibrio entre contenido y estilo a partir de valor ajustable. 
 
## Recursos computacionales:
- GPU de 5.5 GB para entrenar las redes CNN.
- Tiempo estimado: Cada simulación de entrenamiento completo toma aproximadamente una hora y media.
- Simulaciones: 5 simulaciones para ajustar parámetros y evaluar métricas de desempeño y se aproximan 13 simulaciones para cumplir todos los objetivos del proyecto.

## Cronograma de Actividades (Carta GANTT)
![Gráfico diagrama  carta gantt para actividades o proyectos color pastel imprimible](https://github.com/user-attachments/assets/6d33059c-05a5-4752-a98f-b0c271fad2fd)

## Resultados

### Reconstrucción de imágenes por bloque.

Se ha completó la fase de entrenamiento del autoencoder con una buena capacidad de reconstrucción de imágenes. Los experimentos muestran que el modelo preserva los elementos visuales clave del contenido. 

![Captura de pantalla 2024-12-08 132602](https://github.com/user-attachments/assets/6454e187-423d-4b80-9b58-c4a56a3194a1)

![Captura de pantalla 2024-12-08 132624](https://github.com/user-attachments/assets/26e04b01-5e0b-4e4f-9bc6-3fe0f1bbc60f)

![Captura de pantalla 2024-12-08 132653](https://github.com/user-attachments/assets/d911004e-3534-4209-aaac-35527cd7c67e)


### Resultados de tranferencia

![Captura de pantalla 2024-12-08 132931](https://github.com/user-attachments/assets/1c7fa60e-3c45-4ac4-aca3-049c7f741370)

![Captura de pantalla 2024-12-08 132909](https://github.com/user-attachments/assets/a18a035a-f09d-4c4d-8c44-adc657f6343e)

![Captura de pantalla 2024-12-08 132853](https://github.com/user-attachments/assets/6e76f1e9-c453-49b1-ad85-cc98c15dfe0d)


### Resultados evaluación métricas.

A partir del resultado obtenido:
![descarga](https://github.com/user-attachments/assets/54035c88-634d-444b-96a9-1259fc3335dc)

Se obtienen la siguiente evaluación:

![Captura de pantalla 2024-12-08 130951](https://github.com/user-attachments/assets/94c93939-2405-46c4-8562-54b15ff1beb0)

SSIM: 0.311. \
LPIPS: 0.729.

#### Comparando con resultados esperados del paper:

![descarga (1)](https://github.com/user-attachments/assets/561076a2-6afd-4371-9bef-e5f975c95461)

Se obtienen la siguiente evaluación:

![Captura de pantalla 2024-12-08 131728](https://github.com/user-attachments/assets/02bc6358-53b9-4c65-8a42-ef1a6e5d8fce)

SSIM: 0.2191. \
LPIPS: 0.7354.

Se puede observar que ambos resultados presentan una evaluación con medidas similares, por lo que se puede concluir que los resultados son competitivos y concuerdan con lo esperado. 

## Referencias
- Li, Y., Fang, C., Yang, J., Wang, Z., Lu, X., & Yang, M. H. (2017). Universal style transfer via feature transforms. In Advances in neural information processing systems (pp. 386-396). https://arxiv.org/abs/1705.08086 
- T.-Y. Lin et al., “Microsoft Coco: Common Objects in Context,” Lecture Notes in Computer Science, pp. 740–755, 2014. doi:10.1007/978-3-319-10602-1_48 
- Simonyan, K., & Zisserman, A. (2014). Very deep convolutional networks for large-scale image recognition. arXiv preprint arXiv:1409.1556 
- Gatys, L. A., Ecker, A. S., & Bethge, M. (2016). "Image Style Transfer Using Convolutional Neural Networks". IEEE Transactions on Neural Networks and Learning Systems.
- “Structural similarity index — skimage 0.24.0 documentation”. scikit-image: Image processing in Python — scikit-image. [En línea]. Disponible: https://scikit-image.org/docs/0.24.x/auto_examples/transform/plot_ssim.html
- “Learned Perceptual Image Patch Similarity (LPIPS) — PyTorch-Metrics 1.5.2 documentation”. Lightning AI. [En línea]. Disponible: https://lightning.ai/docs/torchmetrics/stable/image/learned_perceptual_image_patch_similarity.html



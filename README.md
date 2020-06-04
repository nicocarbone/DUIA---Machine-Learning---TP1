
# Diplomatura Universitaria en Inteligencia artificial

# Machine Learning - Trabajo Práctico 1

Dataset: Breast Cancer Wisconsin (Diagnostic) Data Set
url: http://mlr.cs.umass.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29

## Determinar el problema que se buscará resolver (por ejemplo, “estimar el costo de una vivienda a partir de sus características”) a partir de los datos

El problema a resolver es la clasificación de tumores mamarios en dos categorías definidas: malignos y benignos.

## Describir los datos en términos de sus características y etiquetas (si existen)

Las features se obtienen de una biopsia mediante aspiración con aguja de la lesión mamaria. Las features son:

1. ID number
2. Diagnosis (M = malignant, B = benign)

Por cada núcleo celular (3x):

3. radius (mean of distances from center to points on the perimeter)
4. texture (standard deviation of gray-scale values)
5. perimeter
6. area
7. smoothness (local variation in radius lengths)
8. compactness (perimeter^2 / area - 1.0)
9. concavity (severity of concave portions of the contour)
10. concave points (number of concave portions of the contour)
11. symmetry
12. fractal dimension ("coastline approximation" - 1)

TODO: no queda claro si hay 3 de cada feature porque hay 3 nucleos estudiados o por alguna otra razón. Las imagenes ya no estan disponibles en la web.

La etiqueta se encuentra en la columna 2 y consiste en el diágnostico experto de la biopsia: tumor maligno o benigno.

## Identificar variables que puedan introducir sesgos y establecer acciones correctivas, según corresponda

A priori no parece haber features que puedan introducir sesgos. Por supuesto, la feature de ID number no es relevante para el algoritmo de aprendizaje asi que debe ser descartada.

## Dividir los datos en conjuntos de entrenamiento, validación y test y estudiar si las distribuciones resultantes son similares entre sí

Hecho en el notebook, segun lo visto en clase. 30% para test, 70% para train y validación, de lo cual 90% va a train y 10% a validation. Con este particionado quedaron 358 instancias en train, 171 en test, 40 en validación. 

## Identificar potenciales relaciones entre características y las etiquetas (si existen las etiquetas), o en su defecto entre algunos pares de características. Discutir las relaciones (¿Tienen sentido? ¿A qué pueden deberse?)



## Estandarizar los datos y representar gráficamente un par de características.
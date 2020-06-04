
# Diplomatura Universitaria en Inteligencia artificial

# Machine Learning - Trabajo Práctico 1

Dataset: Breast Cancer Wisconsin (Diagnostic) Data Set
Url: http://mlr.cs.umass.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29
Paper: http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.56.707&rep=rep1&type=pdf

## Determinar el problema que se buscará resolver (por ejemplo, “estimar el costo de una vivienda a partir de sus características”) a partir de los datos

El problema a resolver es la clasificación de tumores mamarios en dos categorías definidas: malignos y benignos.

## Describir los datos en términos de sus características y etiquetas (si existen)

Las features se obtienen de una biopsia mediante aspiración con aguja de la lesión mamaria. Las features son:

1. ID number
2. Diagnosis (M = malignant, B = benign)

Por cada núcleo celular:

0. radius (mean of distances from center to points on the perimeter)
1. texture (standard deviation of gray-scale values)
2. perimeter
3. area
4. smoothness (local variation in radius lengths)
5. compactness (perimeter^2 / area - 1.0)
6. concavity (severity of concave portions of the contour)
7. concave points (number of concave portions of the contour)
8. symmetry
9. fractal dimension ("coastline approximation" - 1)

por cada feature se tiene el valor medio, el extremo mayor y error estándar, dando un total de 30 features. Las features están construidas para que, en teoría, a mayor valor más probable sea que se trate de una célula cancerígena. Se agrupan primero todos los valores medios, luego todos los errores estándar y finalmente todos los extremos. Por lo tanto, en el dataset procesado, las features Nro 0x son los valores medio, las features Nro 1x son los errores estándar y las features Nro 2x son los valores extremo.

La etiqueta se encuentra en la columna 2 y consiste en el diágnostico experto de la biopsia: tumor maligno o benigno.

## Identificar variables que puedan introducir sesgos y establecer acciones correctivas, según corresponda

A priori no parece haber features que puedan introducir sesgos. Por supuesto, la feature de ID number no es relevante para el algoritmo de aprendizaje asi que debe ser descartada.

## Dividir los datos en conjuntos de entrenamiento, validación y test y estudiar si las distribuciones resultantes son similares entre sí

Hecho en el notebook, según lo visto en clase. 30% para test, 70% para train y validación, de lo cual 90% va a train y 10% a validation. Con este particionado quedaron 358 instancias en train, 171 en test, 40 en validación.
En el notebook se hacen dos análisis para determinar si las distribuciones son similares entre si. Por un lado se grafican los histogramas relativos para una determinada feature y para cada partición del dataset. Por otro lado, ya que se trata de una clasificación binaria y no tiene sentido realizar un histograma de las etiquetas, simplemente se cuenta la proporción de instancias clasificadas como malignas y benignas en cada dataset. Ambos análisis muestran que las distribuciones resultantes son similares entre si.

## Identificar potenciales relaciones entre características y las etiquetas (si existen las etiquetas), o en su defecto entre algunos pares de características. Discutir las relaciones (¿Tienen sentido? ¿A qué pueden deberse?)

El dataset contiene información morfológica estadística de la muestra de células de cada tumor. Las 10 features cuentan con 3 medidas estadísticas: el promedio, el error estándar y el peor valor. 
El valor medio y el error estándar codifican información diferente. Mientras que el valor medio da información sobre el atributo en su conjunto, el error estándar da un indicio de cuanto varia ese valor en las celulas de la muestra. Por lo tanto es de esperar que no haya correlación entre ambos, algo que se puede verificar haciendo un scatterplot entre dos features 0x y 1x.
El peor valor, por otro lado, parece estar relacionado con el valor medio y el error estándar. Esto se puede verificar haciendo un scatterplot entre features 0x y 2x, o 1x y 2x y viendo que tienen una relación linea. entre si. Debido a esto puede ser recomendable descartar las features de los peores valores (Nro 2x).

## Estandarizar los datos y representar gráficamente un par de características

Dado que a priori no sabemos los valores máximos y mínimos de varias de las features y que por su origen se espera que sigan una distribución normal, se estandarizaron los datos usando media y desvió.
En el notebook se encuentra el gráfico de un par de características antes y después de la estandarización.
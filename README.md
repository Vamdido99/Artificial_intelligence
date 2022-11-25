
# Clasificación de la calidad del vino rojo según su puntuación
# Presentado por
- *Kamilo Yani Vam Burbano Rincon*
- *Departamento de electrónica y ciencias de la computación* 
- *Pontificia Universidad Javeriana* 
- *Cali, Colombia*  
 - *kamilo990@javerianacali.edu.co*
 
# Introducción

Utilizando  el conjunto de datos de​ Wine Quality, disponible en https://archive.ics.uci.edu/ml/datasets/wine+quality,  se tomo el dataset de vino rojo proveniente del norte de Portugal, el cual consta de 1599 muestras, con 11 atributos de variables fisioquimicas del vino, las cuales son las siguientes: 
 
- *1 - acidez fija*
- *2 - acidez volátil*
- *3 - ácido cítrico*
- *4 - azúcar residual*
- *5 - cloruros*
- *6 - anhídrido sulfuroso libre*
- *7 - anhídrido sulfuroso total*
- *8 - densidad*
- *9 - pH*
- *10 - sulfatos*
- *11 - alcohol*


y una variable de salida 
 
- *12. Calidad , la cual  es la calidad del vino en una puntuación de 0 a 10.*
 
El problema que se busca resolver es implementar un clasificador que permita etiquetar de acuerdo a los parámetros fisicoquímicos del vino, poder asignar una  puntuación del 0 al 10 según  sea su calidad. 
 
# Desarrollo
Para comenzar con la implementación de los clasificadores se realizó una adecuación del Wine Quality dataset, principalmente porque existían en el archivo csv dos columnas “alcohol_” y “density _” que al cargar el dataset que no fueron listadas debido a que eran de tipo objeto, así que se transformaron a tipo float64 , pero existieron algunos pocos valores anormales que python no pudo transformar así que fueron llenados con NAN, luego de se obtuvo todo el dataset de forma numérica, lo que se hizo fue rellenar los valores NAN con la media de cada columna.

Como ya no existían datos nulos y todas las características son numéricas no hizo falta codificar, limpiar o rellenar valores. 
 
Ahora se dividen las etiquetas de las características y se realiza una división del dataset siendo un 10% para evaluar el desempeño final y un 90% para realizar entrenamiento y validación cruzada. Siguiendo el proceso, los datos se normalizaron usando un StandardScaler y las dimensiones de los datos se reducen por medio de PCA, dando de 11 a  9  dimensiones correspondientes a 97.15% de los datos.
 
Se implementaron 3 clasificadores en el  dataset, los cuales fueron:
 
El modelo K-Neighbors Classifier (KNN), para la optimización de los hiper parámetros del clasificador se utilizó el método GridSearch con validación cruzada (GridSearchCV) de 5 pliegues, en el cual se iteraron los parámetros n_vecinos, métrica y pesos.
 
El modelo Gaussian Naive Bayes, para la optimización de los hiper parámetros del clasificador se utilizó el método GridSearch con validación cruzada (GridSearchCV) de 5 pliegues, en el cual se itero la variable de suavizado. 
 
El modelo Random Forest,para la optimización de los hiper parámetros del clasificador se utilizó el método GridSearch con validación cruzada (GridSearchCV) de 5 pliegues, en el cual se iteraron los parámetros n_estimadores, maximas caracteristicas , profundidad máxima y criterio. 
 
 
# Resultados
 
 
Posterior a realizar el entrenamiento y optimización usando GridSearchCV para cada clasificador  se extrajo el F1 Score  y coeficiente de correlación de Matthews por métrica, obteniendo así los siguientes resultados.
 
Para KNN
![image](https://user-images.githubusercontent.com/119079845/204056931-24266dfc-f533-4ae6-8e91-2cd963b1f653.png)


Para Gaussian Naive Bayes

![image](https://user-images.githubusercontent.com/119079845/204056973-203712b8-eb65-4c65-ab8a-bf82de9e2b6d.png)
 
 
Para Random Forest

![image](https://user-images.githubusercontent.com/119079845/204057060-fc253298-9335-40f1-9a09-b6655058bd4d.png)

 
# Conclusiones
 
El mejor clasificador para nuestro dataset fue el KNN con  un puntaje de F1 Score de 71% aproximadamente como sabemos que esta métrica no es muy buena utilizamos el coeficiente de correlación de Matthews alcanzado un valor del 55.2% aproximadamente, que como podemos ver esta por encima del 50% pero no es un valor muy alto, para poder conseguir puntajes más altos para los clasificadores se podría  implementar más modelos de clasificación que se hayan visto o no en clase y aumentar los datos de entrenamiento, y de esta manera comparar los resultados y poder decir cual es mejor. 

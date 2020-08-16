# Funk SVD: Crítica y Análisis

**Autor:** Vicente Aguilera Yévenes

Este post presenta un algoritmo utilizado como alternativa para el concurso de recomendación lanzado por Netflix. Este concurso consistía en presentar un sistema con el menor error de predicción de valoraciones de usuarios para ciertas películas. La data entregada consistía en 100M ratings (en escala 1-5), 17K de películas y 500K de usuarios, ordenados como tuplas (User, Movie, Rating).

El autor afirma que realizar recomendaciones basados en sistemas convencionales resultaba extremadamente ineficiente, dado que se contaba con una matriz de 8.5 Billones de entradas ($Users \times Movies$) que presentaba problemas por *sparsity*, esto es, que no todas las celdas contaban con valores (lo que es completamente obvio, ya que difícilmente un usuario ha dejado un rating en todas las películas).

El autor plantea una alternativa que en lo personal encuentro bastante lógica: Buscar relaciones de preferencias basadas en la metadata de las películas y como los usuarios se relacionan con esta metada. Una película se puede desglosar en base a una valoración de su calidad, si es de acción, terror, ciencia ficción, en base a sus actores, etc. Al mismo tiempo, un usuario tiene preferencias en diferentes escalas para estos valores, o *features*. Tomando esto como principio, el usuario plantea utilizar **singular value decomposition** (SVD), para poder entender la preferencia de un usuario por una película como la suma ponderada de sus preferencias para este conjunto de *features*.

Creo que esta variante es una buena alternativa a priori, porque -tal como dice el autor- se reduce la cantidad de valores necesarios, desde 8.5B a $k\times(Users + Movies)$, con $k$ el número de features a analizar.

Además, me parece una buena opción el introducir un acercamiento de Machine Learning al proceso de desarrollo del modelo de SVD, proponiendo un pipeline de enteramiento basado en el aprendizaje en función de la derivada de la función con respecto a los parámetros a inferir.

Con respecto a este pipeline de entrenamiento, es muy buena la acotación que hace el autor de mantener un *caché* con los resultados de los residuales para reducir la complejidad computacional.

No me queda claro por qué la alternativa de aprendizaje que propone el autor en su proceso de entrenamiento no está sujeto a *local minima* como ocurre con backpropagation o la mayoría de los algoritmos basados en el descenso del gradiente, ¿es acaso porque el entrenamiento es por feature de manera unitaria?

Es un tanto confuso que el autor plantee que el valor inicial de los vectores de usuario y películas parten siendo $[0.1, 0.1, ..., 0.1]$ de manera aleatoria, pero que más adelante explique que los valores iniciales sin afectan en la performance del algoritmo.

Me pareció una buena alternativa el trabajar con el *Offset* del usuario, tomando su promedio de ratings, así se maneja en cierta manera la presencia de usuarios pesimistas/optimistas.

Creo que el manejo de ratings *outliers* es muy bueno y tiene bastante fundamento lógico. Sin embargo, me parece un poco "salido de la manga" el asumir normalidad en la distribución de valores para los ratings, me baso en los casos de usuarios como yo que varían su recomendación en base a muchísimos factores y no nos mantenemos en un rating ni en un rango estable. Al mismo tiempo, $k=25$ no se justifica en ningún momento más que con un "seems to work well", ¿puede que sea factor de *overfitting* también? De todas maneras, creo que es un buen aproach para manejo de *average ratings* en situaciones donde hay pocos datos, y sin caer en problemas por *sparsity* cuando hay muchos.

Encontré excelente el uso de la regularización de Tikhonov para tratar el overfitting del modelo. No obstante, creo que no se le dió la suficiente profundidad de análisis al tema del overfitting del modelo, creo que el autor no mencionó el uso de otras herramientas para tratamiento de overfitting y aquellas que si utilizó (por ejemplo la selección de la cantidad de epochs) fueron totalmente azarosas a mi parecer, ¿por qué no se menciona el uso de cross-val para el proceso de entrenamiento y *tuning*? si el problema recae en la cantidad de features que inducen overfitting, ¿por qué no se presentaron alternativas para reducción de dimensionalidad como PCA?




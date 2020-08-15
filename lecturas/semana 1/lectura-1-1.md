# Item-Based Collaborative Filtering Recommendation Algorithms: Crítica y Análisis

**Autor:** Vicente Aguilera Yévenes

Este paper introduce una variante de *Collaborative Filtering* para la realización de recomendaciones personalizadas. Esta nueva alternativa propone un modelo donde las predicciones no se basan en la relación *user-item*, sino que en la relación *item-item*, de modo que la recomendación se haga en torno a items similares a los que el *usuario objetivo* ha accedido, y no en los items a los que usuarios similares al *usuario objetivo* (vecinos) han accedido. 

La razón de la búsqueda de nuevas alternativas para algoritmos de filtrado colaborativo es la mejora en el desempeño, dado que la cantidad de usuarios de un sistema crece sostenidamente y con ellos también la complejidad de los algoritmos utilizados hasta ese entonces (principalmente *user-based*), sin dejar de lado la calidad de las recomendaciones, es decir que sigan siendo igual de buenas. 

Este *trade-off* entre complejidad y calidad de la recomendación es abarcado por esta nueva variante *item-item*. La recomendación se genera analizando vecindades para items, y una vez que se encuentra a los items similares, se realiza una suma ponderada para predecir el rating.

En primer lugar, no estoy muy convencido de que se aborde la *sparsity* de los datos. Se dice en el paper que los algoritmos *user-based* presentan este problema porque en sistemas de gran escala, difícilmente el 1% de los usuarios ha interactuado con todos los items (para generar una matriz útil), pero al mismo tiempo los algoritmos *item-based* calculan la similaridad entre items basados en aquellos que poseen rating para un mismo usuario (*ver Figura 1*). Si un usuario posee pocos ratings, ¿no se entran en el mismo problema de *sparsity*? En este mismo sentido, ¿qué se hace con los nuevos usuarios? ¿se les hacen preguntas de entrada sobre items a los que es más afecto?

![](img/item_based_similarity_matrix.png)

Me parece una buena opción el trabajar con *Adjusted Cosine Similarity*, para manejar el caso de usuarios pesimistas u optimista, normalizando los ratings para diferentes items.

Creo que introducir el alcance *Model-size* es una buena alternativa para **tratar** el tema de la escalabilidad, pero no lo veo como la bala de plata para este tipo de problemas, sino que como un calmante al dolor, porque en sistemas con una inmensa cantidad de items (como lo puede ser cualquier e-commerce de gran escala), no se asegura esta condición *estática* de los items.

En cuanto al procedimiento experimental, me parece un poco extraño que en la selección del *benchmark UB system* no se haya tomado en consideración el *performance* del mismo, ¿no es este uno de los problemas que se quiere solucionar con el acercamiento *IB*? Creo que una mejor alternativa es hacer el paralelismo de rendimiento para condiciones similares de ejecución.

Pienso que el fenómeno que ocurre con la variante de predicción en base a un *rating* obtenido por regresión lineal es bastante interesante. Al comienzo la predicción es buena (con un bajo MAE), pero a medida que se aumenta en la cantidad de vecinos, la regresión lineal introduce un sesgo que vuelve la predicción aún más mala que el sistema *UB*. ¿Se puede concluir que para bajas densidades de datos esta alternativa es mejor o simplemente es un fenómeno aislado? Hubiese sido interesante ahondar en eso.

Finalmente, creo que el paper demuestra de muy buena manera, con evidencia experimental, que la opción *Item Based* posee un mejor rendimiento que los *User Based*, manteniendo la calidad de la recomendación. De todas formas, se presenta de manera como una opción general, pero como mencioné anteriormente, es aplicable en casos particulares donde los usuarios han hecho suficientes ratings en los items, y que a su vez estos items tengan poca variabilidad y un tamaño relativamente estático, porque -como se menciona- el algoritmo tiene complejidad $O(n^2)$, siendo $n$ la cantidad de items. No es una buena opción para ecosistemas con una cantidad de items incrementales en el tiempo. Si nos ponemos en el caso de Netflix, que lanza contenido de manera periódica, con un intercambio constante de material, un acercamiento *Item Based* puede rendir mejor que uno *User Based*, pero aún así seguirá siendo ineficiente.


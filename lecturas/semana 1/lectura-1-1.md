# Item-Based Collaborative Filtering Recommendation Algorithms: Crítica y Análisis

**Autor:** Vicente Aguilera Yévenes

Este paper introduce una variante de Collaborative Filtering para la realización de recomendaciones personalizadas. Esta nueva alternativa propone un modelo donde las predicciones no se basan en la relación *user-item*, sino que en la relación *item-item*, de modo que la recomendación se basa en items similiares a los que el *usuario objetivo* ha accedido, y no en los items a los que usuarios similares al *usuario objetivo* han accedido. 

La razón de la busqueda de nuevas alternativas para algoritmos de filtrado colaborativo es la mejora en el desempeño de estos mismos, dado que la cantidad de usuarios de un sistema crece sostenidamente y con ellos también la complejidad de los algoritmos utilizados hasta ese entonces (principalmente *user-based*), sin dejar de lado el *performance* del mismo algoritmo, esto es, que las recomendaciones sigan siendo igual de buenas. Este *trade-off* entre complejidad y calidad de la recomendación es abarcado por esta nueva variante *item-item*.

En primer lugar, no estoy muy convencido de que se aborde la *sparsity* de los datos. Se dice en el paper que los algoritmos *user-based* presentan este problema porque en sistemas de gran escala, dificilmente el 1% de los usuarios ha interactuado con todos los items (para generar una matriz útil), pero al mismo tiempo los algoritmos *item-based* generan la similaridad de items basados en aquellos que poseen rating para un mismo usuario (*ver Figura 1*), si un usuario posee pocos ratings, ¿no se entran en el mismo problema de *sparsity*? En este mismo sentido, ¿qué se hace con los nuevos usuarios? ¿se les hacen preguntas de entrada sobre items a los que es más afecto?

![](img/item_based_similarity_matrix.png)

Me parece una buena opción el trabajar con *Adjusted Cosine Similarity*, para manejar el caso de usuarios pesimistas u optimista, normalizando los ratings para diferentes items.


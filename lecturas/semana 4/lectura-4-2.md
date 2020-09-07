# Document Clustering Based On Non-negative Matrix Factorization: Crítica y análisis

Autor: Vicente Aguilera Yevenes

Este paper presenta un método de *clusterización* de documentos basados en factorización no negativa de la matriz de documentos de un *corpus* determinado. El valor central de esta metodología está en la matriz de factorización no negativa, donde cada eje representa un tópico base de un *cluster* de documento, y por consiguiente los documentos se presentan como sumas ponderadas de cada uno de estos tópicos base. 

Se menciona que la gran diferencia entre NMF y SVD es que los espacios semánticos latentes de NMF no deben ser necesariamente ortogonales y que cada documento solo toma valores positivos, facilitando la tarea de *clusterización* sin necesidad de recurrir a técnicas auxiliares de *clustering* (como debe hacer SVD).

Creo que la descripción de métodos relacionados (utilizados hasta el momento) es bastante buena y deja en claro la necesidad de implementación de una metodología mucho más eficiente. Por ejemplo, los métodos *Agglomerative* no tienen posibilidad de escalar a grandes fuentes de datos por su complejidad $O(n^2\log n)$. Sin embargo se menciona que *Naive Bayes* puede tener problemas por los supuestos de independencia que se hacen, pero en Pazzani y Billsus [1] se menciona que *Naive Bayes* tiene un buen rendimiento, ¿Se refieren a la misma tarea?

En cuanto al método propuesto, me hace mucha lógica que los documentos se representen como sumas ponderadas de tópicos que lo componente (sin incluir restas), esto es bastante cercano a la realidad y facilita el entendimiento (ya que un documento es un tanto A y un tanto B, no un tanto A, menos B y un tanto C), en conjunto con la no negatividad de los valores de la matriz. Sin embargo, en cuanto a la no ortogonalidad, me genera dudas como NMF puede asegurar una mayor certeza en el *clustering* cuando los espacios semánticos latentes son muy similares, ¿qué ocurre si existen colisiones? Surge la duda ya que a diferencia de LSI, se puede observar que este último genera una especie de límite:

<img src="img/NMF_LSI_SPACE_VEC.png" style="zoom: 80%;" />

Además, creo que la idea de generar factorización matricial para representar el grado de afinidad de un termino $f_i$ con diferentes *clusters* que componen el corpus, así como representar el grado de afinidad de un documento $i$ con diferentes *clusters*, es una muy buena medida que permitiría generar información escondida al igual que SVD con los factores latentes y sirve para segmentar la información contenida de manera sencilla. Junto con esto, creo que aplicar normalización a las matrices fue una excelente medida para asegurar unicidad en la solución.

De manera teórica, se puede observar que el desempeño de NMF es mucho mejor que SVD, dando un cierto grado de linealidad en relación a la cantidad de datos utilizados, lo que va de la mano con la escalabilidad de la solución ($O(tkn)$), sumado a esto, queda claro con el sencillo ejemplo mostrado en el paper que la tarea de encontrar el *cluster* al que pertenece cada dato es mucho más fácil en NMF que en SVD.

Me parece extraño lo que se reporta al final sobre NMF al momento de hacer la pruebas, ya que se sometió a 10 rondas de trial para encontrar aquel que minimizaba el error cuadrado $J$. Por un lado, se necesita data externa que muchas veces no se tiene (y que si se ocupa la de entrenamiento puede incurrir en *overfiting*) y por otro, representa una tarea extra que agrega complejidad.

En cuanto a los datasets utilizados, pienso que es bueno que se haya utilizado dos datasets para hacer las pruebas, ya que uno se diferencia de otro en la forma compacta y enfocada de los *clusters*, lo que permite analizar el comportamiento de los diferentes algoritmos en situaciones distintas.

### Referencias:

[1] Pazzani, M. J., & Billsus, D. (2007). Content-based recommendation systems. In The adaptive web (pp. 325-341). Springer Berlin Heidelberg. Xu, W., Liu, X., & Gong, Y. (2003).




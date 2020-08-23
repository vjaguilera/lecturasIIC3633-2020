# BPR: Bayesian Personalized Ranking from Implicit Feedback

Autor: Vicente Aguilera Yévenes

Existen diferentes propuestas para realizar recomendaciones a partir de feedback implícito. Se encuentra por ejemplo los métodos basados en factorización matriciales y los basados en kNN, pero ninguno de ellos se encuentra directamente optimizado para generar un ranking ordenado de elementos.

Este paper presenta el criterio de optimización denominado **BPR-Opt**, además de un algoritmo de aprendizaje denominado **LearnBPR** basado en SGD con *bootstrap sampling*. Finalmente, se presenta la aplicación de este criterio de optimización en diferentes modelos de recomendación para feedback implícito y se analizan los resultados.

Encuentro muy interesante la propuesta de que el criterio de optimización debe centrarse en generar una lista de elementos ordenados por ranking que cumplen con un criterio de orden total. Este problema se vuelve más interesante al considerar que solo existe feedback positivo con respecto a los items (no es tan sencillo como cuantificar cual item es bueno y cual es malo desde el punto de vista del usuario, o cual es o no de su gusto).

Creo que la propuesta de utilizar pares de items para el entrenamiento es muy buena, sin embargo hay un supuesto muy relevante al momento de diseñar el orden de los items, este es que si el usuario $u_i$ vio el item $i_k$ y no el item $i_l$, entonces se asume que el usuario prefiere el item $i_k$ sobre el $i_l$. Esto deja fuera los casos bordes donde un usuario interactúa no por real interés en los elementos (comprar regalos, interacción por error, etc). Creo que se pudo haber agregado alguna regularización en este sentido, como lo hace Hu et al. planteando su *momentum effect*.

Muy bien el hecho de generar conjuntos disjuntos de entrenamiento y testing, de esta manera la evaluación del desempeño de la implementación de BPR es menos sesgada.

Con respecto al planteamiento del BPR, ¿es correcto asumir independencia entre usuarios? Pienso que esto deja fuera del modelamiento el hecho de que usuarios se rijan por comportamientos de sus pares, situación que en lo personal me ocurre (si un amigo compró $x$ y me dice que es bueno, yo lo compro), de todas maneras se entiende que para tomar en consideración estos casos es necesaria otra fuente de datos que relacione *amistades* por ejemplo; de todas maneras me causa ruido.

En cuanto al modelo en si, es importante ver que **BPR-Opt** relaciona la probabilidad de que un usuario realmente prefiera el item $i$ sobre $j$, con lo que el modelo utilizado para la recomendación genera, aplicando una regularización dada por el modelo.

En relación al modelo de aprendizaje, encontré muy bueno el argumento que se da para elegir *SGD* sobre *Full GD*, ya que efectivamente puede ocurrir que existan items con muchos ratings realizados por diferentes usuarios, haciendo que estos sean muy dominantes al momento de buscar el óptimo.

Queda claro que el uso de *boostraping* es una buena decisión, permitiendo que el modelo converja más rápido que usando la exploración extensiva de los datos.

Con respecto a los modelos propuestos para utilizar BPR, creo que aplicar regularizaciones en el *MF* es una buena idea para evitar overfitting, pero no queda claro como encontrar los valores de esos parámetros. En relación al *Adaptive kNN*, ¿por qué ocuparon similaridad del coseno? Existe evidencia de que *adjusted-cosine* tiene mejor performance.

Finalmente, en relación a los resultados, se puede observar que:

- La regularización presente en WR-MF es realmente significativa, esto queda claro cuando SVD decrece al aumentar las dimensiones del modelo (ya que cae en overfitting), mientras que WR-MF aumenta.
- Las versiones de BPR son las que tienen un mejor rendimiento, ya que son especializadas en optimizar para ordenar pares de elementos, generando un ranking.
- SVD se encuentra bajo $np_{max}$ para ambos datasets, lo que muestra que esta opción no es capaz de superar el limite teórico para cualquier método de clasificación no personalizada.
# Collaborative Filtering for Implicit Feedback Datasets: Crítica y análisis

Autor: Vicente Aguilera Yévenes

Contar con feedback explicito para los sistemas de recomendación representa un real desafío, generalmente la matriz de datos presenta *sparsity* por esto mismo, lo que se traduce en que la mayoría de las celdas de la matriz no presentan datos. Esta situación contrasta con lo que ocurre con el feedback implícito, dado que este puede ser recolectado sin que el usuario entregue explícitamente un valor (navegación en sitios, clicks, hipervínculos, tiempos de espectador, etc.).

El paper nos presenta una propuesta de sistema recomendador tomando como input el feedback implícito. Los autores listan las principales características de la información implícita, lo que muestra una limitante importante:

- No hay feedback negativo, por lo que los sistemas de recomendación con feedback implícito no puede identificar exactamente aquello que el usuario no prefiere.
- El ruido del feedback implícito representa mucho bias en las predicciones, y los mismos autores los señalan (que un usuario interactúe con un item no significa que necesariamente este le guste).
- Separación entre *preferences* y *confidence*, a mi parecer, el mejor aporte de los autores en el paper, ya que encapsula la idea de interacción con un item y la real preferencia que un usuario tiene por este mismo.
- La evaluación requiere de métricas apropiadas y los autores abordan esto muy bien, dejando en claro el modelamiento por medio de *confidence* y *preference*, además de que la medida de interacción (para su evaluación) es el tiempo que pasa un usuario viendo un programa.

Al momento de explicar la definición del set de variables $c_{ui}$,  no me queda claro la razón de selección de $\alpha = 40$, creo que mostrar evidencia de algún método de evaluación hubiese servido para replicar la búsqueda de valores óptimos en otras variables.

Creo que aplicar el principio de factorización matricial para encontrar una manera de reducir la complejidad computacional es un tremendo aporte por parte de los autores, logrando un algoritmo que corre en tiempo lineal en relación a la cantidad de usuario e items en el input.

Junto con lo anterior, el hecho de que el resultado entregue feedback con respecto a los items que justifican la recomendación es sumamente útil, y destaca en relación a los modelos de factores latentes que estaban presentes en ese entonces. Entregarle esta cualidad de "memory based" a un "latent factor model" es un rotundo logro.

Los mismo autores afirma que su propuesta puede ser usada como un método de pre procesamiento para modelos de kNN, sumando el hecho de que las similaridades entre items se presentan **independientes** del usuario que se analiza, situación que es cercana a la realidad.

La complejidad computacional del algoritmo es $O(f^2n_u + f^3)$ asumiendo que $Y^TY$ es pre calculada, en este sentido ¿se asume que los valores de los items son relativamente estáticos? ¿Que ocurre con la complejidad si los items cambian en el tiempo?

En cuanto a la evaluación, creo que la construcción del set de testeo eliminando los programas que ya se vieron sirve mucho para hacer análisis real del *performance* y *calidad* del algoritmo. Al mismo tiempo, creo que aplicar logaritmo para mantener en la misma escala a los programas con diferentes valores de $r_{ui}$ sirve mucho para acercar el problema a un plano real, como ellos dicen: "hay gente que dejaba el DVR corriendo para guardar programas que no serían vistos".

Creo que el manejo del *momentum effect* pudo ser mejor si se utilizaba un set de datos auxiliar para rectificar que efectivamente el usuario $u$ estuviese viendo el programa $i$ en un determinado tiempo, así no se entra en el juego de los supuestos que ciertamente introduce bias en el modelo.

No me queda claro que ocurre cuando se pasa la barrera de los 200 factores, ¿se introduce overfitting en el modelo?

En cuanto a los resultados, estos muestra un modelo que es capaz de reconocer patrones de visualización periódica (si se cuentan dentro del test set), siendo capaz de predecir cuando es momento de ver el programa favorito del usuario, por ejemplo.

Los resultados dejan en claro que tomar en consideración tanto *preferences* como *confidence* resulta en un modelo más robusto, esto se puede deber a que modelar la situación de esta manera permite incorporar comportamiento intrínseco que se asume como constante en los demás modelos.


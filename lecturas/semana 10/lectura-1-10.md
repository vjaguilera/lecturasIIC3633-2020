# Deep Learning based Recommender System: A Survey and New Perspectives: Crítica y análisis

Autor: Vicente Aguilera Yévenes

Este trabajo se presenta como un recopilado actualizado con información y lecturas relacionadas a la aplicación de Deep Learning en Sistemas Recomendadores, introduciendo categorías y clasificaciones relacionadas a las distintas arquitecturas, aplicaciones y objetivos que se buscan al aplicar alguna técnica de Deep Learning en la recomendación.

Para partir, creo que es un trabajo sumamente completo y meticuloso: Contiene un introducción precisa que nos habla sobre la creciente tendencia en la aplicación de Deep Learning en todos los aspectos de la vida, siendo el de *Sistemas Recomendadores* uno de los principales involucrados. El trabajo nos presenta un resumen sobre los sistemas recomendadores y cual ha sido el alcance que han tenido hasta antes de la irrupción de Deep Learning. Nos presenta las distintas técnicas de Deep Learning y cual es el área/objetivo principal de cada una, y además nos presenta justificaciones de por qué Deep Learning tiene el impacto que tiene y cuales son las principales desventajas del mismo.

Con respecto a las desventajas que presenta el autor, hay una que llamó bastante mi atención, y tiene que ver con la **interpretabilidad** de los resultados. Creo que es sumamente importante y relevante al momento de evaluar un sistema recomendador, que este sea capaz de explicar el por qué de su recomendación, sobre todo cuando el sistema es presentado frente a un usuario que lo utilizará y evaluará. Mientras más noción de control y poder tenga el usuario, más satisfecho se encontrará este con el desempeño del sistema (Pu et.al, 2011). Es importante tener en cuenta que una de las principales formas de hacer verle a un usuario que tiene el control sobre el sistema es explicándole el origen de la recomendación y qué justifica el resultado (Parra et.al, 2014).

Con respecto a la aplicación de **Multiperceptron**, creo que es una buena idea la incorporación de este en la aplicación de filtrado colaborativo para alivianar el trabajo de factorización matricial, pero ¿es realmente un aporte en la tarea de recomendación o es una generalización del trabajo previo? Si bien agrega la capacidad de encontrar relaciones no lineales, ¿es un aporte significativo esto para una matriz de dos dimensiones con interacciones discretas?

En relación a *Wide & Deep Learning*, los autores señalan: "*This model improve the accuracy as well as the diversity of the recommendation*", pero ¿como se puede mejorar la *accuracy* al mismo tiempo que la diversidad de la recomendación? ¿Esto no viene determinado por el usuario estudiado? ¿Esto no se evalúa a través de un ciclo continuo de interacción usuario-sistema?

También se habla de *Collaborative Metric Learning (CML)* que reemplaza el producto punto de una MF con la distancia Euclidiana, ¿por qué se opta por usarla de manera generalizada? Si bien puede tener buen desempeño en ciertas situaciones, existen casos donde hay relaciones (principalmente semánticas) que la distancia euclidiana no toma en consideración, y la matriz de valores latentes tiene -en cierto sentido- representatividad de estos valores semánticamente similares.

Ya entrando a la descripción de modelos *Deep Structured Semantic*, se nos presenta *Multi View Deep Neural Network*. A pesar de que la idea es muy buena, creo que no es posible generalizar el supuesto subyacente de que "*si dos usuarios comparte gustos por un dominio, entonces deben compartir gustos en otros*". Si, la recomendación es personalizada, pero se siente como un UB-CF mejorado con el hype de Deep Learning.

Cuando se habla de los Autoencoders, se habla también mucho del filtrado colaborativo: ¿estas variantes de filtrado colaborativo con Deep learning presentan las mismas limitantes que los que no utilizan Deep Learning? ¿Sufren de problemas por cold start, por usuarios nuevos o por items nuevos?. Puntualmente se presenta *Collaborative Denoising Auto-Encoder*, que tiene como principal tarea la predicción de ranking, ¿entonces puede ocupar BPR-OPT para la actualización de sus parámetros? Teniendo en consideración que SGD no tiene tan buen desempeño en la tarea de ordenamiento y *rankeo*.

Encuentro muy interesante la combinación que se hace entre algoritmos de Deep Learning para la obtención de *features* o representaciones complejas que son utilizadas por algoritmos clásicos y destacados en eficiencia, como sucede con los Autoencoders y SVD++.

Al momento de presentarse las variantes de CNNs en aplicaciones de recomendación, se presenta el trabajo de Lei et al. Este tipo de recomendador queda muy expuesto a ataques adversarios para introducir *bias* (usuarios que alteren sus gusto y los inviertan). Además, se basa en un supuesto que no siempre se cumple (un usuario interactúa más con elementos que le gustan que aquellos que no le gustan **de manera sostenida**), puede ser que un usuario cambie completamente sus gustos en un periodo de tiempo, por ende quizás esta aplicación es útil en ventanas que representen un corto plazo de aplicación (como el objetivo de sistema de MovieLens), pero en sistemas muy dinámicos con alto intercambio entre sistema-usuario es muy difícil llevarlo a la práctica de manera efectiva.

Queda bastante claro que la principal fortaleza en la aplicación de CNN para sistemas recomendadores es la encontrar características intrínsecas y complejas sobre los ítems con los cuales el usuario interactúa, sin importar el origen o forma de este (multimedia, texto, etc.)



## Referencias:

- Pu, P., Chen, L. and Hu, R. (2011). A user-centric evaluation framework for recommender systems. RecSys'11 - Proceedings of the 5th ACM Conference on Recommender Systems. 157-164.
- Parra, D., Brusilovsky, P., and Trattner, C. (2014). See What You Want to See: Visual User-Driven Approach for Hybrid Recommendation. International Conference on Intelligent User Interfaces, Proceedings IUI
- Chenyi Lei, Dong Liu, Weiping Li, Zheng-Jun Zha, and Houqiang Li. 2016. Comparative Deep Learning of Hybrid Representations for
  Image Recommendations. In Proceedings of the IEEE Conference on Computer Vision and Paern Recognition. 2545–2553
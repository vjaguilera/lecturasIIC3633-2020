# Content-Based Recommendation Systems: Crítica y análisis

Autor: Vicente Aguilera Yevenes

Este paper presenta, a grandes rasgos, lo que son los sistemas recomendadores basados en contenido. Estos sistemas tienen por finalidad recomendar items a usuarios basados en la descripción de los items, y en el perfil de intereses del usuario. Estos sistemas comparten en común los siguientes medios:

- Describir items para ser recomendados
- Generar perfil de usuario con sus preferencias por items
- Comparar items con el perfil de usuarios y sus preferencias

En cuanto al segmento de *alternativas de representación de items*, queda bastante claro (y es bastante intuitivo) que cuando los items están representados de manera estructurada, es mucho más sencillo llevar a cabo la tarea de generar el perfil del usuario para recomendar. Creo que esta sección presenta una disyuntiva que se mantiene a lo largo del texto: *¿Qué hacer cuando la data no está estructurada? principalmente, ¿qué hacer cuando se nos presenta texto libre?* 

En el ejemplo que se proponen, sobre la *diferenciación entre Gray como nombre y no color*, podríamos aplicar técnicas como NER utilizando LSTMs. En base a la fecha se puede identificar que el Deep Learning aún no penetraba en casi todas las áreas del desarrollo tecnológico.

En cuanto a los perfiles de usuarios, *user customization* no está diseñado para sitios de consumo con baja interacción (por ejemplo Instagram no solicita a los usuarios el tipo de contenido que se le desea recomendar). Fintual utiliza este tipo de modelamiento de usuario para generar un perfil de riesgo, dado que su *business logic* no se orienta a la interacción del usuario con el sistema de manera activa (no como en redes sociales). ¿Existen situaciones que escapen a la norma? Algo como hacer *hidden user customization*, de manera esporádica, aleatoria, etc.

Queda muy en claro el uso y aplicación de los diferentes modelos de Machine Learning para la generación de funciones que modelen los intereses de los usuarios, a fin de predecir items recomendados. Sin embargo, creo que la aplicación de modelos de **clasificación lineal** son más cercanos a lo que se necesita en la realidad, ya que como se dice, puede ejecutar de modo *on-line*, sin pasar por el problema de los *new items*.

Creo que Naive Bayes es un método sumamente útil para la clasificación de texto, sin embargo me parece muy extraño que aunque el modelo se basa en la independencia de los atributos de cada componente, tenga una buena performance, ya que esta independencia claramente no se puede inferir ni directamente ni de manera generalizada.

Tal como los autores mencionan, creo que hacer modelos híbridos entre filtrado colaborativo (para encontrar vecindades con respecto a los gustos) y recomendaciones basadas en contenido puede resultar en un mejor desempeño del sistema, se acota la complejidad y se toma como referencia gustos que no corresponden explícitamente a los declarados por los usuarios, situación que -pienso- debe resultar muy provechosa si la data de preferencias es escasa, principalmente en casos donde esta se consigue con una interacción explícita.

Para concluir, hoy en día uno de los campos con más actividad y revolución es el NLP. Juntar ambos mundos (principalmente el de DeepLearning aplicado a NLP) con los algoritmos de recomendación basado en contenido puede resultar en mejores sistemas, tanto por el lado de la eficiencia, como de la correctitud de las recomendaciones, en los casos donde los items se describen por data no estructurada.




# See What You Want to See: Visual User-Driven Approach for Hybrid Recommendation: Crítica y análisis

Autor: Vicente Aguilera Yévenes

Este paper presenta una propuesta de sistema (*SetFusion*) que permite al usuario controlar la relevancia de distintas estrategias de recomendación en el motor que genera un listado de recomendaciones, además de poder visualizar por medio de una interfaz como estas recomendaciones interactúan y se relaciones (con un diagrama de Venn), además de mostrar una justificación de bajo qué estrategia fue recomendado un item (en la lista de items recomendados).

Lo primero que quiero destacar de este paper, es la interpretación que se le da a un sistema que recomienda bien: una mezcla entre *accuracy* a nivel de algoritmo y la satisfacción del usuario al utilizar el sistema. En este trabajo se le dió importancia a la experiencia del usuario y como esta puede incidir directamente en la cualidad de un sistema recomendador. Se intentó estudiar el nivel de control que el usuario tiene sobre el "proceso" de recomendación, lo que se traduce directamente en la capacidad que tiene el usuario de alterar la forma en que se genera la recomendación para maximizar la utilidad percibida del sistema.

En cuanto al sistema propuesto, creo que un aspecto muy importante a considerar al momento de evaluar una interfaz de interacción con usuarios es la complejidad del mismo, y como el usuario interpreta el interfaz y las herramientas que esta provee para poder manipular sus recomendaciones, ya que de cierta manera, esto puede introducir un bias en la calidad del sistema ¿esto de que manera se aborda en el paper?

Creo que la interfaz propuesta es muy buena, ya que permite al usuario entender bastantes cosas sobre la lista de recomendaciones generadas, en particular:

- El diagrama de Venn que muestra los items en cada dominio suma mucho valor para visualizar de manera facil e intuitiva la interacción entre items y como estos generan la recomendación
- Los sliders e inputs para introducir el peso de la recomendación son muy intuitivos para el usuario y permiten entender de mejor manera la composición final del sistema para generar la recomendación
- La lista de recomendaciones, con su justificativo de la estrategia por la cual se obtuvo la recomendación es sumamente valiosa, ya que como se explica, que el usuario entienda de donde surge su recomendación permite que este tengo un control sobre el sistema, lo que aumenta su satisfacción.

Finalmente, con respecto a los resultados, encuentro sorprendente el alcance que tuvo SetFusion, sobretodo en el estudio de UMAP, donde los usuarios interactuaban mucho más de lo cotidiano, e invirtieron un tiempo considerable en el uso del sistema, demostrando que este si tenía valor y que si era de alta calidad en su conjunto (como un todo). Creo que este paper tiene un aspecto más de ingeniería de software, ya que basa su analisis en la aceptación de un producto y de la interfaz utilizando como justificativo del producto el sistema recomendador subyacente, esto lo encuentro muy positivo, ya que deja en claro como un sistema recomendador adquiere valor en la práctica.
# Evaluating Recommendation Systems: Crítica y análisis

Autor: Vicente Aguilera Yévenes

Este paper contiene mucha información útil para aquellas personas que necesitan ahondar en las técnicas necesarias para comparar algoritmos, seleccionar algoritmos, llevar a cabo pruebas sobre algoritmos y para conocer las propiedades que un sistema debe tener. Los autores presentan una especie de "guía" sobre diferentes puntos importantes para realizar una evaluación sobre un sistema recomendador, entre ellas:

- Las propiedades de un sistema recomendador
- Metodologías de evaluación y comparación entre algoritmos
- Configuraciones experimentales para seleccionar algoritmos
- Cómo generar conclusiones sobre experimentos

Creo que el primer y más grande aporte que hacen los autores con este paper es la diferenciación entre 3 tipos de experimentos para conducir un proceso de evaluación entre algoritmos (*offline*, *user studies* y *online experiments*). Primero, cada uno de estos tipos de experimentos presentan sus propias características, son bien independientes (en ciertos aspectos) unos de otros y cada uno tiene diferentes formas de llevarse a cabo, pros y contras; el hecho de que los autores proporcionen este tipo de información a la gente es un tremendo aporte. Segundo, estas 3 categorías toman como fundamentos el método científico, planteando una hipótesis, proponiendo variables, constantes y restricciones a la generalización de resultados, lo que a mi parecer los vuelve fiables y certeros al momento de ser utilizados como punto de partida de un análisis comparativo.

No tengo mucho que agregar o criticar con respecto a la estructuración de cada tipo de experimento propuesto por los autores, son bastante explícitos, claros y precisos al momento de presentar la información y la descripción de los experimentos. Incluso hablan sobre los supuestos de los experimentos (como que en *offline* se trata de utilizar data que emula el comportamiento real del usuario), de los costos (como en *user study* cuando se habla de los *subjects* voluntarios o pagados y el trade-off financiero que esto implica) y de lo que cada tipo de experimento permite conseguir (como en *online* cuando nos dicen que los resultados encontrados son lo más cercano a un comportamiento real).

También creo que los autores hacen un trabajo muy diferente a lo que se está acostumbrado a leer sobre sistemas recomendadores: *presenta el sistema como un producto de software*. Generalmente, los papers de esta área hablan desde un punto de vista más matemático-analítico, sobre rendimiento, métricas, complejidad algorítmica y modelos, a diferencia de este paper que nos habla sobre aquello que -en cierta manera- es más cercano a la realidad: Por más que se construya un algoritmo complejo, implementarlo en un sistema real es otra historia, otro mundo con nuevos desafíos. Se presentan elementos como la *interfaz de usuario*, metodologías de *testing*, experiencia de usuario, diseño de software, infraestructura, seguridad, etc.

Con relación a lo último, creo que estudiar el problema desde este punto de vista es sumamente valioso, porque nos habla del problema real de implementar el sistema como producto de software que usuarios reales utilizarán y evaluarán, más allá de la recomendación que se genere.

Finalmente, creo que los autores hacen un excelente trabajo presentando las diferentes formas de generar conclusiones a partir de los resultados, explicando de manera profunda y con fundamento matemático los diferentes test y metodologías que se pueden (y deben) usar para generalizar conclusiones.
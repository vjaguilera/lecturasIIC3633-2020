# A User-Centric Evaluation Framework for Recommender Systems: Crítica y análisis

Autor: Vicente Aguilera Yévenes

Este paper trata sobre una propuesta de framework para evaluar las recomendaciones desde el **punto de vista del usuario**. Se presenta el framework **ResQue** que consiste en un modelo tipo cuestionario, de 32 preguntas con 15 *constructs* para realizar la evaluación. Algo interesante que plantean las autoras es que su modelo fue comparado y evaluado mediante métodos de análisis psicométricos para validar las conclusiones de los datos.

Lo primero que hay que destacar es la buena investigación de trabajo previo, presentando modelos que sirvieron como sustento para justificar el modelo presentado, y como estos significaron la piedra angular en el desarrollo de **ResQue**. Por ejemplo, se habla del framework propuesto por Knijnenburg et al. plantea *constructs* con características similares a las propuestas en **ResQue** (*perceived accuracy, interaction adequacy, system efectiveness, perceived usefull of the system, diversity* y *beliefs and attitudes*). **ResQue** agrega *privacy* y *situational and personal characteristics*.

En cuanto a las capas de evaluación, con respecto a las cualidades percibidas del sistema, encuentro muy buena la diferencia que se hace entre *Novelty* y *Diversity*, pero creo que se hila muy fino en la aplicación o potenciación de estos aspectos, ya que mucha *novelty* puede resultar poco atractivo para un usuario (entregarle cosas nuevas cuando el usuario es de gusto más conservadores) mientras que la diversidad depende mucho del usuario analizado. En este sentido, puede ser incorporado el nivel de nobleza y diversidad como una característica contextual del usuario?

Personalmente creo que este factor es sumamente relevante y habla muy bien de la personalización de un modelo, ya que es capaz de discriminar el contexto del usuario para personalizar aún más su recomendación

Con respecto a las creencias, estoy muy de acuerdo con darle control al usuario. De esta manera se puede obtener mucha más información de él, aumentando la fuente de información y generando recomendaciones más personalizadas.

Al llegar al punto de *Behavioral Intentions*, pude darme cuenta que efectivamente parte importante de la evaluación del usuario (a modo personal) tiene que ver con la aplicación práctica del sistema recomendador. Este aspecto de los sistemas recomendadores es mucho más "marketero "que conceptual. Es interesante ver como la teoría detrás de un sistema recomendador impacta en aristas del mundo real.

El detalle de los premios dados a los participantes de la encuesta creo que está demás. No aporta información en la línea de estudio del paper

Muy buena la justificación matemática del modelo de correlación entre los *constructs*. Por un lado muestra que la hipótesis se acepta y por otro ayuda a ajustar el modelo, quitándole preguntas (que en el caso práctico, pueden resultar contraproducentes al momento de hacer la encuesta).

Finalmente, creo que este paper tenía un aspecto más de análisis desde el punto de vista de ingeniería de software, diseño y marketing. No había mucho concepto matemático ni un algoritmo nuevo, si no que una métrica de evaluación para implementaciones prácticas de sistemas recomendadores (no como métricas de entrenamiento o de desempeño a nivel de algoritmo).
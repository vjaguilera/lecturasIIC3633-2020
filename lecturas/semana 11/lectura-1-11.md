# Deep Learning based Recommender System: A Survey and New Perspectives: Crítica y análisis

Autor: Vicente Aguilera Yévenes

Este trabajo se presenta como un recopilado actualizado con información y lecturas relacionadas a la aplicación de Deep Learning en Sistemas Recomendadores, introduciendo categorías y clasificaciones relacionadas a las distintas arquitecturas, aplicaciones y objetivos que se buscan al aplicar alguna técnica de Deep Learning en la recomendación. Esta semana se estudió desde el capitulo 3.5 en adelante, abarcando distintos temas como:

- Recomendaciones basadas en RNN
- Recomendaciones basadas en RBM
- Recomendaciones basadas en Neural Attention
- Recomendaciones basadas en Neural AutoRegressive
- Recomendaciones basadas en DRL
- Recomendaciones basadas en redes adversarias (GAN)
- Recomendaciones basadas en modelos híbridos
- Trabajo futuro y problemas abiertos

Es importante partir diciendo que el trabajo es sumamente completo, con mucha bibliografía atingente, pero si creo que desde este punto (3.5) en adelante, los autores se quedaron cortos en cuanto a la profundidad de los temas tratados, quizás porque son técnicas muy novedosas -para ese entonces- o porque no era su foco de atención, no obstante queda la sensación de insatisfacción desde el punto de vista del lector.

En cuanto a los sistemas de recomendación basados en RNN, creo que hubiese sido bueno explicar las diferencias que genera TOP1-max y BPR-max para tratar el problema de vanishing gradient: ¿Cuáles son las diferencias con TOP1 y BPR normal? ¿Cómo abordar el control de Vanishing gradient? ¿Como es la mejora para GRU4Rec en ambos casos? Además, creo que faltó al menos una referencia o indicación de qué es o a que se refiere el *teacher model*.

En relación a los modelos secuenciales que si utilizan el identificador de usuario, me surgen un par de dudas con respecto al análisis del problema como serie de tiempo: ¿Estos modelos incorporan análisis de temporalidades o periodicidades? ¿Es posible mejorar la recomendación si se detectan patrones estacionarios sobre el comportamiento de interacción de los usuarios?

En cuanto a los modelos basados en RNN para *Feature Representation Learning*, ¿puede NRT ser mejorado utilizando modelos generativos en lugar de basarse en factorización matricial? Pienso esto porque la multi-tarea está relacionada con predecir ratings y entregar tips textuales para el usuario.

Luego, en relación a las recomendaciones basadas en *Neural AutoRgressive*, creo hubiese sido bueno explicar un poco lo que es el *Contrastive Divergence algorithm* para poder entender como soluciona el problema de trazabilidad que los modelos basados en RBM no pueden solucionar.

Cuando se habla de los sistemas de recomendación basados en Deep Reinforcement Learning, creo que faltó mencionar otros avances significativos de DRL relacionados, por ejemplo, a Multi Agents encargados de realizar labores de recomendación de manera paralela, optimizando tanto el costo computacional como el regret acumulado, con estrategias entre agentes. Chawla et al (2020) proponen un algoritmo de trabajo multi agente (GosInE) para este tipo de tareas, al mismo tiempo, Vial y Shakkottai (2020) proponen una estrategia basada en blacklisting de agentes para mejorar la recomendación en escenarios multi agentes.

Para los modelos híbridos que combinan CNN con RNN, encuentro muy interesante la propuesta de encoder-decoder, pero siento que es muy limitada a situaciones donde es necesario extraer features de elementos complejos (como multimedia o texto), y no aplica para escenarios más simples de recomendación.

Pienso que los problemas abiertos y trabajos futuros son diversos y desafiantes, pero hay uno que llama mucho mi atención: Machine Reasoning. Es lo que se encuentra en boga hoy en día, cuando vemos modelos de atención como los Transformers. Es sumamente importante agregar un grado de razonamiento con memoria a largo/corto plazo para generar recomendaciones que sean, como dice el tema, razonables.

Finalmente, con respecto al tema de la escalabilidad de los sistemas, creo que la situación es bastante decidora y es un patrón que se ha repetido desde hace ya un tiempo. Como mucho de los papers que hemos leído, existe una componente fundamental relacionada a la creación de sistemas robustos desde un punto de vista más de ingeniería de software, capaces de exponer un sistema que vaya más allá del análisis teórico, que sea aplicable y utilizable a escala real.



## Referencias:

- Chawla, R., Sankararaman, A., Ganesh, A., & Shakkottai, S. (2020). The Gossiping Insert-Eliminate Algorithm for Multi-Agent Bandits. *arXiv preprint arXiv:2001.05452*.
- Vial, D., Shakkottai, S., & Srikant, R. (2020). Robust Multi-Agent Multi-Armed Bandits. *arXiv preprint arXiv:2007.03812*.
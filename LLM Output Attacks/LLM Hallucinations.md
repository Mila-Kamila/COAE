# LLM Hallucinations

# **¿Qué son las alucinaciones y cómo se producen?**

Son casos en los que los LLM generan respuestas sin sentido, engañosas, inventadas o fácticamente incorrectas.

tipos de alucinaciones:

- `Alucinación en conflicto con los hechos` ocurre cuando un LLM genera una respuesta que contiene información fácticamente incorrecta. Por ejemplo, el ejemplo anterior de una afirmación fácticamente incorrecta sobre el número de apariciones de una letra particular en una oración dada es una alucinación en conflicto con los hechos.
- `Alucinación en conflicto con la entrada` ocurre cuando un LLM genera una respuesta que contradice la información proporcionada en el prompt de entrada. Por ejemplo, si el prompt de entrada es `My shirt is red. What is the color of my shirt?`, un caso de alucinación en conflicto con la entrada sería una respuesta del LLM como `The color of your shirt is blue`.
- `Alucinación en conflicto con el contexto` ocurre cuando un LLM genera una respuesta que entra en conflicto con información anterior generada por el LLM, es decir, la propia respuesta del LLM contiene inconsistencias. Este tipo de alucinación puede ocurrir en respuestas largas o de múltiples turnos. Por ejemplo, si el prompt de entrada es `My shirt is red. What is the color of my shirt?`, un caso de alucinación en conflicto con el contexto sería una respuesta del LLM como `Your shirt is red. This is a good looking hat`, ya que la respuesta confunde las palabras `shirt` y `hat` dentro de la respuesta generada.

## ¿Cúal es la causa de las allucionaciones?

→ Problema con los datos de entrenamineto 

Estos problemas pueden incluir datos incompletos, lo que da como resultado un LLM que carece de una comprensión exhaustiva de los detalles más finos del lenguaje, y datos de baja calidad que contienen datos ruidosos o sesgados que el LLM recoge durante el entrenamiento.

→ Prompts confusos 

Los prompts de entrada confusos, ambiguos o contradictorios pueden aumentar la probabilidad de alucinaciones del LLM.

## Mitigaciones de las alucinaciones

Las alucinaciones están inherentemente ligadas a los LLM y, por lo tanto, no se pueden prevenir por completo, solo minimizar y mitigar. 

Sin embargo, para reducir la probabilidad de las alucinaciones se puede mediante darle al modelo  datos de entramiento que no sean confusos, que sean confiables y limpios.

Tambien, generarndo entradas al llm por parte del usuario que sean muy claras, con imporfación completa.

También podemos intentar medir el nivel de certeza del LLM y descartar la respuesta si cae por debajo de un nivel de certeza configurado. Existen tres enfoques para medir el nivel de certeza:

- `Basado en logits`: Esto requiere acceso interno al estado del LLM y la evaluación de sus logits para determinar la probabilidad a nivel de token, lo que hace que este enfoque sea típicamente imposible, ya que la mayoría de los LLM modernos son de código cerrado.
- `Basado en verbalización`: Esta estimación le pide al LLM que proporcione puntuaciones de confianza directamente añadiendo al prompt una frase como `Please also provide a confidence score from 0 to 100`. Sin embargo, los LLM no son necesariamente capaces de dar una estimación precisa de su propia confianza, lo que hace que este enfoque sea poco fiable.
- `Basado en consistencia`: Este enfoque intenta medir la certeza pidiéndole al LLM que responda varias veces y observando la consistencia entre todas las respuestas generadas. La idea detrás de este enfoque es que una respuesta de un LLM basada en información fáctica es más probable que se genere de manera consistente que las respuestas alucinadas.

Otra mitigación de las alucinaciones es un enfoque multiagente donde múltiples LLM colaboran y debaten sus respuestas para llegar a un consenso.
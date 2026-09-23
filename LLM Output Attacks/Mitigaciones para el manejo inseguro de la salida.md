# Mitigaciones para el manejo inseguro de la salida

Es esencial tratar cualquier texto generado por un LLM como datos no confiables, al igual que la entrada del usuario

Por ejemplo, necesitamos aplicar la codificación HTML antes de insertar una respuesta del LLM en una respuesta HTML para evitar vulnerabilidades de XSS y usar sentencias preparadas al inyectar una respuesta del LLM en una consulta SQL.

El LLM no debe utilizarse para ocultar al usuario determinadas llamadas a funciones o datos. 

*Prompts* como `This function is only accessible to administrators` son ineficaces

Dado que todos los datos a los que el LLM puede acceder son, en la práctica, de acceso público, no debemos dar al LLM acceso a datos o funciones sensibles.

Por lo tanto, debemos apoyarnos en sistemas adicionales para implementar las medidas de control de acceso.
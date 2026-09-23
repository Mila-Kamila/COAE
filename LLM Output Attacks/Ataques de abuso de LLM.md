# Ataques de abuso de LLM

## **Generación de desinformación con LLM**

Los LLM modernos suelen estar entrenados para mostrar resiliencia contra la desinformación relacionada con información sensible del mundo real. 

Sin embargo, con tencnicas como jailbreaking es posible evadir estas restricciones eticas para que el módelo genere la acción que inialmente no tiene permitido.

## **Evasión de la detección de discurso de odio**

> **Discurso de odio:** Cualquier tipo de comunicación oral, escrita o conductual que ataque o utilice un lenguaje peyorativo o discriminatorio con referencia a una persona o un grupo en función de quiénes son, en otras palabras, en función de su religión, etnia, nacionalidad, raza, color, ascendencia, género u otro factor de identidad
> 

Detectores de discurso de odio populares basados en IA

- [HateXplain](https://github.com/hate-alert/HateXplain)
- [Detoxify](https://github.com/unitaryai/detoxify)

Estos modelos suelen procesar una entrada de texto y asignar una `puntuación de toxicidad` (toxicity score)

Evadir los detectores de discurso

- `Modificaciones a nivel de carácter (Character-level modifications)`: Estos ataques adversariales modifican la entrada de texto puntuando tokens individuales y modificando los tokens más importantes. Un ejemplo de este tipo de ataque adversarial es [DeepWordBug](https://github.com/QData/deepWordBug). Las modificaciones a nivel de carácter pueden incluir las siguientes operaciones:
    - `Swap`: Intercambiar dos caracteres adyacentes, p. ej., `HackTheBox` se convierte en `HackhTeBox`
    - `Substitution`: Sustituir un carácter por otro diferente, p. ej., `HackTheBox` se convierte en `HackTueBox`
    - `Deletion`: Eliminar un carácter, p. ej., `HackTheBox` se convierte en `HackTeBox`
    - `Insertion`: Insertar un carácter, p. ej., `HackTheBox` se convierte en `HackTheBoux`
- `Modificaciones a nivel de palabra (Word-level modifications)`: Estos ataques adversariales modifican la entrada de texto reemplazando palabras por sinónimos. Un ejemplo sería [PWWS](https://github.com/JHL-HUST/PWWS), que reemplaza vorazmente palabras con sinónimos hasta que la clasificación cambia.
- `Modificaciones a nivel de oración (Sentence-level modifications)`: Este ataque adversarial modifica la entrada de texto parafraseándola. Un LLM puede realizar esta modificación encargándole que parafrasee la entrada proporcionada.
# PII Full GRASP and SOLID
## FIT
### Universidad Católica del Uruguay

En este programa trabajaremos con recetas de cocina que involucran ingredientes y equipamiento.

## Desafío(s)

Este ejemplo es el mismo que hemos utilizado hasta ahora, pero el código tiene modificaciones resultantes de aplicar los principio y patrones anteriores.

La clases que implementan IPrinter, como ConsolePrinter, dependen de la clase Recipe: un mensaje string GetTextToPrint() es enviado a una instancia de Recipe en el método void PrintRecipe(Recipe).

➡️ **Apliquen el principio de inversión de dependencia para que la clase ConsolePrinter no dependa de la clase Recipe.**

### Resumen de los Cambios y Cumplimiento del Principio de Inversión de Dependencia (DIP)

1. **Creación de una interfaz `IPrintable`**: 
   Se definió una interfaz `IPrintable` con el método `GetTextToPrint()`, la cual establece un contrato para obtener un texto imprimible desde cualquier clase que la implemente.

2. **Implementación de `IPrintable` en la clase `Recipe`**: 
   Se hizo que la clase `Recipe` implemente esta interfaz, proporcionando la lógica de cómo se genera el texto para imprimir la receta.

3. **Desacoplamiento de `ConsolePrinter`**: 
   La clase `ConsolePrinter` fue modificada para depender de `IPrintable` en lugar de depender directamente de la clase `Recipe`. De esta forma, `ConsolePrinter` ahora puede trabajar con cualquier clase que implemente `IPrintable`.

### Justificación y Cumplimiento del Principio de Inversión de Dependencia (DIP):

- La clase `ConsolePrinter` es un "módulo de alto nivel" que necesita imprimir la información de recetas, pero ya no depende de una clase concreta (`Recipe`). Ahora depende de una abstracción (`IPrintable`), que es una interfaz.
- Cualquier clase que implemente `IPrintable` puede ser utilizada con `ConsolePrinter`, lo que reduce el acoplamiento y aumenta la flexibilidad y extensibilidad del sistema.
- Si se quiere agregar una nueva clase que proporcione un texto imprimible diferente, solo se necesita que esta nueva clase implemente `IPrintable`, sin cambiar el código de `ConsolePrinter`.

Este diseño hace que el sistema sea más **extensible**, **desacoplado** y **mantenible**, ya que los módulos de alto nivel (como `ConsolePrinter`) no están sujetos a los detalles de los módulos de bajo nivel (como `Recipe`).

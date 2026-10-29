# Historias de usuario de búsqueda

| Campo | Valor |
| --- | --- |
| Proyecto | Proyecto Simbiosis |
| Fecha | 29/10/2026 |
| Versión | 0.1 |
| Estado | Borrador |

## Fuentes comunes

- [Acta de UC-21 Buscar recetas](../captura/acta-acuerdos-uc-21-buscar-recetas.md), v1.1, Vigente.
- [Catálogo de requisitos](catalogo-requisitos.md), UR-08 y FR pertinentes.
- [Modelo de casos de uso](../modelos/modelo-casos-de-uso.md), UC-21.

## Épica de búsqueda

Como persona usuaria registrada, quiero localizar recetas indicando una palabra o frase, los ingredientes que deben contener y los que quiero evitar, para encontrar una receta que se ajuste a lo que quiero cocinar.

**Estado:** descompuesta en US-01, US-02 y US-03. Conserva la necesidad conjunta.

## Justificación de la división

Cada historia desarrolla un criterio de búsqueda que la persona puede usar por sí solo y que ya le da un resultado útil; la exclusión, por ejemplo, funciona sin otros criterios. La división no separa pantallas ni campos, y la combinación de criterios se comprueba en los criterios de aceptación porque el acta fija que una receta debe cumplirlos todos.

## US-01

**Título:** Buscar recetas por una palabra o frase

Como persona usuaria registrada, quiero buscar recetas por una palabra o frase, para encontrar las que tratan de lo que tengo en mente.

**Fuentes:** UR-08; UC-21; FR-085; acta, «Criterios de búsqueda» y «Búsqueda sin resultados».

### Criterios de aceptación

- **CA-01.** Dado que existe la receta «Puré de calabaza», cuando busco «PURE», entonces la receta aparece entre los resultados, porque la búsqueda comprueba el título y la descripción breve sin distinguir mayúsculas ni tildes.
- **CA-02.** Dado que existen las recetas «Sopa de calabaza asada» y «Calabaza para sopa», cuando busco la frase «sopa de calabaza», entonces aparece solo la primera, porque la frase debe aparecer seguida y en el mismo orden.
- **CA-03.** Dado que ninguna receta contiene «tortila», cuando busco «tortila», entonces el sistema indica que no hay resultados, conserva el texto buscado y propone la corrección «tortilla» separada de los resultados, sin ejecutar otra búsqueda.

## US-02

**Título:** Buscar recetas por ingredientes incluidos

Como persona usuaria registrada, quiero buscar recetas que contengan todos los ingredientes que selecciono, para cocinar con lo que tengo disponible.

**Fuentes:** UR-08; UC-21; FR-086; acta, «Criterios de búsqueda» y «Resultados y detalle».

### Criterios de aceptación

- **CA-01.** Dado que selecciono los ingredientes «huevo» y «patata», cuando busco, entonces aparecen solo recetas que contienen ambos; una receta con huevo y sin patata no aparece.
- **CA-02.** Dado que existe una receta con «huevo» pendiente de validación, cuando busco «huevo», entonces esa receta no aparece, porque solo se muestran recetas publicadas y validadas.
- **CA-03.** Dado que hay tres recetas publicadas con «huevo» en fechas distintas, cuando busco «huevo», entonces se muestran de la más reciente a la más antigua.

## US-03

**Título:** Excluir ingredientes de la búsqueda

Como persona usuaria registrada, quiero excluir ingredientes de mi búsqueda, para no ver recetas que los contienen.

**Fuentes:** UR-08; UC-21; FR-087; acta, «Criterios de búsqueda».

### Criterios de aceptación

- **CA-01.** Dado que excluyo «nueces» y «cacahuetes» sin indicar otros criterios, cuando busco, entonces no aparece ninguna receta que contenga alguno de los dos, aunque contenga solo uno.
- **CA-02.** Dado que incluyo «pollo» y excluyo «nata», cuando busco, entonces aparecen solo recetas que contienen pollo y no contienen nata.
- **CA-03.** Dado que selecciono «tomate» para incluirlo y para excluirlo, cuando solicito buscar, entonces el sistema señala el conflicto y no ejecuta la búsqueda hasta que lo corrija.

## Revisión INVEST

La revisión abarca US-01, US-02 y US-03. «Aplicado» indica si se ha realizado la comprobación. «Cumple» indica si todas las historias cumplen el criterio. Si alguna no lo cumple, indicar «No» e identificar la historia y el motivo en la justificación. Si no se ha realizado la comprobación o faltan datos, indicar «Pendiente» en «Cumple».

| Criterio | Pregunta de revisión | Aplicado | Cumple | Justificación |
| --- | --- | --- | --- | --- |
| Independiente | ¿Puede implementarse cada historia y ofrecer un resultado útil sin implementar antes las otras historias del conjunto? Puede compartir infraestructura con ellas. | Sí | Sí | Las tres ofrecen un resultado útil con su propio criterio. El CA-02 de US-03 combina inclusión y exclusión, pero solo comparte la búsqueda con US-02 y el acta exige que se cumplan todos los criterios; la exclusión funciona sola en el CA-01. |
| Negociable | ¿Cada historia explica qué necesita la persona y deja margen para discutir los detalles de la solución, respetando los acuerdos confirmados? | Sí | Sí | Las tres describen la necesidad sin fijar pantallas, controles ni tecnología, y respetan los acuerdos del acta. |
| Valiosa | ¿La parte «para…» de cada historia explica el beneficio que obtiene la persona al usar esa capacidad? | Sí | Sí | Cada «para» indica un beneficio: encontrar lo que tiene en mente (US-01), cocinar con lo que tiene (US-02) y no ver recetas con ingredientes no deseados (US-03). |
| Estimable | ¿Están claros el alcance y los datos necesarios para estimar el trabajo de cada historia? | Sí | Sí | El acta concreta dónde se busca el texto, qué recetas son visibles, el orden y las respuestas ante conflicto y falta de resultados. |
| Pequeña | ¿Se centra cada historia en una única capacidad de alcance manejable? | Sí | Sí | Cada historia trata una sola capacidad de búsqueda y tiene tres criterios. |
| Comprobable | ¿Los criterios de aceptación de cada historia describen acciones y resultados observables que permiten distinguir un comportamiento correcto de uno incorrecto? | Sí | Sí | Los nueve criterios usan datos concretos (textos, ingredientes, fechas) y resultados que se pueden comprobar en pantalla. |

## Dudas pendientes

Ninguna.
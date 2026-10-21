---
instrumento: UD02_PR01
tipo: ordinario
unidad: UD02
titulo: "Diseño E/R y modelo relacional: Taller mecánico y gestión de reparaciones"
contenidos:
  - UD02-C01
  - UD02-C02
  - UD02-C03
  - UD02-C04
  - UD02-C06
  - UD02-C07
  - UD02-C08
criterios:
  - RA6.a
  - RA6.b
  - RA6.c
  - RA6.d
  - RA6.e
  - RA6.f
  - RA6.g
  - RA6.h
puntuacion_maxima: 10.0
---

# Práctica evaluable UD02_PR01

## Diseño E/R y modelo relacional: Taller mecánico y gestión de reparaciones

**Unidad didáctica:** UD02. El modelo Entidad/Relación
**Puntuación máxima:** 10 puntos
**Entregable:** un único documento (PDF o Markdown) que contenga, en este orden, los apartados del Ejercicio 1, Ejercicio 2 y Ejercicio 3, con los diagramas y tablas suficientemente legibles (herramienta gráfica libre: draw.io, dbdiagram.io, Mermaid, lápiz y papel escaneado, etc.).

### Contexto

Un taller mecánico desea informatizar la gestión de sus reparaciones. Tras entrevistar al responsable del taller se ha obtenido la siguiente especificación de requerimientos:

> El taller dispone de varios **mecánicos**, de los que interesa conocer su DNI, nombre completo y teléfono. Cada mecánico puede estar especializado en una o varias **categorías de reparación** (por ejemplo, "motor", "electricidad", "chapa"); de cada categoría interesa su código y su descripción. Un mecánico puede estar especializado en varias categorías y una categoría puede tener varios mecánicos especializados en ella.
>
> El taller atiende a **clientes**, de los que se registra el DNI, nombre completo, teléfono y dirección (calle, número, localidad y código postal).
>
> Cada cliente puede llevar al taller uno o varios **vehículos**. De cada vehículo interesa su matrícula, marca, modelo y año de fabricación. Un vehículo pertenece siempre a un único cliente en un momento dado, pero podría cambiar de propietario a lo largo del tiempo (esta situación de cambio de propietario no debe modelarse: basta con reflejar el propietario actual).
>
> Cuando un vehículo entra al taller se abre una **orden de reparación**. De cada orden de reparación interesa un código identificativo, la fecha de entrada, la fecha estimada de salida y un campo de observaciones. Toda orden de reparación corresponde a un único vehículo, y un vehículo puede tener a lo largo del tiempo varias órdenes de reparación asociadas.
>
> En cada orden de reparación puede intervenir uno o varios mecánicos, y un mismo mecánico puede intervenir en varias órdenes de reparación a lo largo del tiempo. De cada intervención concreta de un mecánico en una orden de reparación interesa registrar las **horas dedicadas** por ese mecánico a esa orden en concreto (un mismo mecánico no puede intervenir dos veces de forma independiente en la misma orden; sus horas dedicadas se acumulan en un único registro de intervención).
>
> Cada orden de reparación incluye una o varias **piezas de recambio** utilizadas, y una misma pieza de recambio (identificada por su referencia, con su descripción y precio unitario) puede usarse en distintas órdenes de reparación. De cada uso de una pieza en una orden interesa registrar la cantidad utilizada.
>
> Las **furgonetas** son un tipo particular de vehículo que, además de los datos comunes a todo vehículo, tienen un dato adicional: la carga máxima admitida (en kg). No todos los vehículos del taller son furgonetas; los que no lo son se consideran turismos y no tienen ningún dato adicional distinto de los comunes a todo vehículo.
>
> El responsable del taller indica además una condición que no depende únicamente de las tablas ni de las claves: **una orden de reparación no puede cerrarse (marcarse como finalizada) si tiene alguna pieza de recambio registrada con cantidad utilizada igual a cero**, ya que eso indicaría un registro incompleto. Esta condición debe quedar documentada, aunque el taller es consciente de que no puede representarse directamente mediante el diseño lógico de tablas y claves.

### Ejercicio 1. Diagrama Entidad/Relación (3 puntos)

A partir de la especificación anterior, elabora el **diagrama E/R** (modelo básico o extendido, según corresponda) que represente completamente el problema. Debes:

a) Identificar y representar todas las entidades del problema, incluyendo si alguna de ellas es una entidad débil (indicando su tipo de dependencia: en existencia o en identificación). *(0,75 puntos)*
b) Representar todos los atributos de cada entidad, señalando la clave (o claves) de cada una. *(0,75 puntos)*
c) Representar todas las relaciones necesarias, indicando su grado, su cardinalidad (1:1, 1:N o M:N) y la cardinalidad de participación `(mín,máx)` de cada entidad en cada relación. *(0,75 puntos)*
d) Representar la jerarquía de generalización/especialización entre `VEHICULO` y sus posibles subtipos, indicando explícitamente si es total o parcial y si es exclusiva o con solapamiento, justificando tu respuesta en una frase. *(0,75 puntos)*

### Ejercicio 2. Paso al modelo relacional (4 puntos)

A partir del diagrama E/R del Ejercicio 1:

a) Indica, si es necesario, qué transformaciones previas aplicarías al esquema conceptual (Esquema Conceptual Modificado) antes de pasar a tablas, explicando el motivo de cada una. *(0,5 puntos)*
b) Obtén el conjunto completo de tablas del modelo relacional resultante, indicando para cada tabla sus atributos, subrayando la clave primaria y señalando explícitamente las claves foráneas y a qué tabla referencian. *(2 puntos)*
c) Indica el tipo de dato adecuado para al menos los siguientes atributos, justificando brevemente la elección: `matricula`, `fecha_entrada`, `precio_unitario`, `carga_maxima`, `horas_dedicadas`. *(0,75 puntos)*
d) Indica cómo resolverías en tablas la jerarquía `VEHICULO`/`FURGONETA` del apartado 1.d, mostrando la estructura de tablas resultante. *(0,75 puntos)*

### Ejercicio 3. Restricciones semánticas y normalización (3 puntos)

a) Para el modelo de tablas obtenido en el Ejercicio 2, identifica y describe al menos tres restricciones semánticas del modelo relacional (integridad de entidad, integridad referencial, restricción de dominio) aplicadas a atributos o claves concretas de tu esquema. *(1 punto)*
b) Explica cómo documentarías la restricción de negocio indicada al final del contexto (no cerrar una orden con piezas de cantidad cero), justificando por qué no puede expresarse únicamente mediante tablas y claves. *(0,5 puntos)*
c) Comprueba si las tablas obtenidas en el Ejercicio 2 están en 1FN, 2FN y 3FN. Si detectas alguna tabla que no cumpla alguna forma normal, indica la dependencia problemática (parcial o transitiva) y aplica la descomposición necesaria, mostrando el resultado final normalizado. *(1,5 puntos)*

### Condiciones de entrega

- El diagrama E/R puede entregarse dibujado a mano (fotografiado o escaneado con calidad legible) o mediante cualquier herramienta gráfica.
- Las tablas del modelo relacional deben expresarse con la notación `TABLA(atributo1, atributo2, ...)`, subrayando la clave primaria y señalando las claves foráneas.
- No se exige la creación de sentencias SQL: esta práctica evalúa exclusivamente el diseño conceptual y lógico.
- Debes justificar tus decisiones de diseño cuando el enunciado lo pida expresamente; no es necesario justificar lo que no se solicita.

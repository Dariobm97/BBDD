---
unidad: UD02
id: UD02-ACT-06
tipo: análisis de situaciones
contenidos:
  - UD02-C05
criterios:
  - RA6.a
  - RA6.d
ra:
  - RA6
objetivo: Reconocer y aplicar las extensiones del modelo E/R Extendido (restricciones sobre relaciones, generalización/especialización, agregación) sobre situaciones concretas.
dificultad: avanzada
---

# UD02 · Actividad 06 — El modelo E/R ampliado

## Objetivo

Identificar qué mecanismo del modelo E/R Extendido corresponde a cada situación descrita y justificar la clasificación de las jerarquías según cobertura y solapamiento.

## Tareas

1. Una empresa de mensajería tiene repartidores. Un repartidor puede *conducir* una furgoneta o *conducir* una moto, pero nunca ambas cosas en el mismo turno. ¿Qué tipo de restricción sobre relaciones describe mejor esta situación (exclusividad, exclusión, inclusividad o inclusión)? Justifica tu respuesta.

2. En un club deportivo, un socio primero debe *inscribirse* en la actividad de natación antes de poder *acceder* a las clases avanzadas de natación, y ese acceso debe realizarse necesariamente sobre la misma inscripción concreta con la que se registró. ¿Qué restricción sobre relaciones se describe? Justifica tu respuesta distinguiendo esta situación de la inclusividad simple.

3. Se dispone de las entidades `PERRO` (atributos: `chip`, `raza`, `fecha_nacimiento`, `tamaño_pelaje`) y `GATO` (atributos: `chip`, `raza`, `fecha_nacimiento`, `esterilizado`). Ambas comparten atributos comunes.
   a) Propón una superclase adecuada y los atributos que quedarían en ella.
   b) Indica qué atributos permanecen como propios de cada subclase.
   c) Un mismo animal registrado en la base de datos no puede ser simultáneamente `PERRO` y `GATO`, pero podría no estar clasificado en ninguna de las dos subclases si aún no se ha determinado su especie exacta. Clasifica esta jerarquía según cobertura (total/parcial) y solapamiento (exclusiva/con solapamiento), justificando ambos ejes.

4. Una agencia de viajes gestiona `RESERVA` que asocia a un `CLIENTE` con un `VUELO`. Cuando una reserva se confirma, puede generar una `FACTURA`, que se relaciona con la reserva completa (no con el cliente ni con el vuelo por separado). Explica por qué esta situación requiere una **agregación** y no puede resolverse conectando directamente `FACTURA` con `CLIENTE` o con `VUELO`.

5. Se quiere representar el conjunto de jugadores que forman un mismo equipo de baloncesto (todos ellos con el mismo rol de "jugador del equipo"). Si alguien propusiera modelar esto como una agregación de tipo compuesto/componente, ¿sería correcto? Justifica tu respuesta indicando el tipo de agregación adecuado.

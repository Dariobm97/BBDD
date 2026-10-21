---
unidad: UD02
id: UD02-ACT-04
tipo: ejercicios progresivos
contenidos:
  - UD02-C03
criterios:
  - RA6.d
ra:
  - RA6
objetivo: Determinar el grado de una relación y calcular las cardinalidades de relación y de participación de las entidades implicadas.
dificultad: intermedia
---

# UD02 · Actividad 04 — Cardinalidades de relaciones

## Objetivo

Practicar el cálculo del grado, la cardinalidad de relación (1:1, 1:N, N:1, M:N) y la cardinalidad de participación `(mín,máx)` de cada entidad, con dificultad creciente.

## Tareas

**Tarea 1 (grado).** Indica el grado de cada una de las siguientes relaciones y su nombre correspondiente (unaria, binaria, ternaria):

a) `PROFESOR` *imparte* `ASIGNATURA`.
b) `EMPLEADO` *supervisa* a otro `EMPLEADO`.
c) `ALUMNO`, `ASIGNATURA` y `AULA` participan simultáneamente en la relación *examina*.

**Tarea 2 (cardinalidad de relación).** Para cada caso siguiente, indica si la relación es 1:1, 1:N, N:1 o M:N:

a) Un país tiene una única capital, y una ciudad es capital de un único país.
b) Un autor puede escribir varios libros; un libro, en la política de esta biblioteca, es escrito por un único autor.
c) Un estudiante puede matricularse en varias actividades extraescolares, y una actividad extraescolar puede tener matriculados varios estudiantes.

**Tarea 3 (cardinalidad de participación).** Dada la relación `EQUIPO` *ficha* `JUGADOR`, donde: un jugador puede estar sin equipo o fichado por un único equipo, y un equipo tiene entre 1 y 25 jugadores fichados:

a) Indica la cardinalidad de participación de `JUGADOR` (colocada junto a `EQUIPO`).
b) Indica la cardinalidad de participación de `EQUIPO` (colocada junto a `JUGADOR`).
c) Explica, con tus propias palabras, la regla que determina junto a qué entidad se coloca cada pareja `(mínimo, máximo)`.

**Tarea 4 (caso combinado).** Un hospital gestiona citas médicas: cada `PACIENTE` puede solicitar varias citas a lo largo del tiempo (o ninguna si es nuevo); cada `CITA` está asociada exactamente a un único paciente. Determina la cardinalidad de la relación `PACIENTE`-`CITA` y las cardinalidades de participación de ambas entidades.

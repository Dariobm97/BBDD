---
unidad: UD02
id: UD02-ACT-05
tipo: análisis de casos
contenidos:
  - UD02-C04
criterios:
  - RA6.d
  - RA6.e
  - RA6.f
ra:
  - RA6
objetivo: Distinguir entidades fuertes de débiles y diferenciar dependencia en existencia de dependencia en identificación.
dificultad: intermedia
---

# UD02 · Actividad 05 — Entidades débiles y tipos de dependencia

## Objetivo

Analizar distintos casos para decidir si una entidad es fuerte o débil, y en caso de ser débil, determinar si su dependencia respecto de la entidad fuerte es en existencia o en identificación.

## Tareas

Para cada uno de los siguientes casos, indica: (a) si la entidad subrayada es fuerte o débil; (b) en caso de ser débil, si la dependencia es en existencia o en identificación; (c) justifica tu respuesta.

1. En un hotel, la entidad `HABITACION` se identifica mediante un número de habitación que se repite en distintas plantas del hotel (por ejemplo, la habitación 101 existe en la planta 1 y en la planta 2). La entidad `HOTEL` (con un único hotel para esta base de datos, sin necesidad de considerar varios edificios) organiza las habitaciones por planta.
2. En una empresa, la entidad `FACTURA` tiene un número de factura único a nivel de toda la empresa, que no se repite nunca, independientemente del cliente al que pertenezca.
3. En una biblioteca, la entidad `EJEMPLAR` (un ejemplar físico concreto de un libro) se numera correlativamente **dentro de cada libro** (por ejemplo, el libro X tiene los ejemplares 1, 2 y 3, y el libro Y también puede tener ejemplares numerados 1, 2 y 3).
4. En una base de datos hospitalaria, la entidad `TRATAMIENTO` recogida para un paciente solo tiene sentido si existe el paciente al que se aplica (si el paciente se da de baja del sistema, sus tratamientos también desaparecen), pero cada tratamiento tiene un código propio (por ejemplo, un identificador de protocolo clínico) que lo identifica sin necesidad de conocer el paciente.
5. Un compañero afirma: "Toda entidad que dependa en existencia de otra, depende también en identificación de ella". Valora si esta afirmación es correcta, utilizando el caso 4 como contraejemplo o confirmación.

---
unidad: UD02
id: UD02-ACT-07
tipo: diseño / caso práctico integrador
contenidos:
  - UD02-C01
  - UD02-C02
  - UD02-C03
  - UD02-C05
criterios:
  - RA6.a
  - RA6.b
  - RA6.c
  - RA6.d
ra:
  - RA6
objetivo: Elaborar un diagrama Entidad/Relación completo a partir de una especificación de requerimientos, aplicando entidades, atributos, relaciones, cardinalidades y, si procede, extensiones del modelo E/R Extendido.
dificultad: avanzada
---

# UD02 · Actividad 07 — Diseño de un diagrama E/R completo

## Objetivo

Aplicar de forma integrada el procedimiento de elaboración de diagramas E/R: identificación de entidades, atributos, relaciones, cardinalidades y, si el problema lo requiere, jerarquías de generalización/especialización.

## Contexto

Especificación de requerimientos de una academia de idiomas:

> "La academia organiza cursos. De cada curso interesa el código, el nombre del idioma y el nivel (A1, A2, B1...). Cada curso es impartido por un único profesor, y un profesor puede impartir varios cursos a lo largo del año. De cada profesor se conocen su DNI, nombre y los idiomas que domina (un profesor puede dominar varios idiomas). Los alumnos se matriculan en los cursos: un alumno puede matricularse en varios cursos, y un curso puede tener matriculados varios alumnos. De cada matrícula interesa registrar la fecha de matriculación y si el pago se ha completado o no. De cada alumno se conoce el DNI, el nombre y el teléfono. Existen dos tipos de profesores: los profesores nativos, de los que se registra su país de origen, y los profesores no nativos, de los que se registra su titulación académica. Todo profesor de la academia es necesariamente de uno de estos dos tipos, sin poder pertenecer a ambos a la vez."

## Tareas

1. Identifica las entidades del problema y, para cada una, sus atributos, señalando cuáles forman la clave primaria.
2. Identifica las relaciones del problema, indicando para cada una su grado y su cardinalidad (1:1, 1:N, N:1 o M:N).
3. Determina las cardinalidades de participación `(mín,máx)` de las entidades en la relación de matriculación.
4. El idioma que domina un profesor, ¿es un atributo monovaluado o multivaluado de `PROFESOR`? Justifica tu respuesta con el texto.
5. Analiza la jerarquía de profesores (nativos/no nativos): identifica la superclase, las subclases, los atributos que corresponden a cada nivel, y clasifícala según cobertura y solapamiento.
6. Redacta, en lenguaje descriptivo o mediante notación textual (no es obligatorio un diagrama gráfico), el esquema completo del diagrama E/R resultante: entidades con sus atributos y clave, relaciones con su cardinalidad y cardinalidad de participación, y la jerarquía identificada.

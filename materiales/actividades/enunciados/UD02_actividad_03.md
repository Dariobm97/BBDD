---
unidad: UD02
id: UD02-ACT-03
tipo: ejercicio de clasificación
contenidos:
  - UD02-C02
criterios:
  - RA6.b
  - RA6.c
ra:
  - RA6
objetivo: Clasificar atributos según sus tipos (obligatorio/opcional, atómico/compuesto, monovaluado/multivaluado, derivado/almacenado) y distinguir superclave, clave candidata y clave primaria.
dificultad: intermedia
---

# UD02 · Actividad 03 — Clasificación de atributos y claves

## Objetivo

Aplicar correctamente las clasificaciones de atributos y los conceptos de superclave, clave candidata y clave primaria sobre un conjunto de datos concreto.

## Contexto

Se dispone de la entidad `EMPLEADO` con los siguientes atributos: `dni`, `numero_seguridad_social`, `nombre`, `apellido_1`, `apellido_2`, `direccion` (compuesta por `calle`, `numero`, `localidad`), `fecha_nacimiento`, `edad`, `telefonos_contacto` (un empleado puede tener de 0 a varios teléfonos).

## Tareas

1. Clasifica cada uno de los siguientes atributos como **atómico o compuesto**: `dni`, `direccion`, `nombre`.
2. Clasifica `telefonos_contacto` como **monovaluado o multivaluado** e indica su cardinalidad en formato `(mínimo, máximo)`.
3. Indica si `edad` es un atributo **derivado o almacenado**, justificando tu respuesta a partir de otro atributo de la entidad.
4. De los atributos `dni`, `numero_seguridad_social` y el conjunto `{nombre, apellido_1, apellido_2}`, indica cuáles son **claves candidatas** válidas y cuál **no lo es**, justificando la respuesta.
5. Si el diseñador elige `dni` como clave primaria, ¿qué nombre recibe `numero_seguridad_social`? Justifica tu respuesta según la definición estudiada.
6. Explica la diferencia entre **superclave** y **clave candidata** utilizando como ejemplo el conjunto `{dni, nombre}` sobre la entidad `EMPLEADO`.

---
unidad: UD02
id: UD02-ACT-09
tipo: corrección de errores
contenidos:
  - UD02-C07
criterios:
  - RA6.h
ra:
  - RA6
objetivo: Identificar y clasificar violaciones de las restricciones semánticas del modelo relacional (dominio, clave, integridad referencial, restricciones de usuario) en un conjunto de datos de ejemplo.
dificultad: intermedia
---

# UD02 · Actividad 09 — Restricciones semánticas del modelo relacional

## Objetivo

Detectar, en un conjunto de datos de ejemplo, qué filas incumplen alguna restricción semántica del modelo relacional y clasificar el tipo de restricción incumplida.

## Contexto

Se dispone de las siguientes tablas de una gestoría:

```
CLIENTE (dni [PK], nombre, edad)
FACTURA (num_factura [PK], fecha, importe, dni_cliente [FK -> CLIENTE.dni])
```

Y los siguientes datos:

**CLIENTE**

| dni | nombre | edad |
|---|---|---|
| 11111111A | Ana Pérez | 34 |
| 22222222B | Luis Gómez | -5 |
| 11111111A | Ana P. (duplicado) | 40 |

**FACTURA**

| num_factura | fecha | importe | dni_cliente |
|---|---|---|---|
| F001 | 2024-01-10 | 150.00 | 11111111A |
| F002 | 2024-02-15 | -30.00 | 22222222B |
| F003 | 2024-03-01 | 200.00 | 99999999Z |
| F004 | 2024-03-05 | 90.00 | (nulo) |

## Tareas

1. Analiza la tabla `CLIENTE` y detecta qué filas incumplen la **restricción de clave (integridad de entidad)**. Justifica tu respuesta.
2. Analiza la fila del cliente con `edad = -5`. ¿Qué tipo de restricción semántica se incumple? Justifica tu respuesta, asumiendo que el dominio del atributo `edad` es el conjunto de enteros no negativos razonables para una persona.
3. Analiza la fila `F002` de `FACTURA`, con `importe = -30.00`. ¿Qué tipo de restricción se incumple, asumiendo que el dominio de `importe` no admite valores negativos?
4. Analiza la fila `F003`, cuyo `dni_cliente` es `99999999Z`. ¿Qué restricción se incumple? Justifica tu respuesta comprobando la tabla `CLIENTE`.
5. Analiza la fila `F004`, con `dni_cliente` nulo. ¿Incumple esta fila la integridad referencial? Justifica tu respuesta según la definición estudiada.
6. Supón que la gestoría añade la regla de negocio "ninguna factura puede superar los 10.000 €". ¿Es esta una restricción que pueda expresarse mediante las tablas, claves y relaciones del diseño lógico, o corresponde a otro tipo de restricción? Justifica tu respuesta.

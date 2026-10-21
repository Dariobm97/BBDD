---
unidad: UD02
id: UD02-ACT-10
tipo: ejercicio progresivo
contenidos:
  - UD02-C08
criterios:
  - RA6.g
ra:
  - RA6
objetivo: Aplicar el proceso de normalización (1FN, 2FN, 3FN, FNBC) analizando dependencias funcionales, completas y transitivas sobre una tabla no normalizada.
dificultad: avanzada
tiempo_estimado: 30 minutos
---

# UD02 · Actividad 10 — Normalización hasta FNBC

## Objetivo

Practicar el proceso completo de normalización, identificando en cada paso qué dependencia funcional provoca el incumplimiento de la forma normal correspondiente.

## Contexto

Se dispone de la siguiente tabla de matrículas de una academia, con clave primaria `{cod_alumno, cod_curso}`:

```
MATRICULA (cod_alumno, nombre_alumno, cod_curso, nombre_curso, cod_profesor, nombre_profesor, fecha_matricula, nota_final)
```

Dependencias funcionales conocidas:

- `cod_alumno → nombre_alumno`
- `cod_curso → nombre_curso`
- `cod_curso → cod_profesor`
- `cod_profesor → nombre_profesor`
- `{cod_alumno, cod_curso} → fecha_matricula`
- `{cod_alumno, cod_curso} → nota_final`

## Tareas

1. Comprueba si `MATRICULA` está en **1FN**. Justifica tu respuesta.
2. Comprueba si `MATRICULA` está en **2FN**. Identifica qué atributo(s) no dependen funcionalmente completa de la clave compuesta y por qué. Si no está en 2FN, descompón la tabla en las tablas necesarias.
3. Sobre las tablas resultantes de la tarea 2, comprueba si cada una está en **3FN**. Identifica cualquier dependencia transitiva existente y, si la hay, descompón de nuevo.
4. Sobre el resultado final, comprueba si todas las tablas están en **FNBC**, verificando que todo determinante de cada tabla es clave candidata.
5. Presenta el esquema final completo de tablas normalizadas, indicando la clave primaria de cada una.

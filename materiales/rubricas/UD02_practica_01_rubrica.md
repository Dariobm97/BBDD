---
instrumento: UD02_PR01
tipo: ordinario
titulo: "Diseño E/R y modelo relacional: Taller mecánico y gestión de reparaciones"
unidad: UD02
contenidos:
  - UD02-C01
  - UD02-C02
  - UD02-C03
  - UD02-C04
  - UD02-C06
  - UD02-C07
  - UD02-C08
criterios_evaluacion:
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

# Rúbrica analítica — UD02_PR01

**Instrumento:** UD02_PR01 — Diseño E/R y modelo relacional: Taller mecánico y gestión de reparaciones
**Tipo:** ordinario
**Unidad:** UD02
**Puntuación máxima:** 10 puntos
**Fuente de cálculo:** `materiales/rubricas/UD02_practica_01_rubrica.yml` (este Markdown es la versión legible; el YAML es la fuente que consume `scripts/corregir.py`).

## 1. Tabla analítica de criterios

| ID | Ejercicio | Apartado | Aspecto evaluado | Evidencia o condición de cumplimiento | Peso | Nivel | Puntuación obtenida | Observaciones |
|---|---|---|---|---|---:|---|---:|---|
| E1-a | Ejercicio 1 | Apartado a | Identificación de entidades y de su posible debilidad | Se identifican `MECANICO`, `CATEGORIA`, `CLIENTE`, `VEHICULO`, `ORDEN_REPARACION` y `PIEZA`; se indica correctamente que no hay entidades débiles (o se justifica coherentemente una alternativa con `ORDEN_REPARACION` como débil) | 0.75 | | | |
| E1-b | Ejercicio 1 | Apartado b | Atributos y clave primaria de cada entidad | Cada entidad incluye todos sus atributos del enunciado (incluyendo la descomposición de `direccion` en `CLIENTE`) y se señala explícitamente la clave primaria de cada una | 0.75 | | | |
| E1-c | Ejercicio 1 | Apartado c | Relaciones, grado, cardinalidad y cardinalidad de participación | Se representan `ESPECIALIZADO` (M:N), `POSEE` (1:N), `ABRE` (1:N), `INTERVIENE` (M:N con atributo) y `USA` (M:N con atributo), todas binarias, con cardinalidad de participación `(mín,máx)` coherente con el enunciado | 0.75 | | | |
| E1-d | Ejercicio 1 | Apartado d | Jerarquía de generalización/especialización VEHICULO/TURISMO/FURGONETA | Se representa la jerarquía `ES_UN` con superclase `VEHICULO` y subclases `TURISMO`/`FURGONETA`, declarando y justificando que es total y exclusiva | 0.75 | | | |
| E2-a | Ejercicio 2 | Apartado a | Transformaciones previas del esquema conceptual (ECM) | Se identifican como mínimo las transformaciones de las tres relaciones M:N (`ESPECIALIZADO`, `INTERVIENE`, `USA`) en entidades intermedias, con justificación | 0.5 | | | |
| E2-b1 | Ejercicio 2 | Apartado b | Tablas y atributos del modelo relacional | Todas las tablas resultantes (10 tablas de la solución, o equivalentes coherentes con el diagrama propio del alumnado) contienen los atributos correctos derivados del Ejercicio 1 | 1.0 | | | |
| E2-b2 | Ejercicio 2 | Apartado b | Claves primarias y claves foráneas correctamente identificadas | Cada tabla señala su clave primaria (simple o compuesta) y cada clave foránea indica explícitamente la tabla referenciada | 1.0 | | | |
| E2-c | Ejercicio 2 | Apartado c | Selección justificada de tipos de datos | Se indica un tipo de dato adecuado y justificado para `matricula`, `fecha_entrada`, `precio_unitario`, `carga_maxima` y `horas_dedicadas` | 0.75 | | | |
| E2-d | Ejercicio 2 | Apartado d | Resolución de la jerarquía en el modelo de tablas | Se muestra la estructura de tablas resultante de la jerarquía (tablas separadas 1:1 o tabla única con discriminante), consistente con la decisión tomada en el Ejercicio 1.d | 0.75 | | | |
| E3-a | Ejercicio 3 | Apartado a | Restricciones semánticas del modelo relacional | Se identifican y describen correctamente al menos tres restricciones (integridad de entidad, integridad referencial, restricción de dominio) aplicadas a atributos/claves concretos del propio esquema | 1.0 | | | |
| E3-b | Ejercicio 3 | Apartado b | Documentación de la restricción de negocio no representable en el diseño lógico | Se explica por qué la restricción de "no cerrar orden con pieza de cantidad 0" no es expresable mediante tablas/claves y se propone un mecanismo de aplicación (disparador o validación de aplicación) | 0.5 | | | |
| E3-c | Ejercicio 3 | Apartado c | Comprobación y aplicación de las formas normales (1FN, 2FN, 3FN) | Se comprueban 1FN y 2FN en todas las tablas y se detecta y corrige correctamente la dependencia transitiva `cod_postal → localidad` en `CLIENTE`, aportando el esquema final descompuesto | 1.5 | | | |

**Suma de pesos:** 0.75+0.75+0.75+0.75+0.5+1.0+1.0+0.75+0.75+1.0+0.5+1.5 = **10.0** (coincide con `puntuacion_maxima`).

## 2. Escala de niveles de consecución

La escala oficial de 8 niveles y sus factores porcentuales se define en `curriculum/ponderaciones.yml` (`escala_niveles`) y no se reproduce numéricamente aquí salvo para referencia de lectura: Excelente, Sobresaliente, Notable, Bien, Aprobado, Insuficiente, Muy insuficiente, Sin respuesta.

### Descriptores operativos por criterio (referencia general aplicable a todos los criterios de esta práctica)

- **Excelente:** el aspecto evaluado se cumple íntegramente, sin errores técnicos ni omisiones, incluyendo las alternativas técnicamente válidas descritas en la solución.
- **Sobresaliente:** se cumple casi en su totalidad; existe una imprecisión menor (por ejemplo, una cardinalidad de participación discutible pero razonada, o un tipo de dato aceptable aunque no óptimo) que no compromete la validez del diseño.
- **Notable:** se cumple lo esencial, pero aparece un error conceptual o de notación localizado (por ejemplo, una relación mal etiquetada, una clave foránea no señalada explícitamente en una única tabla).
- **Bien:** cumple una parte significativa del aspecto evaluado, pero con deficiencias apreciables (por ejemplo, dos o tres tablas con atributos incompletos, o cardinalidades incoherentes con el enunciado en varios puntos).
- **Aprobado:** cumplimiento mínimo: se reconoce el concepto pedido (por ejemplo, se detecta que existen relaciones M:N) pero su resolución técnica es deficiente en la mayoría de los casos.
- **Insuficiente:** el aspecto evaluado está presente de forma muy limitada y no alcanza las condiciones mínimas (por ejemplo, faltan la mayoría de las claves foráneas, o no se distingue ninguna forma normal).
- **Muy insuficiente:** aparece un intento reconocible pero esencialmente incorrecto (por ejemplo, se confunde una entidad con un atributo, o se aplica una forma normal de manera errónea en todas las tablas).
- **Sin respuesta:** el apartado correspondiente no se ha entregado o está en blanco.

**Criterios con posible evaluación binaria:** ninguno de los criterios de esta rúbrica se define como estrictamente binario; todos admiten graduación porque implican varios elementos evaluables simultáneamente (varias entidades, varias tablas, varias restricciones).

**Alternativas válidas contempladas:** cardinalidad de `VEHICULO` en `POSEE` ((0,n) o (1,n)); resolución de la jerarquía como tablas separadas 1:1 o como tabla única con discriminante; modelado de `ORDEN_REPARACION` como entidad fuerte o, alternativamente, como entidad débil de `VEHICULO` si se justifica y se mantiene coherentemente en todo el ejercicio.

## 3. Fórmula de cálculo

$$\text{Puntos criterio} = \text{Peso} \times \frac{\text{Factor del nivel}}{100}$$

$$\text{Nota instrumento (0-10)} = \sum \text{Puntos criterio}$$

El cálculo lo ejecuta `scripts/corregir.py` a partir del juicio de corrección; no se redondea en pasos intermedios, únicamente en la nota final presentada en el informe.

## 4. Validación automática

Ejecutar antes de publicar:

```
python scripts/validar_rubrica.py materiales/rubricas/UD02_practica_01_rubrica.yml
```

Resultado de la validación: **ver informe final de generación** (sección de validaciones del agente). No se da por publicada la rúbrica sin una ejecución exitosa de este script.

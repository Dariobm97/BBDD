---
unidad: UD02
id: UD02-ACT-08
tipo: ejercicio progresivo
contenidos:
  - UD02-C06
criterios:
  - RA6.b
  - RA6.c
  - RA6.d
  - RA6.e
  - RA6.f
ra:
  - RA6
objetivo: Aplicar el procedimiento de simplificación (Esquema Conceptual Modificado) y las reglas de paso a tablas sobre distintos tipos de relaciones (1:N, M:N, entidad débil, relación ternaria).
dificultad: avanzada
tiempo_estimado: 40 minutos
---

# UD02 · Actividad 08 — Del diagrama E/R al modelo relacional

## Objetivo

Practicar el paso a tablas, resolviendo progresivamente casos de complejidad creciente: relación 1:N, relación M:N, entidad débil y relación ternaria.

## Tarea 1 — Relación 1:N (nivel básico)

Sea la relación `PERTENECE` de cardinalidad 1:N entre `DEPARTAMENTO` (atributos: `cod_departamento`, `nombre_departamento`, `presupuesto`) y `EMPLEADO` (atributos: `dni`, `nombre`, `salario`), donde un departamento tiene varios empleados y un empleado pertenece a un único departamento.

Aplica la regla de paso a tablas propagando la clave desde el lado "1" hacia el lado "N", indicando expresamente cuál es la clave primaria de cada tabla y cuál es la clave foránea.

## Tarea 2 — Relación M:N (nivel intermedio)

Sea la relación `PARTICIPA` de cardinalidad M:N entre `JUGADOR` (`dni_jugador`, `nombre`) y `TORNEO` (`cod_torneo`, `nombre_torneo`), con el atributo propio de la relación `puesto_obtenido`.

a) Indica por qué esta relación no puede resolverse mediante propagación simple de clave, a diferencia de una relación 1:N.
b) Aplica la transformación M:N → 1:N (creación de entidad intermedia) y obtén las tablas resultantes, incluyendo la clave primaria de la tabla intermedia y el atributo `puesto_obtenido`.

## Tarea 3 — Entidad débil (nivel intermedio-avanzado)

Sea la entidad débil `HABITACION` (atributo propio: `numero_habitacion`, `tipo`) con dependencia en identificación respecto de la entidad fuerte `HOTEL` (`cod_hotel`, `nombre_hotel`, `ciudad`).

a) Aplica la regla de conversión de entidad débil a tabla: indica qué atributos se añaden a `HABITACION` procedentes de `HOTEL` y cuál es la clave primaria resultante de la tabla `HABITACION`.
b) Explica por qué, al tratarse de dependencia en identificación (y no solo en existencia), el atributo importado de `HOTEL` forma parte de la clave primaria de `HABITACION` y no es únicamente una clave foránea sin más.

## Tarea 4 — Relación ternaria (nivel avanzado)

Sea la relación ternaria `entrega` entre las entidades `PROVEEDOR`, `PRODUCTO` y `ALMACEN`, con el atributo propio `cantidad`. Se sabe que:

- Fijados un `producto` y un `almacen`, varios `proveedores` distintos pueden haber realizado entregas.
- Fijados un `proveedor` y un `almacen`, puede haberse entregado varios `productos` distintos.
- Fijados un `proveedor` y un `producto`, la entrega solo puede haberse realizado en un único `almacen`.

a) Determina la conectividad de la relación ternaria (etiquetando cada entidad con "uno" o "muchos" según corresponda).
b) Según la tabla de conectividades del apartado de relaciones ternarias, determina la clave primaria de la tabla resultante `ENTREGA` y su conjunto completo de atributos.

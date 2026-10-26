---
marp: true
theme: default
paginate: true
size: 16:9
lang: es
title: "UD1 - Modelos de bases de datos y arquitectura cliente-servidor"
header: "Bases de Datos · 1º DAW"
footer: "UD1 · Modelos y arquitectura cliente-servidor"
style: |
  :root {
    --azul: #1f3a5f;
    --azul-claro: #e8eef5;
    --gris: #4a4a4a;
    --acento: #b5523b;
    --nota-fondo: #fbf3e4;
    --nota-borde: #c8902e;
  }
  section {
    font-family: "Segoe UI", "Helvetica Neue", Arial, sans-serif;
    font-size: 24px;
    color: var(--gris);
    background: #ffffff;
    padding: 60px 70px 50px 70px;
    border-top: 10px solid var(--azul);
  }
  h1 {
    color: var(--azul);
    font-size: 40px;
    border-bottom: 2px solid var(--azul);
    padding-bottom: 8px;
    margin-bottom: 20px;
  }
  h2 {
    color: var(--azul);
    font-size: 32px;
    border-bottom: 1px solid #c9d3df;
    padding-bottom: 6px;
  }
  h3 {
    color: var(--acento);
    font-size: 26px;
    margin-bottom: 6px;
  }
  strong { color: var(--azul); }
  blockquote {
    background: var(--azul-claro);
    border-left: 6px solid var(--azul);
    color: var(--gris);
    padding: 12px 20px;
    margin: 14px 0;
    font-style: normal;
  }
  table {
    border-collapse: collapse;
    font-size: 20px;
    margin: 0 auto;
  }
  th {
    background: var(--azul);
    color: #ffffff;
    padding: 6px 12px;
  }
  td {
    padding: 6px 12px;
    border-bottom: 1px solid #d9dee5;
  }
  tr:nth-child(even) td { background: #f5f7fa; }
  code { background: #f0f2f5; color: var(--azul); }
  pre { background: #f5f7fa; border: 1px solid #d9dee5; font-size: 18px; }
  header, footer { color: #8a95a5; font-size: 14px; }
  section::after { color: #8a95a5; font-size: 14px; }
  .columnas { display: grid; grid-template-columns: 1fr 1fr; gap: 36px; }
  .tres { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 24px; }
  .pequeno { font-size: 20px; }
  .pequeno table { font-size: 18px; }

  /* Nota didáctica (comentario visible para el alumnado) */
  .nota {
    background: var(--nota-fondo);
    border-left: 6px solid var(--nota-borde);
    padding: 10px 18px;
    margin-top: 14px;
    font-size: 19px;
  }
  .nota strong { color: #8a5a10; }

  /* Portada y separadores de sección */
  section.portada, section.seccion {
    background: var(--azul);
    color: #ffffff;
    border-top: none;
    justify-content: center;
  }
  section.portada h1, section.seccion h1 {
    color: #ffffff;
    border-bottom: 2px solid #ffffff;
  }
  section.portada h2, section.portada p,
  section.seccion h2, section.seccion p {
    color: #dbe4ef;
    border: none;
  }
  section.portada header, section.portada footer,
  section.seccion header, section.seccion footer { color: #9fb2c8; }
  section.portada::after, section.seccion::after { color: #9fb2c8; }
---

<!-- _class: portada -->
<!-- _paginate: false -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Bases de Datos
## Modelos de bases de datos y arquitectura cliente-servidor

1º Desarrollo de Aplicaciones Web (DAW) · Unidad Didáctica 1
Colegio Salesiano "San Ignacio" · Cádiz

---

# Índice de contenidos

<div class="columnas">
<div>

1. Introducción: ¿cómo organizamos los datos?
2. Modelo jerárquico
3. Modelo en red
4. Modelo relacional
5. Comparativa de modelos

</div>
<div>

6. Arquitectura cliente-servidor
7. Tipos de configuraciones
8. Evolución hacia la arquitectura multicapa
9. Consolidación y autoevaluación
10. Recursos y resumen

</div>
</div>

<!--
Nota para el docente: la presentación tiene dos bloques bien diferenciados.
Bloque A (apartados 2-5): CÓMO SE ORGANIZAN LOS DATOS (modelo lógico).
Bloque B (apartados 6-8): DÓNDE Y CÓMO SE DESPLIEGA el SGBD (arquitectura física/de red).
Conviene explicitar esta separación al alumnado desde el principio para que no mezclen "modelo" con "arquitectura".
-->

---

<!-- _class: seccion -->

# 1. Introducción
## ¿Cómo organizamos los datos?

---

# Cuestión inicial

> Imagina que tienes que organizar:
> - **Una biblioteca** con miles de libros.
> - **Una empresa** con empleados y departamentos.
> - **Una tienda online** con productos y clientes.
>
> **¿Cómo estructurarías esta información?**

### Actividad: organizadores naturales

**Organización:** por parejas · **Duración:** 3 minutos

1. Elegid uno de los ejemplos anteriores.
2. Dibujad cómo organizaríais esa información.
3. Explicad las **relaciones** entre los elementos.

<!--
Pista para el docente: tras la actividad, pedir a 2-3 parejas que muestren su dibujo.
Normalmente aparecen árboles (empresa → departamentos → empleados) y tablas (tienda online).
Usar esos dibujos como puente: "acabáis de inventar, sin saberlo, el modelo jerárquico y el relacional".
-->

---

# Concepto clave y evolución histórica

> **Modelo de base de datos:** define la forma en que los datos se **estructuran**, **organizan** y **relacionan** entre sí dentro de un sistema.

| Década | 1960 | 1970 | 1980 | 2000 |
|---|---|---|---|---|
| **Modelo** | Jerárquico | En red | Relacional | Orientado a objetos |

> **Pregunta conectora:** ¿por qué crees que han evolucionado los modelos de datos?

<div class="nota">

**Nota didáctica:** las fechas indican cuándo cada modelo se **popularizó**. El modelo relacional se propuso en 1970, pero su uso comercial se extendió en los 80. A partir de los 2000 también surgen las bases de datos **NoSQL** (documentales, clave-valor, de grafos), que estudiaréis más adelante.

</div>

---

<!-- _class: seccion -->

# 2. Modelo jerárquico

---

# Características principales

> **Organiza los datos en forma de árbol:**
> - Cada nodo **padre** puede tener varios **hijos**.
> - Cada hijo **solo tiene un padre**.
> - Representa relaciones **1:N (uno a muchos)**.

```
                    EMPRESA
                       │
          ┌────────────┴────────────┐
          │                         │
       Ventas                  Informática
          │                         │
     ┌────┴────┐               ┌────┴────┐
     │         │               │         │
    Ana       Luis           Marta      Juan
```

---

# Actividad: construye tu árbol

**Escenario:** el sistema de archivos de tu ordenador.

**Tareas:**
1. Dibuja la estructura desde `C:\` hasta un archivo concreto.
2. Identifica las relaciones padre-hijo.
3. ¿Puede un archivo estar en dos carpetas a la vez?

<div class="nota">

**Nota didáctica:** la pregunta 3 es la clave del tema. En un árbol puro, **no**: cada archivo tiene una única carpeta padre. Los accesos directos (Windows) o enlaces (Linux) son precisamente un "parche" para saltarse esa limitación, igual que el modelo en red lo hizo con el jerárquico.

</div>

---

# Ejemplo real: sistema de nóminas

**Contexto:** empresa con varios departamentos.

```
                          Empresa XYZ
                               │
        ┌──────────────────────┼──────────────────────┐
        │                      │                      │
   Dpto. Ventas            Dpto. IT          Dpto. Contabilidad
        │                      │                      │
   ┌────┴─────┐          ┌─────┴─────┐                │
   │          │          │           │                │
Ana García  Luis Pérez  Marta López  Juan Ruiz   Carmen Torres
 2.500 €     2.800 €     3.200 €     3.000 €       2.700 €
```

<!--
Pregunta para lanzar en clase: "¿Cómo obtendrías el salario de Marta López?"
Respuesta: hay que recorrer el árbol desde la raíz: Empresa → Dpto. IT → Marta López.
Esto ilustra que el acceso en el modelo jerárquico es por CAMINOS PREDEFINIDOS: rápido si la consulta sigue el árbol, costoso si no (p. ej., "todos los empleados que cobran más de 2.800 €").
-->

---

# Ventajas y desventajas del modelo jerárquico

<div class="pequeno">

| Ventaja | Descripción | Ejemplo |
|---|---|---|
| **Simplicidad** | Estructura fácil de entender | Árbol de carpetas |
| **Velocidad** | Accesos predefinidos muy rápidos | Búsqueda por departamento |
| **Eficiencia** | Ideal para relaciones 1:N | Padre → hijos |

| Desventaja | Descripción | Ejemplo |
|---|---|---|
| **Rigidez** | Un hijo solo puede tener un padre | Un empleado no puede estar en 2 departamentos |
| **Limitaciones** | No representa relaciones N:M | Proyectos con varios empleados |
| **Mantenimiento** | Cambios estructurales complicados | Reorganizar departamentos |

</div>

---

# Contexto histórico

> **Años 60:** primer modelo utilizado de forma masiva.
>
> **IBM IMS** (*Information Management System*): sistema pionero desarrollado para la misión Apollo.

> **Pregunta de transición:** si un empleado trabaja en **dos** departamentos, ¿cómo lo representarías en un modelo jerárquico?

<!--
Respuesta esperada: no se puede de forma natural; habría que DUPLICAR el registro del empleado bajo cada departamento.
Esto conecta con la UD anterior: duplicar = REDUNDANCIA → riesgo de INCONSISTENCIA.
Es justo el problema que resuelve el modelo en red (siguiente apartado).
-->

---

<!-- _class: seccion -->

# 3. Modelo en red

---

# Características principales

> **Evolución del modelo jerárquico:**
> - Un nodo **puede tener varios padres**.
> - Permite relaciones **N:M (muchos a muchos)**.
> - La información se guarda en **registros (nodos)** conectados mediante **enlaces**.

```
   Ana ─────────► Pedido 101 ◄───────── Luis
    │               │     │              │
    ▼               ▼     ▼              ▼
Pedido 102    Auriculares Móvil      Pedido 103
    │               ▲       ▲          │     │
    └───────────────┘       └──────────┘     ▼
                                         Portátil
```

<div class="nota">

**Nota didáctica:** fíjate en que *Pedido 101* recibe flechas de **dos clientes** y *Auriculares* de **dos pedidos**: eso es tener varios padres, algo imposible en el modelo jerárquico.

</div>

---

# Relaciones del ejemplo anterior

Para leer el diagrama con más claridad, estas son las conexiones que representa:

<div class="columnas">
<div>

**Clientes → Pedidos**

| Cliente | Pedidos |
|---|---|
| Ana | 101, 102 |
| Luis | 101, 103 |

</div>
<div>

**Pedidos → Productos**

| Pedido | Productos |
|---|---|
| 101 | Auriculares, Móvil |
| 102 | Auriculares |
| 103 | Móvil, Portátil |

</div>
</div>

<div class="nota">

**Nota didáctica:** en el original un mismo pedido (101) pertenece a dos clientes; sirve para ilustrar los "varios padres", aunque en una tienda real cada pedido tendría un único cliente.

</div>

---

# Actividad: red de relaciones

**Escenario:** una universidad con estudiantes y asignaturas.

| Estudiante | Asignaturas |
|---|---|
| **Ana** | Matemáticas, Programación, Inglés |
| **Luis** | Matemáticas, Historia, Inglés |
| **Marta** | Programación, Historia, Arte |

**Tareas:**
1. Dibuja la red de relaciones.
2. Identifica qué estudiantes comparten asignaturas.
3. ¿Cuántos "padres" tiene cada estudiante?

<!--
Soluciones:
2) Ana-Luis: Matemáticas e Inglés · Ana-Marta: Programación · Luis-Marta: Historia.
3) Depende de la dirección de las flechas. Si la asignatura es el "padre", cada estudiante tiene 3 padres. Y cada asignatura puede tener varios estudiantes: relación N:M.
Aprovechar para subrayar que la pregunta 3 no tiene sentido en el modelo jerárquico (solo habría 1 padre).
-->

---

# Ejemplo real: sistema de pedidos

**Contexto:** plataforma de comercio electrónico.

| Entidad | Relaciones |
|---|---|
| **Clientes** | Pueden realizar múltiples pedidos |
| **Pedidos** | Pertenecen a un cliente y contienen múltiples productos |
| **Productos** | Pueden aparecer en múltiples pedidos |

**Ventaja clave:** un producto puede aparecer en muchos pedidos simultáneamente.

---

# Ventajas y desventajas del modelo en red

<div class="pequeno">

| Ventaja | Descripción | Ejemplo |
|---|---|---|
| **Flexibilidad** | Permite relaciones complejas | Estudiante-Asignatura |
| **Realismo** | Refleja mejor el mundo real | Productos en múltiples pedidos |
| **Conectividad** | Enlaces múltiples entre registros | Red social de amistades |

| Desventaja | Descripción | Impacto |
|---|---|---|
| **Complejidad** | Diseño y mantenimiento difíciles | Programadores especializados |
| **Enlaces manuales** | Hay que gestionar punteros | Propenso a errores |
| **Sobrecarga** (*overhead*) | Gestión de múltiples relaciones | Mayor uso de recursos |

</div>

<div class="nota">

**Nota didáctica:** un **puntero** es una referencia a la posición física de otro registro. Si el registro se mueve, el puntero queda "roto". Este es el principal motivo por el que el modelo en red se abandonó en favor del relacional.

</div>

---

# Pregunta de reflexión

> En una red social como Instagram, ¿cómo representarías que…
> - un usuario puede **seguir** a muchos otros,
> - un usuario puede **ser seguido** por muchos otros,
> - una publicación puede recibir **likes** de múltiples usuarios?

<!--
Respuesta orientativa:
- Seguir/ser seguido es una relación N:M de USUARIO consigo mismo (relación reflexiva).
- Like es una relación N:M entre USUARIO y PUBLICACIÓN.
En el modelo en red se resolvería con enlaces entre registros. En el relacional (siguiente apartado) se resuelve con tablas intermedias: SEGUIDORES(id_seguidor, id_seguido) y LIKES(id_usuario, id_publicacion).
Dejarlo planteado como "cliffhanger" y retomarlo tras ver la tabla VALORACIONES.
-->

---

<!-- _class: seccion -->

# 4. Modelo relacional

---

# Características principales

> **El modelo más utilizado en la actualidad:**
> - Propuesto por **E. F. Codd en 1970**.
> - La información se organiza en **tablas**.
> - Filas = **tuplas / registros** · Columnas = **atributos / campos**.
> - Las relaciones se establecen mediante **claves externas** (ajenas).

<div class="nota">

**Nota didáctica:** la gran diferencia con los modelos anteriores es que **no hay punteros físicos**. Dos tablas se relacionan porque comparten un **valor** (por ejemplo, el mismo `ID_CLIENTE`). Eso hace que la estructura física pueda cambiar sin romper las relaciones.

</div>

---

# Ejemplo: tienda online (I)

**Tabla CLIENTES**

| ID_CLIENTE | NOMBRE | CIUDAD | EMAIL |
|---|---|---|---|
| 1 | Ana García | Sevilla | ana@email.com |
| 2 | Luis Pérez | Cádiz | luis@email.com |
| 3 | Marta López | Madrid | marta@email.com |

**Tabla PEDIDOS**

| ID_PEDIDO | ID_CLIENTE | FECHA | TOTAL |
|---|---|---|---|
| 101 | 1 | 2025-01-12 | 250,50 € |
| 102 | 2 | 2025-02-01 | 89,99 € |
| 103 | 1 | 2025-02-15 | 125,00 € |

---

# Ejemplo: tienda online (II)

**Tabla PRODUCTOS**

| ID_PRODUCTO | NOMBRE | PRECIO | CATEGORÍA |
|---|---|---|---|
| P001 | iPhone 15 | 899,99 € | Móviles |
| P002 | MacBook Air | 1.299,99 € | Portátiles |
| P003 | AirPods Pro | 249,99 € | Accesorios |

<div class="nota">

**Nota didáctica:** con estas tres tablas **no podemos saber qué productos contiene cada pedido**, porque PEDIDOS y PRODUCTOS no están conectadas. Como es una relación N:M, haría falta una cuarta tabla intermedia, por ejemplo `DETALLE_PEDIDO(ID_PEDIDO, ID_PRODUCTO, CANTIDAD)`. Lo veréis en detalle en el modelo Entidad-Relación.

</div>

---

# Actividad: constructor de consultas

Responde utilizando las tablas anteriores:

1. ¿Qué clientes viven en Sevilla?
2. ¿Cuántos pedidos ha realizado Ana García?
3. ¿Cuál es el pedido más caro?
4. ¿Qué productos cuestan menos de 300 €?

<div class="nota">

**Nota didáctica:** para la pregunta 2 tendrás que **cruzar dos tablas**: buscar el `ID_CLIENTE` de Ana en CLIENTES y después contar cuántas veces aparece en PEDIDOS. Esta operación de cruce es lo que en SQL se llama **JOIN**.

</div>

---

# Actividad: soluciones

| Pregunta | Respuesta |
|---|---|
| 1. Clientes de Sevilla | Ana García |
| 2. Pedidos de Ana García | 2 pedidos (101 y 103) |
| 3. Pedido más caro | Pedido 101 (250,50 €) |
| 4. Productos de menos de 300 € | AirPods Pro (249,99 €) |

<!--
Se han separado las soluciones en una diapositiva propia para que el alumnado piense antes de verlas.
Opcional: mostrar cómo sería la pregunta 1 en SQL (anticipo de la UD de SQL):
  SELECT NOMBRE FROM CLIENTES WHERE CIUDAD = 'Sevilla';
-->

---

# Conceptos clave: claves primaria y externa

<div class="columnas">
<div>

### Clave primaria (*Primary Key*)
> **Identifica de forma única** cada registro.

```
ID_CLIENTE   (en CLIENTES)
ID_PEDIDO    (en PEDIDOS)
ID_PRODUCTO  (en PRODUCTOS)
```

</div>
<div>

### Clave externa (*Foreign Key*)
> **Conecta las tablas** entre sí.

```
ID_CLIENTE en la tabla PEDIDOS
        ↓
hace referencia a
ID_CLIENTE en la tabla CLIENTES
```

</div>
</div>

<div class="nota">

**Nota didáctica:** la clave primaria **no puede repetirse ni estar vacía**. La clave externa **sí puede repetirse** (Ana tiene dos pedidos, por eso el valor `1` aparece dos veces en PEDIDOS), pero siempre debe existir en la tabla a la que apunta.

</div>

---

# Ejemplo ampliado: plataforma de streaming

<div class="columnas pequeno">
<div>

**Tabla PELÍCULAS**

| ID_PELICULA | TÍTULO | GÉNERO | AÑO |
|---|---|---|---|
| M001 | Matrix | Ciencia ficción | 1999 |
| M002 | Titanic | Romance | 1997 |

**Tabla USUARIOS**

| ID_USUARIO | NOMBRE | PLAN | FECHA_REGISTRO |
|---|---|---|---|
| U001 | Ana | Premium | 2023-01-15 |
| U002 | Luis | Básico | 2023-03-20 |

</div>
<div>

**Tabla VALORACIONES**

| ID_USUARIO | ID_PELICULA | PUNTUACIÓN | FECHA |
|---|---|---|---|
| U001 | M001 | 5 | 2024-02-10 |
| U001 | M002 | 4 | 2024-02-15 |
| U002 | M001 | 3 | 2024-03-01 |

<div class="nota">

**Nota didáctica:** VALORACIONES es una **tabla intermedia** que resuelve la relación N:M entre usuarios y películas. Su clave primaria es **compuesta**: (`ID_USUARIO`, `ID_PELICULA`). Así un usuario solo puede valorar una vez cada película.

</div>

</div>
</div>

---

# Ventajas y desventajas del modelo relacional

<div class="pequeno">

| Ventaja | Descripción | Ejemplo |
|---|---|---|
| **Independencia** | Niveles lógico y físico separados | Cambiar la estructura sin afectar a las aplicaciones |
| **SQL** | Lenguaje estándar universal | `SELECT`, `INSERT`, `UPDATE`, `DELETE` |
| **Integridad** | Reglas automáticas de consistencia | Claves primarias únicas |
| **Simplicidad** | Fácil de entender y usar | Tablas similares a hojas de cálculo |
| **Flexibilidad** | Permite consultas complejas | `JOIN` entre múltiples tablas |

| Desventaja | Descripción | Cuándo ocurre |
|---|---|---|
| **Complejidad** | Muchas tablas y relaciones | Sistemas muy grandes |
| **Rendimiento** | Los `JOIN` pueden ser costosos | Consultas complejas |
| **Planificación** | Requiere un diseño cuidadoso | Antes de implementar |

</div>

---

# Actividad práctica: diseña tu plataforma de streaming

**Escenario:** crear una plataforma de música similar a Spotify.

<div class="columnas">
<div>

**Entidades necesarias:**
- Usuarios
- Canciones
- Artistas
- Álbumes
- Playlists

</div>
<div>

**Tareas:**
1. Diseña las tablas con sus campos.
2. Identifica claves primarias y externas.
3. Define las relaciones entre tablas.
4. Escribe 3 consultas de ejemplo.

</div>
</div>

<div class="nota">

**Pista:** pregúntate en cada pareja de entidades "¿uno o muchos?". Por ejemplo, una playlist tiene muchas canciones y una canción puede estar en muchas playlists → N:M → necesitarás una tabla intermedia, como en VALORACIONES.

</div>

---

# Pregunta de transición

> Después de ver estos tres modelos, ¿cuál crees que es mejor para…
> - una aplicación móvil sencilla,
> - un sistema bancario,
> - una red social global?

<!--
Respuestas orientativas (no hay una única correcta; lo importante es la justificación):
- App móvil sencilla: relacional ligero (p. ej., SQLite, que viene integrado en Android/iOS).
- Sistema bancario: relacional, por la integridad y las transacciones.
- Red social global: relacional en gran parte, aunque en la práctica se combina con bases de datos NoSQL y de grafos para las relaciones de seguidores.
-->

---

<!-- _class: seccion -->

# 5. Comparativa de modelos

---

# Tabla comparativa

| Característica | Jerárquico | En red | Relacional |
|---|---|---|---|
| **Estructura** | Árbol | Grafo | Tablas |
| **Relaciones** | 1:N | N:M | N:M |
| **Flexibilidad** | Baja | Media | Alta |
| **Facilidad de uso** | Media | Baja | Alta |
| **Lenguaje / acceso** | Punteros | Enlaces | SQL |
| **Velocidad** | Alta | Media | Media |
| **Coste de desarrollo** | Bajo | Alto | Medio |
| **Época de uso** | Años 60 | Años 70 | Años 70 - actualidad |

<div class="nota">

**Nota didáctica:** "grafo" es el término matemático para una red de nodos y enlaces (en el original aparecía como "gráfico"). El relacional representa N:M **de forma indirecta**, mediante tablas intermedias.

</div>

---

# Actividad: elige tu modelo

Para cada escenario, **justifica** qué modelo utilizarías:

<div class="tres pequeno">
<div>

**Escenario 1: sistema de archivos del SO**
- **Estructura:** carpetas y subcarpetas.
- **Relaciones:** una carpeta padre, múltiples hijos.
- **Accesos:** navegación por rutas.

</div>
<div>

**Escenario 2: red social profesional (LinkedIn)**
- **Estructura:** usuarios, empresas, habilidades, contactos.
- **Relaciones:** un usuario puede trabajar en varias empresas y tener múltiples habilidades.
- **Accesos:** búsquedas complejas, recomendaciones.

</div>
<div>

**Escenario 3: reservas de vuelos**
- **Estructura:** vuelos, pasajeros, asientos, rutas.
- **Relaciones:** un vuelo tiene muchos pasajeros y un pasajero puede tener muchos vuelos.
- **Accesos:** consultas en tiempo real, alta concurrencia.

</div>
</div>

---

# Actividad: respuestas esperadas

| Escenario | Modelo | Justificación |
|---|---|---|
| **1. Sistema de archivos** | Jerárquico | Estructura natural de árbol |
| **2. Red social profesional** | Relacional | Flexibilidad para consultas complejas |
| **3. Reservas de vuelos** | Relacional | SQL para consultas complejas |

<div class="nota">

**Nota didáctica:** en los escenarios 2 y 3 hay relaciones N:M, lo que descarta el modelo jerárquico. Entre red y relacional, se elige el relacional por su facilidad de uso, el estándar SQL y la gestión de la concurrencia.

</div>

---

# Casos de uso reales

<div class="columnas">
<div>

### Modelos jerárquicos actuales
- **Sistemas de archivos:** Windows, macOS, Linux.
- **Organigramas empresariales:** estructura de mando.
- **XML / JSON:** estructuras de datos anidadas.
- **Clasificaciones:** taxonomías, categorías.

</div>
<div>

### Modelos relacionales dominantes
- **Sistemas bancarios:** MySQL, PostgreSQL, Oracle.
- **Comercio electrónico:** Amazon, eBay, Shopify.
- **Sistemas educativos:** Moodle, universidades.
- **Gestión hospitalaria:** historiales médicos.

</div>
</div>

<div class="nota">

**Nota didáctica:** XML y JSON no son bases de datos, sino **formatos** con estructura jerárquica. Como futuros desarrolladores web los usaréis constantemente (por ejemplo, en las respuestas de una API).

</div>

---

# Pregunta reflexiva

> ¿Por qué crees que el modelo relacional ha "ganado" la batalla y es el más utilizado actualmente?

**Pistas para el debate:**
- El estándar SQL.
- La independencia de datos.
- La flexibilidad de las consultas.
- El ecosistema de herramientas.

<!--
Conectar con la UD anterior: la independencia física y lógica de los datos (arquitectura ANSI/SPARC de tres niveles) es mucho más fácil de conseguir en el modelo relacional porque no hay punteros físicos.
-->

---

<!-- _class: seccion -->

# 6. Arquitectura cliente-servidor

---

# Concepto fundamental

> **Arquitectura cliente-servidor:** forma de **organizar los equipos y programas** que participan en la gestión y el uso de una base de datos.

### Cuestión inicial

> Cuando accedes a Instagram desde tu móvil…
> - ¿Dónde están almacenadas tus fotos?
> - ¿Dónde se procesan los "likes"?
> - ¿Qué hace exactamente tu móvil?

<div class="nota">

**Nota didáctica:** a partir de aquí cambiamos de pregunta. Hasta ahora estudiábamos **cómo se organizan** los datos (modelo); ahora estudiamos **dónde están** y **quién accede** a ellos (arquitectura).

</div>

---

# División de responsabilidades

```
 ┌──────────────────────────┐                    ┌──────────────────────────┐
 │         CLIENTE          │   Petición (SQL)   │         SERVIDOR         │
 │                          │ ─────────────────► │                          │
 │  · Interfaz de usuario   │        Red         │  · Almacena la BD        │
 │  · Presenta los datos    │ ◄───────────────── │  · Ejecuta el SGBD       │
 │  · Envía peticiones      │  Resultados/datos  │  · Procesa las consultas │
 └──────────────────────────┘                    └──────────────────────────┘
```

| Componente | Función | Ubicación |
|---|---|---|
| **Gestión de datos** | Manipula y administra la BD | Servidor |
| **Interfaz de usuario** | Muestra la información y permite interactuar | Cliente |
| **Lógica de aplicación** | Procesa las reglas de negocio | Cliente / Servidor |

---

# Actividad: identifica cliente y servidor

Para cada ejemplo, indica qué actúa como cliente y qué como servidor:

| Ejemplo | Cliente | Servidor |
|---|---|---|
| **Cajero automático** | ? | ? |
| **Gmail en el navegador** | ? | ? |
| **Fortnite online** | ? | ? |
| **Hoja de cálculo con BD local** | ? | ? |

<div class="nota">

**Recuerda:** "cliente" y "servidor" son **papeles** (roles) que desempeñan los programas, no tipos de ordenador. Un mismo equipo puede hacer de ambos a la vez.

</div>

---

# Actividad: soluciones

| Ejemplo | Cliente | Servidor |
|---|---|---|
| **Cajero automático** | El cajero | Sistema bancario central |
| **Gmail en el navegador** | El navegador | Servidores de Google |
| **Fortnite online** | Consola / PC | Servidores de Epic Games |
| **Hoja de cálculo con BD local** | El mismo ordenador | El mismo ordenador |

<!--
El último caso conecta directamente con la "configuración monoequipo" del apartado 7.
Matiz: una hoja de cálculo (Excel) no es un SGBD; un ejemplo más preciso sería Microsoft Access o SQLite en el propio equipo.
-->

---

# Ejemplo detallado: banca online

<div class="columnas">
<div>

### En el cliente (app móvil)
- Pantalla de inicio de sesión
- Mostrar el saldo actual
- Historial de movimientos
- Formulario de transferencia

</div>
<div>

### En el servidor
- Base de datos con las cuentas
- Validación de credenciales
- Cálculo de saldos
- Autorización de operaciones

</div>
</div>

### Comunicación

```
Cliente envía:     "LOGIN: usuario123, password456"
Servidor responde: "OK: Token de sesión ABC123"

Cliente envía:     "CONSULTAR_SALDO: cuenta 12345"
Servidor responde: "SALDO: 1.250,75 €"
```

---

# Banca online: aclaraciones

<div class="nota">

**Nota didáctica 1 (seguridad):** el intercambio anterior es una **simplificación**. En una aplicación real la contraseña nunca viaja en texto plano: la comunicación va **cifrada (HTTPS)** y el servidor no guarda la contraseña, sino un **hash** de ella.

</div>

<div class="nota">

**Nota didáctica 2 (token):** el **token de sesión** evita enviar la contraseña en cada petición. El cliente lo adjunta en las siguientes solicitudes para demostrar que ya se identificó.

</div>

<div class="nota">

**Nota didáctica 3 (lógica):** los cálculos importantes (saldos, autorizaciones) se hacen **siempre en el servidor**. Si se hicieran en el cliente, un usuario podría manipular la app y falsear el resultado.

</div>

---

# Ventajas de la arquitectura cliente-servidor

| Ventaja | Descripción | Ejemplo |
|---|---|---|
| **Centralización** | Datos en un solo lugar | Actualizaciones instantáneas |
| **Seguridad** | Control centralizado del acceso | Permisos gestionados desde el servidor |
| **Concurrencia** | Múltiples usuarios simultáneos | Miles de usuarios en WhatsApp |
| **Mantenimiento** | Cambios solo en el servidor | Actualizar sin reinstalar en cada cliente |
| **Escalabilidad** | Añadir clientes fácilmente | Nuevos usuarios sin problemas |
| **Ubicuidad** | Acceso desde cualquier lugar | Teletrabajo |

---

# Desventajas de la arquitectura cliente-servidor

| Desventaja | Descripción | Impacto |
|---|---|---|
| **Punto único de fallo** | Si cae el servidor, todo se detiene | Instagram caído = nadie puede usarlo |
| **Coste de infraestructura** | Servidores potentes y caros | Inversión inicial alta |
| **Dependencia de la red** | Sin conexión no hay servicio | Sin wifi no hay acceso |
| **Cuello de botella** | El servidor tiene una capacidad limitada | Lentitud en horas punta |

> **Pregunta de reflexión:** ¿por qué aplicaciones como WhatsApp funcionan incluso con poca conexión, mientras que otras como Instagram necesitan una buena conexión?

<!--
Pistas para el debate:
- Un mensaje de texto ocupa muy pocos bytes; una foto o un vídeo, miles de veces más.
- WhatsApp guarda los mensajes en una cola local y los envía cuando hay red (y guarda el historial en el propio móvil).
- Instagram descarga continuamente contenido nuevo desde el servidor.
Idea clave: cuanto más dependa la app de datos del servidor en tiempo real, más le afecta la "dependencia de la red".
-->

---

<!-- _class: seccion -->

# 7. Tipos de configuraciones

---

# 1. Configuración monoequipo (anfitrión)

> **Cliente y servidor en el mismo equipo.**

```
   ┌────────────────────────── MI ORDENADOR ───────────────────────────┐
   │                                                                   │
   │   Aplicación (cliente)  ◄── lee / escribe ──►  Datos (servidor)   │
   │                                                                   │
   └───────────────────────────────────────────────────────────────────┘
```

**Ejemplo: entorno de desarrollo local**
- **Situación:** programador trabajando en su proyecto.
- **Cliente:** navegador web (`localhost:3000`).
- **Servidor:** MySQL instalado localmente.
- **BD:** base de datos de pruebas.

<!--
El original ilustra este caso con Excel + archivo datos.xlsx. Se ha generalizado a "aplicación / datos" porque Excel no es un SGBD.
El ejemplo del desarrollador local es exactamente lo que harán en clase con XAMPP o MySQL Workbench: conviene decírselo para que lo identifiquen.
-->

---

# Monoequipo: ventajas y desventajas

<div class="columnas">
<div>

### Ventajas
- **Muy rápido:** sin latencia de red.
- **Económico:** un solo equipo.
- **Privado:** los datos no salen del equipo.

</div>
<div>

### Desventajas
- **Un solo usuario.**
- **Sin acceso remoto.**
- **Recursos limitados.**

</div>
</div>

<div class="nota">

**Nota didáctica:** `localhost` (o `127.0.0.1`) es el nombre con el que un equipo se refiere **a sí mismo**. Cuando en clase instaléis MySQL en vuestro ordenador y os conectéis a `localhost`, estaréis usando esta configuración.

</div>

---

# 2. Cliente/servidor clásico

> **Un servidor dedicado y múltiples clientes.**

```
     PC Oficina 1 ────┐
                      │
     PC Oficina 2 ────┼──── Red ────► SERVIDOR BD ────► Oracle Database
                      │
     PC Oficina 3 ────┘
```

**Ejemplo: sistema de gestión escolar**
- **Servidor:** equipo ubicado en el centro de datos del colegio.
- **Clientes:** PC de secretaría, aulas y dirección.
- **BD:** datos de alumnos, notas y horarios.

---

# Actividad: diseña tu red escolar

Identifica a qué información accedería cada usuario:

| Usuario | Pregunta |
|---|---|
| **Profesor/a** | ¿Qué puede ver y modificar? |
| **Secretaría** | ¿Qué permisos necesita? |
| **Dirección** | ¿Qué nivel de acceso tiene? |
| **Alumno/a** | ¿Qué puede consultar? |

<div class="nota">

**Conexión con la unidad anterior:** esta actividad aplica dos conceptos ya vistos: las **vistas** (nivel externo: cada usuario ve solo una parte de la BD) y el lenguaje **DCL** (`GRANT` / `REVOKE`) para conceder permisos.

</div>

---

# 3. Bases de datos distribuidas

> **La información se reparte entre varios servidores.**

```
                          Usuario global
                                │
                                ▼
                         Sistema central
                                │
          ┌─────────────────────┼─────────────────────┐
          ▼                     ▼                     ▼
   Servidor Europa       Servidor América        Servidor Asia
  (datos de España)    (datos de EE. UU.)     (datos de Japón)
```

**Ejemplo: Netflix global**
- **Europa:** perfiles y visualizaciones de usuarios europeos.
- **América:** datos de usuarios americanos.
- **Asia:** información de usuarios asiáticos.
- **Usuario:** percibe "una sola" plataforma Netflix.

---

# Bases de datos distribuidas: ventajas y desventajas

<div class="columnas">
<div>

### Ventajas
- **Rendimiento:** los datos están cerca del usuario.
- **Resistencia:** si un servidor cae, los demás siguen funcionando.
- **Escalabilidad:** se añaden servidores por región.

</div>
<div>

### Desventajas
- **Complejidad:** sincronización entre servidores.
- **Consistencia:** mantener los mismos datos en todos los nodos.
- **Coste:** múltiples infraestructuras.

</div>
</div>

<div class="nota">

**Nota didáctica:** que el usuario perciba "una sola" base de datos aunque esté repartida se denomina **transparencia de distribución**. Además, la "resistencia" responde a la principal desventaja del cliente-servidor clásico: el **punto único de fallo**.

</div>

---

# 4. Con servidor de aplicaciones

> **Tres capas separadas: cliente, aplicación y base de datos.**

```
  Navegador web ──HTTP/HTTPS──► Servidor web ──► Servidor de aplicaciones ──SQL──► Servidor BD
                                (Apache/Nginx)    (PHP / Java / Node.js)         (MySQL/PostgreSQL)
  └── Capa cliente ──┘          └──────────── Capa aplicación ────────────┘      └─ Capa datos ─┘
```

**Ejemplo: Moodle (plataforma educativa)**

<div class="tres pequeno">
<div>

**Capa cliente**
- Navegador del estudiante o profesor
- App móvil de Moodle

</div>
<div>

**Capa aplicación**
- Servidor con el código PHP de Moodle
- Gestiona sesiones, permisos y lógica de negocio

</div>
<div>

**Capa datos**
- Base de datos MySQL
- Almacena usuarios, cursos y calificaciones

</div>
</div>

<!--
Aclaración: el diagrama tiene 4 cajas pero son 3 capas. El servidor web y el servidor de aplicaciones suelen considerarse parte de la misma capa intermedia (a menudo se ejecutan en la misma máquina, p. ej., Apache con PHP).
-->

---

# Actividad: traza la petición

**Escenario:** un estudiante sube una tarea a Moodle.

| Paso | Qué ocurre | Capa |
|---|---|---|
| 1 | El estudiante hace clic en "Subir archivo" | Cliente |
| 2 | El navegador envía una petición HTTP | Cliente → Aplicación |
| 3 | El servidor web la recibe y procesa | Aplicación |
| 4 | La aplicación valida permisos y guarda el archivo | Aplicación |
| 5 | La base de datos almacena los metadatos | Datos |
| 6 | La confirmación regresa al estudiante | Aplicación → Cliente |

<div class="nota">

**Nota didáctica:** se ha añadido la columna "Capa" para relacionar cada paso con la arquitectura. Los **metadatos** son "datos sobre datos": nombre del archivo, fecha, autor, tamaño… El archivo en sí suele guardarse en disco, no dentro de la BD.

</div>

---

# Pregunta comparativa

> ¿Qué configuración utilizarías para…
> - una tienda con 3 empleados,
> - un banco nacional,
> - una startup tecnológica,
> - un videojuego multijugador global?

<!--
Respuestas orientativas:
- Tienda con 3 empleados: monoequipo o cliente/servidor clásico pequeño (un PC hace de servidor).
- Banco nacional: cliente/servidor con servidor de aplicaciones, con alta disponibilidad y réplicas.
- Startup tecnológica: multicapa en la nube, para poder crecer sin gran inversión inicial.
- Videojuego global: base de datos distribuida por regiones (latencia baja para cada jugador).
-->

---

<!-- _class: seccion -->

# 8. Evolución hacia la arquitectura multicapa

---

# Arquitectura de tres capas (*three-tier*)

> **Separación clara de responsabilidades en tres niveles.**

```
 ┌──────────────────────────────────────────────────────────┐
 │  CAPA DE PRESENTACIÓN                                    │
 │  Interfaces de usuario · Apps móviles · Navegadores web  │
 └──────────────────────────────────────────────────────────┘
                 │  API REST (HTTP / JSON)
 ┌──────────────────────────────────────────────────────────┐
 │  CAPA DE LÓGICA                                          │
 │  Reglas de negocio · Procesamiento · Validaciones        │
 └──────────────────────────────────────────────────────────┘
                 │  SQL (conectores de BD)
 ┌──────────────────────────────────────────────────────────┐
 │  CAPA DE DATOS                                           │
 │  Base de datos · Almacenamiento · Consultas              │
 └──────────────────────────────────────────────────────────┘
```

<div class="nota">

**Atención:** no confundas estas **tres capas** (arquitectura de la aplicación) con los **tres niveles** ANSI/SPARC de la unidad anterior (interno, conceptual y externo), que describen la propia base de datos.

</div>

---

# Actividad: diseña Amazon en tres capas

Identifica en qué capa va cada funcionalidad:

| Funcionalidad | Capa de presentación | Capa de lógica | Capa de datos |
|---|---|---|---|
| **Carrito de compra** | Interfaz del carrito | Calcular total e impuestos | Productos y precios |
| **Buscar productos** | Caja de búsqueda | Algoritmo de búsqueda | Catálogo de productos |
| **Procesar pago** | Formulario de pago | Validar tarjeta y stock | Guardar la transacción |
| **Reseñas** | Mostrar estrellas | Calcular la media | Comentarios de usuarios |

<!--
Sugerencia didáctica: mostrar primero la tabla solo con la columna "Funcionalidad" (tapando el resto) y que el alumnado proponga el contenido de cada capa. Después revelar la tabla completa.
-->

---

# Ejemplo detallado: plataforma de streaming

<div class="tres pequeno">
<div>

### Capa de presentación
**App móvil:**
- Lista de películas
- Reproductor de vídeo
- Perfil de usuario

**Navegador web:**
- Catálogo navegable
- Sistema de búsqueda
- Panel de administración

</div>
<div>

### Capa de lógica de negocio
**Servidor de aplicaciones:**
- Algoritmo de recomendaciones
- Gestión de suscripciones
- Control de acceso por regiones
- Transcodificación de vídeos

</div>
<div>

### Capa de datos
**Bases de datos:**
- Catálogo de contenido
- Perfiles de usuarios
- Historiales de visualización
- Datos de facturación

</div>
</div>

<div class="nota">

**Nota didáctica:** la **transcodificación** consiste en convertir un vídeo a distintos formatos y calidades (4K, HD, móvil…) para adaptarlo al dispositivo y a la conexión de cada usuario.

</div>

---

# Ventajas de la arquitectura multicapa

| Ventaja | Descripción | Ejemplo |
|---|---|---|
| **Mantenibilidad** | Cambios aislados por capa | Cambiar el diseño sin tocar la BD |
| **Escalabilidad** | Cada capa escala de forma independiente | Más servidores de aplicación en Black Friday |
| **Especialización** | Equipos expertos por capa | *Frontend*, *backend*, DBA |
| **Reutilización** | Una misma lógica para varias interfaces | Una API para web y móvil |
| **Pruebas** | Pruebas independientes por capa | Tests unitarios de la lógica |

<div class="nota">

**Vocabulario DAW:** el **frontend** es la capa de presentación y el **backend**, la capa de lógica y datos. Son términos que usaréis continuamente en el ciclo.

</div>

---

# Evolución a la nube: microservicios

```
       App móvil ─────┐                 ┌──► Microservicio Auth ───────► BD Usuarios
                      │                 │
                      ├──► API Gateway ─┼──► Microservicio Productos ──► BD Productos
                      │                 │
       Web app ───────┘                 ├──► Microservicio Pagos ──────► BD Transacciones
                                        │
                                        └──► Microservicio Analytics ──► BD Analytics
```

<div class="nota">

**Nota didáctica:** cada **microservicio** es una pequeña aplicación independiente con su propia base de datos. El **API Gateway** es la "puerta de entrada" única que recibe las peticiones de los clientes y las reparte al microservicio adecuado.

</div>

---

# Características *cloud native*

| Característica | Descripción | Ejemplos |
|---|---|---|
| **Contenedores** | Empaquetan una aplicación con todo lo que necesita | Docker, Kubernetes |
| **Serverless** | Se ejecuta código sin gestionar servidores | AWS Lambda, Azure Functions |
| **Base de datos como servicio** | El proveedor gestiona la BD | Amazon RDS, Azure Cosmos DB |
| **Autoescalado** | Los recursos se ajustan automáticamente a la demanda | Más instancias en horas punta |

<!--
La columna "Descripción" se ha añadido para aclarar cada término, ya que en 1º DAW suelen ser conceptos nuevos.
No es necesario profundizar: basta con que les "suenen" y sepan que son la evolución natural de la arquitectura multicapa.
-->

---

# Actividad final: tu startup multicapa

**Escenario:** crear una plataforma de reparto de comida a domicilio.

1. **Diseña la capa de presentación:** ¿qué interfaces necesitas? (cliente, restaurante, repartidor)
2. **Define la lógica de negocio:** ¿qué reglas y procesos necesitas?
3. **Planifica la capa de datos:** ¿qué información hay que almacenar?
4. **Considera la escalabilidad:** ¿cómo gestionar 1.000 pedidos simultáneos?

> **Pregunta de síntesis:** compara las ventajas de un **monolito tradicional** (todo en un servidor), una **arquitectura de 3 capas** y **microservicios en la nube**. ¿Cuándo utilizarías cada uno?

<!--
Orientación para la pregunta de síntesis:
- Monolito: proyectos pequeños o que empiezan; más sencillo de desarrollar y desplegar.
- 3 capas: la opción "estándar" para la mayoría de aplicaciones web de tamaño medio.
- Microservicios: sistemas grandes, con muchos equipos y necesidad de escalar partes concretas. Añaden mucha complejidad, por lo que no conviene usarlos "porque sí".
-->

---

<!-- _class: seccion -->

# 9. Actividades de consolidación

---

# Actividad integradora 1: elige el modelo y la arquitectura

Para cada escenario, decide: **1)** modelo de datos (jerárquico, red o relacional), **2)** arquitectura (monoequipo, cliente-servidor o multicapa) y **3)** justifica la combinación.

<div class="tres pequeno">
<div>

**Biblioteca digital**
- **Entidades:** libros, usuarios, préstamos, autores, categorías.
- **Usuarios:** 500 estudiantes concurrentes.
- **Acceso:** local y remoto.

</div>
<div>

**Videojuego multijugador**
- **Entidades:** jugadores, partidas, rankings, objetos, clanes.
- **Usuarios:** 100.000 jugadores en todo el mundo.
- **Requisitos:** tiempo real, alta disponibilidad.

</div>
<div>

**Tienda de barrio**
- **Entidades:** productos, ventas, clientes, proveedores.
- **Usuarios:** 2 empleados.
- **Requisitos:** sencillo, económico y fiable.

</div>
</div>

---

# Actividad 2: role playing (comité de decisión)

**Escenario:** *startup* de transporte compartido (similar a Uber). **Debate:** ¿qué arquitectura implementar?

<div class="columnas pequeno">
<div>

**Roles:**
- **CTO** (*Chief Technology Officer*): toma las decisiones técnicas.
- **CFO** (*Chief Financial Officer*): controla el presupuesto.
- **Diseñador/a UX:** se centra en la experiencia de usuario.
- **Experto/a en seguridad:** prioriza la seguridad.
- **Lead developer:** valora la implementación.

</div>
<div>

**Aspectos a considerar:**
- Escalabilidad global
- Coste de desarrollo
- Tiempo hasta el lanzamiento
- Seguridad de los datos
- Experiencia de usuario

</div>
</div>

---

# Actividad 3: red social universitaria

<div class="columnas pequeno">
<div>

**Especificaciones:**
- 10.000 estudiantes
- 50 universidades
- Mensajería instantánea
- Compartir apuntes
- Grupos de estudio

</div>
<div>

**Entregables:**
1. **Modelo de datos:** diseño de tablas y relaciones.
2. **Arquitectura:** diagrama de componentes.
3. **Interfaces:** bocetos (*mockups*) de las pantallas principales.
4. **Escalabilidad:** plan de crecimiento.
5. **Seguridad:** medidas de protección de datos.

</div>
</div>

<div class="nota">

**Nota didáctica:** al tratar datos personales de estudiantes, la propuesta de seguridad debería tener en cuenta el **RGPD** (Reglamento General de Protección de Datos).

</div>

---

# Autoevaluación (I)

### Nivel básico
1. ¿Cuáles son las principales características del modelo jerárquico?
2. ¿Qué elementos componen una tabla en el modelo relacional?
3. ¿Cuál es la diferencia entre cliente y servidor en una arquitectura cliente-servidor?

### Nivel intermedio
4. Compara las ventajas y desventajas de los tres modelos de datos.
5. ¿Cuándo recomendarías utilizar una arquitectura distribuida?
6. ¿Qué ventajas ofrece la arquitectura multicapa frente a la cliente-servidor tradicional?

---

# Autoevaluación (II)

### Nivel avanzado
7. Diseña un sistema de gestión hospitalaria especificando el modelo de datos y la arquitectura.
8. ¿Cómo evolucionaría tu diseño si el sistema tuviera que dar servicio a 100 hospitales?
9. Analiza por qué el modelo relacional se ha impuesto a los demás modelos.

---

<!-- _class: seccion -->

# 10. Recursos y resumen

---

# Recursos adicionales

<div class="columnas pequeno">
<div>

### Lecturas recomendadas
- *Database System Concepts* – Silberschatz, Korth, Sudarshan
- *Designing Data-Intensive Applications* – Martin Kleppmann
- *Clean Architecture* – Robert C. Martin

### Vídeos educativos
- "Database Design Course" – FreeCodeCamp
- "Microservices Explained" – TechWorld with Nana
- "SQL vs NoSQL" – Hussein Nasser

</div>
<div>

### Herramientas prácticas
- **Diseño:** draw.io, Lucidchart
- **Bases de datos:** MySQL Workbench, pgAdmin
- **Nube:** AWS RDS, Google Cloud SQL
- **Modelado:** ERD Plus, dbdiagram.io

### Sitios web de referencia
- Database Design Principles – Microsoft Docs
- AWS Architecture Center
- High Scalability – casos reales

</div>
</div>

<!--
Corrección: el original atribuye "Database System Concepts" a "Silberschatz, Galvin, Gagne", que son los autores de "Operating System Concepts". Los autores de "Database System Concepts" son Silberschatz, Korth y Sudarshan.
-->

---

# Próximas unidades

| Unidad | Contenido |
|---|---|
| **UD2** | Modelo Entidad-Relación en profundidad |
| **UD3** | Normalización de bases de datos |
| **UD4** | SQL: lenguaje de consulta estructurado |

---

# Resumen: conceptos clave

| Tema | Conceptos principales |
|---|---|
| **Modelos de datos** | Jerárquico (árbol), red (grafo), relacional (tablas) |
| **Modelo relacional** | Tablas, claves primarias y externas, SQL |
| **Cliente-servidor** | Separación de responsabilidades, centralización |
| **Arquitecturas** | Monoequipo, distribuidas, multicapa |
| **Evolución** | De los grandes ordenadores centrales a los microservicios en la nube |

---

# Competencias desarrolladas

<div class="columnas">
<div>

Al finalizar esta unidad, el alumnado será capaz de:

- **Distinguir** entre los diferentes modelos de datos.
- **Evaluar** qué modelo usar según el contexto.
- **Diseñar** arquitecturas cliente-servidor básicas.
- **Analizar** ventajas y desventajas de cada enfoque.
- **Aplicar** los conocimientos en casos prácticos reales.
- **Justificar** decisiones técnicas de diseño.

</div>
<div>

### Conexión con el futuro
Estos conocimientos son la base para:
- El diseño de sistemas empresariales.
- Las arquitecturas *cloud native*.
- El desarrollo de aplicaciones modernas.
- La seguridad en sistemas distribuidos.
- La escalabilidad y el rendimiento.

</div>
</div>

---

<!-- _class: portada -->
<!-- _paginate: false -->
<!-- _header: "" -->
<!-- _footer: "" -->

# Fin de la presentación

Modelos de bases de datos y arquitectura cliente-servidor
Bases de Datos · 1º DAW
Colegio Salesiano "San Ignacio" · Cádiz

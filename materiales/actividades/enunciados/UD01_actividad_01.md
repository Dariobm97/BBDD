# UD01 - Actividades
## Centros Deportivos Atlántico

| | |
|---|---|
| **Ciclo formativo** | 1º Desarrollo de Aplicaciones Web (DAW) |
| **Módulo profesional** | 0484 · Bases de Datos |
| **Unidad didáctica** | UD1 · Conceptos básicos · Modelos de bases de datos y arquitectura cliente-servidor |
| **Resultado de aprendizaje** | RA1. Reconoce los elementos de las bases de datos, analizando sus funciones y valorando la utilidad de los sistemas gestores. |
| **Criterios de evaluación** | RA1.a · RA1.b · RA1.c · RA1.d · RA1.e · RA1.f · RA1.g · RA1.h · RA1.i · RA1.j |


---

## 1. Objetivo de la actividad

El objetivo de esta actividad es que **apliques** los contenidos de la unidad a un caso realista. No se trata de reproducir definiciones, sino de demostrar que sabes **analizar** un sistema de información, **detectar** sus problemas, **proponer** soluciones y **justificar** tus decisiones técnicas.

---

## 2. Descripción del caso

**Centros Deportivos Atlántico** es una cadena de gimnasios con tres sedes en la provincia de Cádiz: **Cádiz**, **Jerez** y **San Fernando**. Cuenta con unos 1.800 socios.

### 3.1. Situación actual

Cada sede dispone de un ordenador en recepción donde se guarda la información en **ficheros independientes**. La sede de Cádiz utiliza ficheros de texto con campos de longitud fija; la de Jerez, una hoja de cálculo; y la de San Fernando, un fichero de texto con los campos en otro orden. Hay programas sencillos, escritos hace años por un informático externo, que leen estos ficheros para emitir los recibos mensuales.

Los socios pueden contratar tres tarifas: **Básica** (una sede), **Premium** (una sede con clases ilimitadas) y **Multisede** (acceso a las tres sedes).

**Extracto del fichero `SOCIOS` · Sede Cádiz**

| Nº_SOCIO | DNI | NOMBRE | APELLIDOS | DIRECCIÓN | CP | TELÉFONO | IBAN | TARIFA | PRECIO |
|---|---|---|---|---|---|---|---|---|---|
| C-014 | 31234567A | Lucía | Ramos Gil | C/ Sopranis, 12 | 11005 | 600111222 | ES12 **** 3456 | Multisede | 45 € |
| C-015 | 44556677B | Pedro | Díaz Mora | Av. Andalucía, 3 | 11008 | 600333444 | ES98 **** 1122 | Básica | 30 € |
| C-016 | 77889900C | Ana | Torres Vela | C/ Ancha, 7 | 11001 | 600555666 | ES45 **** 7788 | Básica | 32 € |

**Extracto del fichero `SOCIOS` · Sede Jerez**

| Nº_SOCIO | DNI | NOMBRE | APELLIDOS | DIRECCIÓN | CP | TELÉFONO | IBAN | TARIFA | PRECIO |
|---|---|---|---|---|---|---|---|---|---|
| J-102 | 31234567A | Lucía | Ramos Gil | C/ Larga, 40 | 11402 | 600111222 | ES12 **** 3456 | Multisede | 45 € |

**Extracto del fichero `CLASES` · Sede Cádiz**

| COD_CLASE | NOMBRE | DÍA Y HORA | MONITOR | AFORO | PLAZAS_LIBRES |
|---|---|---|---|---|---|
| PIL-1 | Pilates | Lunes 18:00 | Marta Gómez | 15 | 4 |
| SPI-1 | Spinning | Miércoles 19:00 | Andrés Vela | 20 | 1 |
| YOG-1 | Yoga | Jueves 10:00 | Marta Gómez | 12 | 6 |

**Extracto del fichero `RESERVAS` · Sede Cádiz**

```
Nº_SOCIO | NOMBRE_SOCIO | CLASE_1, DÍA_HORA_1, MONITOR_1          | CLASE_2, DÍA_HORA_2, MONITOR_2
C-014    | Lucía Ramos  | Pilates, Lunes 18:00, Marta Gómez       | Spinning, Miércoles 19:00, Andrés Vela
C-015    | Pedro Díaz   | Spinning, Miércoles 19:00, Andrés Vela  | —
C-016    | Ana Torres   | Pilates, Lunes 18:00, Marta Gómez       | Yoga, Jueves 10:00, Marta Gómez
C-999    | (sin nombre) | Yoga, Jueves 10:00, Marta Gómez         | —
```

### 3.2. Incidencias registradas el último trimestre

| Nº | Incidencia |
|---|---|
| **I1** | Lucía Ramos comunicó en la sede de Cádiz su cambio de domicilio. Un mes después, la sede de Jerez le sigue enviando la correspondencia a su dirección antigua. |
| **I2** | Un miércoles, la recepcionista del mostrador y la que atendía el teléfono asignaron **a la vez** la última plaza de Spinning. A la clase acudieron 21 personas para un aforo de 20. |
| **I3** | La gerente pidió un listado de los socios de las tres sedes con código postal 11005. El informático respondió que necesitaba **escribir un programa nuevo** y antes **unificar los formatos** de los tres ficheros, y presupuestó dos semanas de trabajo. |
| **I4** | Los monitores utilizan el ordenador de recepción para consultar sus clases y **pueden ver el IBAN** de todos los socios. |
| **I5** | En el fichero `RESERVAS` figura una reserva del socio **C-999**, que no existe en el fichero `SOCIOS`. |
| **I6** | Para poder guardar teléfonos con prefijo internacional se amplió la longitud del campo `TELÉFONO`. Al día siguiente **dejó de funcionar el programa de recibos**. |
| **I7** | Dos socios con la misma tarifa Básica pagan precios distintos (30 € y 32 €), sin que nadie sepa cuál es el correcto. |

### 3.3. Plan de futuro

La dirección ha aprobado un plan con los siguientes objetivos:

- **Sustituir los ficheros por un Sistema Gestor de Bases de Datos** relacional.
- Lanzar una **aplicación móvil** para que los socios consulten horarios y reserven clases.
- **Expandirse en tres años a 20 sedes** en tres zonas: **Cádiz**, **Sevilla** y **Málaga**, con unos 15.000 socios.
- **Analizar el histórico** de reservas y accesos para decidir horarios, clases y la ubicación de nuevas sedes.

Personas implicadas en el proyecto:

- **La gerente**, que decide qué información necesita la empresa.
- **Un técnico de sistemas** contratado para instalar, configurar y administrar la base de datos.
- **Una empresa de desarrollo** que programará la aplicación móvil.
- **Las recepcionistas**, **el personal de administración**, **los monitores** y **los socios**.

---

## 3. Actividades

### Actividad 1. Análisis del sistema actual de ficheros · RA1.a 

**1.1.** Para **cada incidencia** (I1 a I7), indica qué problema propio de los sistemas de ficheros la ha provocado y **explica por qué** la organización actual la hace posible. Debes señalar los **datos concretos** de los extractos que lo demuestran.

| Incidencia | Problema de los sistemas de ficheros | Explicación aplicada al caso (con datos de los extractos) |
|---|---|---|
| I1 | Redundancia → inconsistencia | Lucía aparece en Cádiz con C/ Sopranis, 12 y en Jerez con C/ Larga, 40. |
| I2 | Concurrencia | Dos recepcionistas asignaron a la vez la última plaza y acabaron 21 personas para 20 plazas. |
| I3 | Acceso difícil a los datos | Las sedes usan formatos diferentes, por lo que hay que unificarlos para consultar los datos. |
| I4 | Falta de seguridad | Los monitores pueden acceder al IBAN de todos los socios. |
| I5 | Falta de integridad | Aparece una reserva para C-999, pero ese socio no existe en SOCIOS. |
| I6 | Dependencia entre programas y datos | Al ampliar el campo TELÉFONO, dejó de funcionar el programa de recibos. |
| I7 | Inconsistencia | Dos socios con tarifa Básica pagan precios diferentes: 30 € y 32 €.

**1.2.** El fichero `RESERVAS` repite en cada registro el nombre del socio, el día, la hora y el monitor de cada clase.

- **a)** Explica qué consecuencias tiene esta organización cuando, por ejemplo, Andrés Vela deja de impartir Spinning.
- **b)** Propón una **reorganización en varios ficheros** que elimine las repeticiones, indicando los campos de cada uno y el **campo clave**.
- **c)** Define el **formato de registro** del nuevo fichero `SOCIOS` (campo, nombre, tipo y longitud) e indica su campo clave. Justifica por qué no has elegido `NOMBRE` como clave.

1.2.a) Si Andrés Vela deja de impartir Spinning, habría que cambiar su nombre en todas las reservas donde aparezca. Si se olvida alguna, quedarían datos diferentes y se produciría una inconsistencia.

1.2.b) Se pueden separar los datos en varios ficheros. El fichero SOCIOS tendría Nº_SOCIO, DNI, NOMBRE, APELLIDOS, DIRECCIÓN, CP, TELÉFONO, IBAN y TARIFA. Su clave sería Nº_SOCIO.

El fichero MONITORES tendría COD_MONITOR, NOMBRE y APELLIDOS. Su clave sería COD_MONITOR.

El fichero CLASES tendría COD_CLASE, NOMBRE, DÍA, HORA, COD_MONITOR y AFORO. Su clave sería COD_CLASE.

El fichero RESERVAS tendría Nº_SOCIO y COD_CLASE. Su clave sería la combinación de Nº_SOCIO y COD_CLASE.

1.2.c)

El fichero SOCIOS tendría los siguientes campos: Nº_SOCIO, alfanumérico de 10 caracteres; DNI, alfanumérico de 9; NOMBRE, texto de 30; APELLIDOS, texto de 60; DIRECCIÓN, texto de 100; CP, numérico de 5; TELÉFONO, alfanumérico de 15; IBAN, alfanumérico de 34; y TARIFA, alfanumérico de 10.

La clave sería Nº_SOCIO porque identifica de forma única a cada socio. No elegiría NOMBRE porque puede haber varios socios con el mismo nombre.

---

### Actividad 2. Utilidad de un Sistema Gestor de Bases de Datos · RA1.d 

**2.1.** Explica cómo resolvería un SGBD **cada una de las incidencias** de la actividad 1. Relaciona cada solución con la **ventaja concreta** del SGBD que la hace posible.

I1: El SGBD tendría los datos de los socios centralizados, por lo que al cambiar la dirección de Lucía se actualizaría una sola vez y el cambio estaría disponible para todas las sedes. Esto evita la redundancia y la inconsistencia de datos.

I2: El SGBD controla el acceso simultáneo de varios usuarios y evita que dos personas puedan reservar la misma última plaza. Esto se consigue gracias al control de concurrencia.

I3: Los datos estarían almacenados en una misma base de datos y con un formato común. Así se podrían realizar consultas sobre las tres sedes sin tener que crear un programa nuevo cada vez. La ventaja es la facilidad para acceder y consultar los datos.

I4: El SGBD permite establecer permisos diferentes para cada usuario. Por ejemplo, los monitores podrían consultar las clases sin tener acceso a los IBAN de los socios. Esto mejora la seguridad de los datos.

I5: Se pueden establecer relaciones entre las tablas y restricciones de integridad. De esta forma, no se podría crear una reserva para un socio que no existe en SOCIOS. Esto garantiza la integridad de los datos.

I6: Los programas trabajan con la base de datos en lugar de depender directamente de la estructura de los ficheros. Por ello, cambiar la longitud de un campo como TELÉFONO no tendría por qué romper el programa de recibos. Esto reduce la dependencia entre los programas y los datos.

I7: El precio de cada tarifa se puede guardar en un único lugar. Por ejemplo, la tarifa Básica tendría un precio concreto y todos los socios que la tengan utilizarían ese precio. Esto evita la redundancia y las inconsistencias.

**2.2.** La gerente se pregunta si el cambio "merece la pena". Analiza qué **inconvenientes** tendrá la implantación de un SGBD **para esta empresa en concreto** y emite una recomendación razonada.

La implantación de un SGBD tendrá algunos inconvenientes. La empresa tendrá que pagar la instalación, configuración y mantenimiento del sistema y posiblemente también la formación de los trabajadores. Además, habrá que migrar los datos actuales de las tres sedes y unificar sus formatos. También será necesario hacer copias de seguridad y mantener el sistema para evitar problemas.

Aun así, creo que para Centros Deportivos Atlántico sí merece la pena. Actualmente ya tienen problemas de datos repetidos, reservas simultáneas, falta de seguridad y diferentes formatos entre sedes. Además, tienen previsto pasar de 3 a 20 sedes y aumentar hasta unos 15.000 socios. Por tanto, las ventajas de un SGBD serán mayores que sus inconvenientes y facilitarán el crecimiento de la empresa.

**2.3.** Un monitor que trabaja como entrenador personal por su cuenta, con 12 clientes, guarda en un fichero de texto la fecha y el tipo de sesión de cada cliente. ¿Le recomendarías un SGBD? Justifica tu respuesta comparándola con la de Centros Deportivos Atlántico.

En el caso del monitor con 12 clientes no recomendaría instalar un SGBD. Tiene pocos clientes y solo necesita guardar la fecha y el tipo de sesión, por lo que un fichero de texto puede ser suficiente y más sencillo de mantener.

En cambio, Centros Deportivos Atlántico tiene unos 1.800 socios, varias sedes, muchos usuarios y reservas simultáneas. Además, quiere crecer hasta 20 sedes y unos 15.000 socios. Por eso, en este caso un SGBD sí está justificado.

---

### Actividad 3. Elementos de un SGBD · RA1.e

**3.1.** Una vez implantado el SGBD, se producen las situaciones siguientes. Para cada una, indica **qué elemento del SGBD interviene** (núcleo, DDL, DML, DCL, utilidades o diccionario de datos), **qué tipo de usuario la realiza** (administrador de datos, administrador de la base de datos, programador de aplicaciones, usuario final o ninguno si es automática) y **justifica** brevemente tu respuesta.

| Nº | Situación | Elemento del SGBD | Tipo de usuario | Justificación |
|---|---|---|---|---|
| 1 | La gerente decide que a partir de ahora se registrará un teléfono de emergencia de cada socio. El cambio se aplicará modificando la estructura de la tabla `SOCIOS`. | **DDL** | **Administrador de datos** | Se modifica la estructura de la base de datos añadiendo un nuevo campo a la tabla `SOCIOS`. |
| 2 | El técnico ejecuta `CREATE TABLE RESERVAS (...)`. | **DDL** | **Administrador de la base de datos** | `CREATE TABLE` es una instrucción DDL que permite crear una nueva tabla en la base de datos. |
| 3 | Una recepcionista consulta, desde el programa de recepción, qué clases del jueves tienen plazas libres. | **DML** | **Usuario final** | La recepcionista realiza una consulta para obtener información almacenada en la base de datos. |
| 4 | Se ejecuta `GRANT SELECT ON CLASES TO monitores;` | **DCL** | **Administrador de la base de datos** | `GRANT` sirve para conceder permisos de acceso a los usuarios sobre los datos. |
| 5 | El SGBD rechaza una reserva porque el número de socio no existe. | **Núcleo** | **Ninguno** | El núcleo del SGBD comprueba automáticamente las restricciones de integridad y rechaza una operación que no las cumple. |
| 6 | Dos recepcionistas intentan asignar a la vez la última plaza de Spinning; el SGBD solo acepta una de las dos operaciones. | **Núcleo** | **Ninguno** | El núcleo controla la concurrencia y las transacciones para evitar que dos operaciones simultáneas produzcan un conflicto. |
| 7 | El técnico consulta qué tablas existen, qué campos tienen y qué usuarios tienen permisos sobre ellas. | **Diccionario de datos** | **Administrador de la base de datos** | El diccionario de datos almacena información sobre la estructura de la base de datos y los permisos de los usuarios. |
| 8 | Administración genera el informe mensual de cuotas con un asistente gráfico, sin escribir código. | **Utilidades** | **Usuario final** | Utiliza una herramienta del SGBD que permite generar informes mediante un asistente, sin necesidad de escribir instrucciones. |
| 9 | Se cargan en la nueva base de datos los ficheros antiguos de las tres sedes. | **Utilidades** | **Administrador de la base de datos** | Las utilidades del SGBD permiten realizar tareas de carga, importación y migración de datos. |
| 10 | La empresa de desarrollo programa la pantalla de reservas de la app, que resta una plaza libre cada vez que un socio reserva. | **DML** | **Programador de aplicaciones** | El programador desarrolla una aplicación que modifica los datos de la base de datos al realizar una reserva. |

**3.2.** Analiza los cambios siguientes. Para cada uno, indica **qué nivel de la arquitectura** de la base de datos se modifica (interno, conceptual o externo), **qué tipo de independencia** de datos interviene (si procede) y **qué programas o usuarios se ven afectados**.

| Cambio | Nivel modificado | Independencia | ¿A quién afecta? |
|---|---|---|---|
| a) El técnico reorganiza el almacenamiento de `SOCIOS` y crea un índice sobre el DNI para acelerar las búsquedas. | interno | física | Nada se ve afectado  |
| b) Se añade el campo `TELEFONO_EMERGENCIA` a `SOCIOS`. | Conceptual | Lógica | |
| c) Se crea una vista para los monitores que muestra solo el nombre del socio y sus clases. | Externo | Lógica | Sólo afecta a los monitores  |
| d) Se elimina el campo `FAX` de `SOCIOS`, que solo usaba el antiguo programa de envío de cartas. | Conceptual | Lógica | Afecta al antiguo programa |

Por último, compara el cambio *b* con la incidencia **I6** y explica qué ha cambiado gracias al SGBD.

En I6, al ampliar el campo TELÉFONO, el programa de recibos dejó de funcionar. Esto muestra que el programa dependía de la estructura de los datos.

En el cambio b, se añade TELEFONO_EMERGENCIA a SOCIOS. Gracias al SGBD y a la arquitectura de tres niveles, este cambio puede hacerse sin afectar necesariamente a los programas que no utilizan ese nuevo campo.

En decir el SGBD permite que los cambios en la estructura de los datos afecten lo menos posible a los programas. Esto es la independencia de datos.

---

### Actividad 4. Modelos de datos · RA1.b 

Utiliza los datos de reservas de la sede de Cádiz (excluyendo la reserva errónea de C-999):

- Lucía Ramos → Pilates y Spinning.
- Pedro Díaz → Spinning.
- Ana Torres → Pilates y Yoga.

**4.1.** **Modelo jerárquico.** Representa la información en forma de árbol, tomando como raíz la *Sede Cádiz*, después las *clases* y, por debajo, los *socios*. Indica qué datos aparecen **duplicados** y explica por qué este modelo obliga a ello.

Sede Cádiz
│
├── Pilates
│   ├── Lucía Ramos
│   └── Ana Torres
│
├── Spinning
│   ├── Lucía Ramos
│   └── Pedro Díaz
│
└── Yoga
    └── Ana Torres

Datos duplicados:
- Lucía Ramos aparece dos veces: Pilates y Spinning.
- Ana Torres aparece dos veces: Pilates y Yoga.
Esto ocurre porque en el modelo jerárquico cada elemento solo puede tener un padre. Como un socio puede estar apuntado a varias clases, hay que repetir sus datos debajo de cada clase.

**4.2.** **Modelo en red.** Representa la misma información como red. Señala qué nodos tienen **más de un padre** y explica qué ventaja supone respecto al modelo jerárquico.

                 Sede Cádiz
                     │
        ┌────────────┼────────────┐
        │            │            │
     Pilates      Spinning       Yoga
        │          /     \          │
        │         /       \         │
    Lucía ───────┘         Pedro    │
        │                           │
        └────────────────────── Ana ┘

Pilates ─── Lucía Ramos
         └─ Ana Torres

Spinning ── Lucía Ramos
          └ Pedro Díaz

Yoga ────── Ana Torres

La ventaja frente al modelo jerárquico es que un elemento puede tener varios padres, por lo que no es necesario duplicar los datos de los socios.     

**4.3.** **Modelo relacional.**

SOCIOS

| ID_SOCIO | NOMBRE |
|---|---|
| 1 | Lucía Ramos |
| 2 | Pedro Díaz |
| 3 | Ana Torres |

CLASES

| ID_CLASE | CLASE |
|---|---|
| 1 | Pilates |
| 2 | Spinning |
| 3 | Yoga |

RESERVAS

| ID_SOCIO | ID_CLASE |
|---|---|
| 1 | 1 |
| 1 | 2 |
| 2 | 2 |
| 3 | 1 |
| 3 | 3 |

Así, Lucía y Ana no necesitan aparecer repetidas en la tabla de socios. La tabla RESERVAS relaciona cada socio con las clases que tiene reservadas.

- **a)** Diseña las tablas `SOCIOS`, `CLASES` y `RESERVAS` con sus campos e indica la **clave primaria** y las **claves externas** de cada una.

SOCIOS

| Campo | Clave |
|---|---|
| `ID_SOCIO` | **Clave primaria (PK)** |
| `NOMBRE` | — |

CLASES

| Campo | Clave |
|---|---|
| `ID_CLASE` | **Clave primaria (PK)** |
| `NOMBRE_CLASE` | — |

RESERVAS

| Campo | Clave |
|---|---|
| `ID_SOCIO` | **Clave externa (FK)** |
| `ID_CLASE` | **Clave externa (FK)** |
| `ID_SOCIO + ID_CLASE` | **Clave primaria (PK)** |


- **b)** Rellena las tres tablas con los datos anteriores.

SOCIOS

| ID_SOCIO | NOMBRE |
|---|---|
| 1 | Lucía Ramos |
| 2 | Pedro Díaz |
| 3 | Ana Torres |

CLASES

| ID_CLASE | NOMBRE_CLASE |
|---|---|
| 1 | Pilates |
| 2 | Spinning |
| 3 | Yoga |

RESERVAS

| ID_SOCIO | ID_CLASE |
|---|---|
| 1 | 1 |
| 1 | 2 |
| 2 | 2 |
| 3 | 1 |
| 3 | 3 |

- **c)** Explica por qué es necesaria la tabla `RESERVAS` y por qué en ella un mismo valor de clave externa puede repetirse.

La tabla RESERVAS es necesaria para relacionar a los socios con las clases, ya que un socio puede reservar varias clases y una clase puede tener varios socios.
Un mismo valor de clave externa puede repetirse porque, por ejemplo, Lucía Ramos puede tener varias reservas. Su ID_SOCIO aparecerá varias veces en RESERVAS, una por cada clase que reserve.

**4.4.** Justifica cuál de los tres modelos es el adecuado para Centros Deportivos Atlántico. Indica además **una parte del sistema** de la empresa (actual o futura) en la que una estructura jerárquica sí tendría sentido y por qué.

El modelo relacional es el más adecuado para Centros Deportivos Atlántico porque permite relacionar fácilmente socios, clases y reservas sin tener que repetir información. Además, facilita consultar y modificar los datos.
Una estructura jerárquica sí tendría sentido, por ejemplo, para organizar las sedes y sus departamentos.
Tiene sentido porque cada departamento pertenece a una única sede, formando una estructura de tipo padre-hijo.

---

### Actividad 5. Clasificación de los sistemas gestores · RA1.f 

**5.1.** Clasifica los siguientes sistemas completando la tabla. Si un sistema **no es un SGBD**, indícalo y explica el motivo.

| Sistema | ¿Es un SGBD? | Modelo de datos | Ubicación de la información | Usuarios | Configuración |
|---|---|---|---|---|---|
| A. Sistema actual de cada sede, con ficheros en el ordenador de recepción. | No | Ficheros | Centralizada en cada ordenador | Uno | Monoequipo |
| B. SQLite instalado en un portátil para gestionar clientes. | Sí | Relacional | Centralizada | Uno | Monoequipo |
| C. SGBD jerárquico similar a IBM IMS, en un servidor central con varios terminales. | Sí | Jerárquico | Centralizada | Varios simultáneos | Cliente-servidor |
| D. MySQL en un servidor de Cádiz al que se conectan las tres sedes. | Sí | Relacional | Centralizada | Varios simultáneos | Cliente-servidor |
| E. App móvil → servidor de aplicaciones → PostgreSQL. | Sí | Relacional | Centralizada | Varios simultáneos | Con servidor de aplicaciones |
| F. Cada zona tiene su propio servidor PostgreSQL y todos funcionan como una única base de datos. | Sí | Relacional | Distribuida | Varios simultáneos | Distribuida |

**5.2.** Los ficheros de las tres sedes ya están repartidos en tres ordenadores distintos. ¿Puede considerarse el sistema actual una **base de datos distribuida**? Justifica tu respuesta.

Aunque los datos están repartidos entre tres ordenadores distintos, simplemente son ficheros independientes de cada sede. No existe un SGBD que gestione esos datos como una única base de datos ni que permita trabajar con ellos de forma conjunta.
Por tanto, es un sistema de ficheros independientes, no una base de datos distribuida.

---

### Actividad 6. Ubicación de la información y bases de datos distribuidas · RA1.c · RA1.g

**6.1.** Para afrontar la expansión a 20 sedes, el técnico plantea cuatro opciones. Completa la tabla **aplicándola al caso**:

| Opción | ¿Dónde se encuentra físicamente la información? | Ventaja principal para Atlántico | Inconveniente principal para Atlántico |
|---|---|---|---|
| 1. Cada sede con su propio SGBD en el ordenador de recepción (monoequipo). | En el ordenador de cada una de las 20 sedes. | Es sencilla y barata de instalar y mantener en cada sede. | La información queda separada y es difícil tener una visión conjunta de las 20 sedes. |
| 2. Un único servidor central en Cádiz al que se conectan todas las sedes (cliente-servidor). | En un único servidor situado en Cádiz. | Todos los datos están centralizados y todas las sedes pueden acceder a la misma información. | Si el servidor o la conexión con Cádiz falla, puede afectar al acceso de todas las sedes. |
| 3. Un servidor en cada zona (Cádiz, Sevilla y Málaga) formando una base de datos distribuida. | Repartida entre los servidores de Cádiz, Sevilla y Málaga. | Reparte la carga y permite que cada zona tenga sus datos más cerca, manteniendo el sistema como una única BD. | Es más compleja y cara de administrar y mantener. |
| 4. Cualquiera de las anteriores con un servidor de aplicaciones intermedio para la app móvil. | La información sigue estando donde corresponda según la opción elegida; el servidor de aplicaciones se sitúa entre la app y el SGBD. | Aumenta la seguridad y permite que la app móvil acceda a los datos sin conectarse directamente al SGBD. | Añade otro componente que hay que mantener y puede aumentar la complejidad del sistema. |

**6.2.** Describe, paso a paso, qué ocurre desde que una socia pulsa *Reservar* en la app hasta que recibe la confirmación. Indica en qué **capa** (presentación, lógica o datos) se produce cada paso y en qué capa debe comprobarse que quedan plazas libres. Justifica esto último.

1. **La socia pulsa el botón “Reservar” en la app.**  
   → **Capa de presentación.** La app recoge la acción de la usuaria y envía la petición.

2. **La petición llega al servidor de aplicaciones.**  
   → **Capa de lógica.** El servidor recibe la solicitud y comprueba qué reserva se quiere realizar.

3. **La lógica solicita a la base de datos las plazas disponibles de la clase.**  
   → **Capa de datos.** El SGBD consulta la información de la clase y devuelve las plazas disponibles.

4. **Se comprueba que todavía queda alguna plaza libre.**  
   → **Capa de lógica.** Aquí debe comprobarse que la plaza está disponible antes de confirmar la reserva.

5. **Si hay plaza, se registra la reserva y se actualiza el número de plazas disponibles.**  
   → **Capa de datos.** El SGBD modifica los datos de la reserva y de las plazas.

6. **El resultado vuelve al servidor de aplicaciones y después a la app.**  
   → **Capa de lógica → capa de presentación.** La aplicación recibe el resultado y muestra a la socia que la reserva se ha realizado correctamente.

**6.3.** Analiza cómo responderían la opción 2 (centralizada) y la opción 3 (distribuida) ante estas situaciones:

- **a)** Un lunes a las 19:00, hora punta, se produce un corte eléctrico en el edificio donde está el servidor de Cádiz.
Centralizada: Al estar toda la información en el servidor de Cádiz, todas las sedes perderían el acceso a la base de datos mientras el servidor esté apagado.
Distribuida: Si falla el servidor de Cádiz, Sevilla y Málaga podrían seguir funcionando con sus servidores locales, aunque algunas operaciones podrían verse afectadas si necesitan información que estaba en Cádiz.

- **b)** Lucía Ramos, con tarifa Multisede y dada de alta en Cádiz, reserva una clase en una sede de Málaga. Explica qué debe ocurrir para que la socia **perciba un único sistema** y qué dificultad técnica supone.
Centralizada: La sede de Málaga consulta directamente el servidor central de Cádiz, por lo que puede comprobar los datos de Lucía y realizar la reserva sobre la misma base de datos.
Distribuida: El sistema debe consultar y sincronizar los datos entre los servidores para comprobar que Lucía existe, que tiene tarifa Multisede y que puede reservar en Málaga.

**6.4.** Recomienda razonadamente una de las opciones para la empresa dentro de tres años, valorando tanto sus ventajas como sus inconvenientes.
Recomendaría la opción 3, distribuida, porque con 20 sedes sería más segura y permitiría que un problema en un servidor no afectase a toda la empresa. Aunque es más cara y complicada de mantener, creo que para una empresa que está creciendo compensa.

---

### Actividad 7. Reparto de la información entre servidores (fragmentación) · RA1.h

Cuando se elige una base de datos distribuida, hay que decidir **qué parte de la información se guarda en cada servidor**. A esta división se la denomina **fragmentación**, y puede hacerse de dos formas:

- **Repartir registros (filas)** de una tabla según un criterio, como en el ejemplo de Netflix de la unidad, donde cada servidor regional guarda los datos de los usuarios de su zona.
- **Repartir campos (columnas)** de una misma tabla en servidores distintos, de modo que cada servidor guarda solo una parte de la información de cada registro.

Además, algunas tablas pueden **replicarse**, es decir, guardarse **completas en todos los servidores**.

Tras la expansión, la tabla `SOCIOS` tendría este aspecto (extracto):

| Nº_SOCIO | DNI | NOMBRE | SEDE_ALTA | ZONA | TELÉFONO | IBAN | TARIFA | CUOTA |
|---|---|---|---|---|---|---|---|---|
| CA-014 | 31234567A | Lucía Ramos | Cádiz | Cádiz | 600111222 | ES12 **** 3456 | Multisede | 45 € |
| CA-015 | 44556677B | Pedro Díaz | Jerez | Cádiz | 600333444 | ES98 **** 1122 | Básica | 30 € |
| SE-201 | 12345678D | Javier Ruiz | Sevilla Nervión | Sevilla | 611222333 | ES33 **** 9900 | Premium | 55 € |
| SE-202 | 23456789E | Elena Mena | Dos Hermanas | Sevilla | 622333444 | ES71 **** 4455 | Básica | 30 € |
| MA-301 | 34567890F | Carmen Soto | Málaga Centro | Málaga | 633444555 | ES20 **** 6677 | Multisede | 45 € |
| MA-302 | 45678901G | Luis Peña | Marbella | Málaga | 644555666 | ES88 **** 2211 | Básica | 30 € |

**7.1.** Propón cómo repartir las tablas `SOCIOS`, `CLASES`, `RESERVAS` y `TARIFAS` entre los tres servidores de zona. Para cada tabla indica si la **fragmentarías por registros** (y con qué criterio) o si la **replicarías**, y justifica la decisión pensando en qué datos consulta cada sede con más frecuencia.

**7.2.** Aplica tu criterio al extracto anterior: indica qué registros de `SOCIOS` se almacenarían en cada servidor. Comprueba que ningún registro se pierde ni aparece en dos fragmentos.

**7.3.** El técnico propone además **separar por campos** la tabla `SOCIOS`: los datos bancarios y de cuota se guardarían en un servidor de administración especialmente protegido, y el resto en los servidores de zona.

- **a)** Indica qué campos tendría cada fragmento.
- **b)** ¿Qué campo debe aparecer **en ambos fragmentos** y por qué?
- **c)** Explica qué ventaja aporta esta separación en relación con la incidencia **I4**.

**7.4.** Con tu propuesta, ¿en qué servidor quedaría registrada la reserva que Lucía Ramos (Cádiz, Multisede) hace en Málaga? Analiza qué problema plantea y propón una solución.

---

### Actividad 8. Protección de datos · RA1.i

**8.1.** A partir de los campos de la tabla `SOCIOS`, identifica qué datos son **de carácter personal** e indica cuáles consideras **más delicados** y por qué.

**8.2.** Indica qué **normativa europea** de protección de datos, citada en los materiales de la unidad, debe cumplir Centros Deportivos Atlántico, y explica **con tus palabras** por qué le afecta.

**8.3.** Propón **al menos cuatro medidas técnicas** para proteger los datos de los socios, basadas en los contenidos de la unidad. Al menos una debe resolver la incidencia **I4** y otra debe aplicarse a la app móvil.

| Medida | Concepto de la unidad en el que se basa | Riesgo que evita en Atlántico |
|---|---|---|
| | | |

Incluye en una de las medidas la **sentencia DCL** que utilizarías, siguiendo el ejemplo de la unidad.

---

### Actividad 9. Análisis de datos para la toma de decisiones · RA1.j

En la unidad se han visto plataformas que guardan datos para **analizarlos**: el *microservicio Analytics* con su propia base de datos, los *historiales de visualización* o los *algoritmos de recomendación* de una plataforma de *streaming*.

- Utilizar los datos acumulados de una empresa para **apoyar la toma de decisiones** se denomina **inteligencia de negocio** (*Business Intelligence*, BI).
- Cuando el **volumen** de datos es tan grande, se genera **tan rápido** o es **tan variado** que las herramientas tradicionales no bastan para procesarlo, se habla de **Big Data**.

**9.1.** Dentro de tres años habrá unos 15.000 socios que, de media, realizan 3 reservas por semana. Calcula **cuántas reservas se registrarán al año** y cuántas se acumularán en los tres años. Compara esa cifra con el sistema actual de ficheros y razona si podría gestionarla.

**9.2.** Plantea **tres preguntas de negocio** que la gerente podría responder analizando el histórico. Para cada una, indica **qué tablas y campos** necesitaría y **qué decisión** permitiría tomar.

| Pregunta de negocio | Tablas y campos necesarios | Decisión que permite tomar |
|---|---|---|
| | | |

**9.3.** Siguiendo el ejemplo de los microservicios de la unidad, el técnico propone guardar los datos de análisis en una **base de datos separada** de la que usan la recepción y la app para las reservas. Explica por qué es una buena decisión, relacionándola con algún inconveniente de la arquitectura cliente-servidor visto en la unidad.

---

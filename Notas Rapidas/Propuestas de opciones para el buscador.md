# Opciones
Ideas generales de flujo de trabajo:
```mermaid
graph TD
    A[Texto Natural a Consultas] --> B{Opciones}
    
    %% Opción 1: PHP + OpenAI
    B -->|Opción 1| C1[PHP + OpenAI API]
    C1 --> D1[Procesar con PHP]
    D1 --> E1[Enviar a OpenAI API]
    E1 --> F1[Schema + Query → OpenAI]
    F1 --> G1[Recibir SQL generado]
    G1 --> H1[Ejecutar en MySQL]
    H1 --> I1[Retornar Resultados]
    
    %% Opción 2: PHP Puro
    B -->|Opción 2| C2[PHP Puro + Patrones]
    C2 --> D2[Correccion con Busqueda Difusa]
    D2 --> E2[Análisis de Patrones/Regex]
    E2 --> F2[Mapeo de Campos]
    F2 --> G2[Construcción SQL]
    G2 --> H2[Ejecutar en MySQL]
    H2 --> I2[Retornar Resultados]
    
    %% Opción 3: PHP + Python
    B -->|Opción 3| C3[PHP + spaCy/Python]
    C3 --> D3[PHP recibe request]
    D3 --> E3[Enviar a Microservicio Python]
    E3 --> F3[spaCy procesa NLP]
    F3 --> G3[Python retorna estructura]
    G3 --> H3[PHP construye SQL]
    H3 --> I3[Ejecutar en MySQL]
    I3 --> J3[Retornar Resultados]
    
    %% Opción 4: PHP + Elasticsearch
    B -->|Opción 4| C4[PHP + Elasticsearch]
    C4 --> D4[Indexar campos en ES]
    D4 --> E4[Procesar consulta natural]
    E4 --> F4[Generar query Elasticsearch]
    F4 --> G4[Traducir ES query a SQL]
    G4 --> H4[Ejecutar en MySQL]
    H4 --> I4[Retornar Resultados]
    
    %% Opción 5: PHP + Base Conocimiento
    B -->|Opción 5| C6[PHP + Base Conocimiento Local]
    C6 --> D6[Cargar mapas semánticos]
    D6 --> E6[Tokenización y scoring]
    E6 --> F6[Mapeo por patrones]
    F6 --> G6[Construcción SQL]
    G6 --> H6[Ejecutar en MySQL]
    H6 --> I6[Retornar Resultados]
    
    %% Base de datos común
    H1 --> Z[(MySQL Database)]
    H2 --> Z
    I3 --> Z
    H4 --> Z
    H6 --> Z
    
    %% Servicios externos
    E1 -.->|API Call| X1[OpenAI Service]
    E3 -.->|HTTP Request| X2[Python Microservice]
    F4 -.->|Query| X3[Elasticsearch Cluster]
    
    %% Estilos
    classDef phpNode fill:#8b5cf6,stroke:#7c3aed,stroke-width:2px,color:#fff
    classDef externalService fill:#f59e0b,stroke:#d97706,stroke-width:2px,color:#fff
    classDef database fill:#10b981,stroke:#059669,stroke-width:2px,color:#fff
    classDef decision fill:#ef4444,stroke:#dc2626,stroke-width:2px,color:#fff
    
    class C1,C2,C3,C4,C5,C6,D1,D2,D3,D4,D5,D6,E2,F2,G2,G3,G5,G6,H1,H2,H3,H4,H5,H6 phpNode
    class X1,X2,X3,X4 externalService
    class Z database
    class B decision
```

## Opcion 1: PHP + OpenAI API
Proceso general:
```mermaid
---

config:

layout: dagre

---

flowchart TD

A["Entrada de Usuario<br>Texto Natural"] --> B["Validación y Sanitización<br>de Entrada"]

B --> C["Preparación del Prompt<br>Sistema + Contexto"]

C --> D["Llamada a OpenAI API"]

D --> E{"Respuesta<br>Válida?"}

E -- No --> F["Manejo de Errores"]

F --> G["Respuesta de Error<br>al Usuario"]

E -- Sí --> H["Consulta Generada"]

K{"Consulta Valida"} -- No --> F

K -- Sí --> M["Ejecutar Consulta"]

M --> N["Optimización de Consulta"]

N --> O["Ejecucion de Consulta"]

AA["Esquema de Base<br>Metadatos para Context"] -.-> C

H --> n2["Validador SQL"]

n2 --> n3["Validaciones"] & n4["Permisos"] & n5["Optimizacion"]

n3 --> K

n4 --> K

n5 --> K

O --> n6["Ejecucion Exitosa"]

n6 -- No --> n7["Manejador de Errores"]

n6 --> n8["Procesar Resultado"]

n8 --> n9["Respuesta al Usuario"] & n10["Historial de Busqueda"]

n9 --> n11["Presentar Resultados"]

n10 --> n11

n11 --> n12["Fin"]

n6@{ shape: diam}

style F fill:#FFCDD2

style H fill:#C8E6C9

style M fill:#C8E6C9

style n7 fill:#FFCDD2

style n8 fill:#C8E6C9
```
### Consideraciones:
- Seguridad:
	- Implementacion de white list de comandos.
	- Uso de usuario con permiso a solo consultas.
	- Usar consultas preparadas para evitar inyecciones SQL.
- Logs:
	- Errores de consultas con el prompt y la consulta creada.
	- Medicion de operaciones.
- Costos(aproximados o estimados):
	- GPT-4o:
		- $5 USD por 1M tokens de entrada
		- $20 USD por 1M tokens de salida
	- GPT-4mini:
		- $0.15 USD por 1M tokens de entrada
		- $0.60 USD por 1M tokens de salida
	- Estimacion de tokens por consulta:
		- Prompt + Esquema DB : ~500 tokens
		- Busqueda de Usuario: ~50 - 200 tokens
		- Respuesta estructurada: ~100 - 300 tokens
		- Total: ~650 - 1000 tokens por consulta
Suponiendo que se realizan 100 consultas por dia:
- GPT4o: $19-30 USD por mes
- GPT4o mini: $0.60 - $0.90 USD por mes

### Pros
- Flexibilidad: Maneja variaciones naturales del lenguaje de forma robusta
- Comprension Contextual: Entiende intenciones complejas y mejor manejo de ambigüedades en las busquedas
- Mantenimiento: menos mantenimiento
- Capacidades avanzadas: Puede sugerir alternativas, reformular consultas y optimizarlas
### Contras
- Costos: Cada consulta tiene un costo en tokens, puede ser significativo dependiendo del numero de consultas
- Dependencia externa: Requiere conexion a interner y disponibilidad del servicio de la API de OpenAI
- Latencia: Las llamadas a la API pueden tener mayor tiempo de respuesta dependiendo de la conexion
- Menor control: si no se controla el prompt puede generar respuestas impredecibles
- Complejidad en el manejo de respuesta: manejo de errores para validar respuestas no validas
### Opción 2: PHP + Patrones
Proceso general:
```mermaid
---

config:

layout: dagre

---

flowchart TD

A["Consulta Natural"] --> B["PreProcesamiento"]

B --> B1["Limpieza de Texto"] & B2["Normalización"] & B4["Tokenización"]

B1 --> B5["Búsqueda Difusa y Corrección"]

B2 --> B5

B4 --> B5

B5 --> B51["Detección de Errores Ortográficos"] & B52["Distancia de Levenshtein"] & B53["Diccionario de Términos BD"] & B54["Algoritmos de Similaridad"]

B51 --> BX{"¿Errores Detectados?"}

B52 --> BX

B53 --> BX

B54 --> BX

BX -- "Sí - Auto-corregible" --> B55["Corrección Automática"]

BX -- "Sí - Requiere confirmación" --> B56["Sugerencias Interactivas"]

BX -- No --> C["Análisis Contextual"]

B55 --> BY["Aplicar Correcciones"]

B56 --> BZ["Mostrar Sugerencias al Usuario"]

BY --> C

BZ --> BW["Confirmación Usuario"]

BW --> BY

C --> C1["Carga de Esquema BD"] & C3["Metadatos de Tablas"] & C4["Relaciones FK"]

C1 --> D["Análisis Semántico"]

C3 --> D

C4 --> D

D --> D1["Reconocimiento de Entidades"] & D2["Detección de Intenciones"] & D3["Extracción de Parámetros"] & D4["Identificación de Ambigüedades"]

D1 --> E{"¿Ambigüedad Detectada?"}

D2 --> E

D3 --> E

D4 --> E

E -- Sí --> F["Solicitar Clarificación"]

F --> G["Entrada Usuario"]

G --> D

E -- No --> H["Descomposición en Bloques Lógicos"]

H --> H1["Intención Principal<br>SELECT"] & H2["Entidades Centrales<br>Tablas y Columnas"] & H3["Condiciones<br>WHERE, HAVING"] & H4["Agrupaciones<br>GROUP BY"] & H5["Ordenamiento<br>ORDER BY"] & H6["Límites<br>LIMIT, OFFSET"] & H7["Joins Necesarios<br>INNER/LEFT/RIGHT"] & H8["Funciones Agregadas<br>SUM, COUNT, AVG, etc."]

H1 --> I["Constructor SQL"]

H2 --> I

H3 --> I

H4 --> I

H5 --> I

H6 --> I

H7 --> I

H8 --> I

I --> I1["Generación de SELECT"] & I2["Construcción de FROM"] & I3["Ensamblaje de JOIN"] & I4["Construcción de WHERE"] & I5["Aplicación de GROUP BY"] & I6["Construcción de HAVING"] & I7["Aplicación de ORDER BY"] & I8["Aplicación de LIMIT"]

I1 --> J["Validador SQL"]

I2 --> J

I3 --> J

I4 --> J

I5 --> J

I6 --> J

I7 --> J

I8 --> J

J --> J1["Validación Sintáctica"] & J2["Validación Semántica"] & J3["Verificación de Permisos"] & J4["Optimización de Consulta"]

J1 --> K{"¿Consulta Válida?"}

J2 --> K

J3 --> K

J4 --> K

K -- No --> L["Generador de Errores"]

L --> L1["Identificación de Error"] & L2["Sugerencias de Corrección"]

L1 --> M["Retroalimentación al Usuario"]

L2 --> M

M --> N["¿Reintentar?"]

N -- Sí --> D

N -- No --> O["Fin"]

K -- Sí --> P["Consulta SQL Final"]

P --> Q["Ejecutor SQL"]

Q --> Q1["Ejecución Segura"] & Q2["Manejo de Timeouts"] & Q3["Control de Recursos"]

Q1 --> R{"¿Ejecución Exitosa?"}

Q2 --> R

Q3 --> R

R -- No --> S["Manejo de Errores de Ejecución"]

S --> S1["Log de Errores"] & S2["Mensaje Usuario"]

S1 --> T["Respuesta de Error"]

S2 --> T

R -- Sí --> U["Procesador de Resultados"]

U --> U1["Formateo de Datos"] & U2["Paginación"] & U3["Exportación"] & U4["Visualización"]

U1 --> V["Respuesta Final"]

U2 --> V

U3 --> V

U4 --> V

V --> W["Logger del Sistema"]

T --> W

W --> W1["Consulta Original"] & W2["SQL Generado"] & W3["Tiempo de Procesamiento"] & W4["Resultado/Error"]

W1 --> X["Mejoras"]

W2 --> X

W3 --> X

W4 --> X

X --> X1["Actualización de Patrones"] & X2["Optimización de Reglas"] & X3["Mejora de Precisión"]

style A fill:#e1f5fe

style E fill:#fff3e0

style K fill:#fff3e0

style P fill:#c8e6c9

style R fill:#fff3e0

style T fill:#ffcdd2

style V fill:#c8e6c919
```

### Componentes Principales:
- Busqueda Difusa
	- Resuelve problemas gramaticales
	- Corrige errores de escritura
- Analizador de Intenciones
	- Detecta el tipo de consulta(SELECT,WHERE,LIMIT,etc)
	- Extrae entidades y parametros
	- Detecta ambiguedad o contradicciones
- Constructor de Consultas
	- Crea la consulta a en base al Analizador de Intenciones
	- Verifica y valida Consultas
	- Ejecuta la Consulta.
- Logger
	- Errores
	- Consultas fallidas
	- Busquedas con consulta generada.
	- Base para mejoras en las reglas y diccionarios.

### Consideraciones:
Creación de diccionarios para optimización del Analizador
- Diccionario de Intenciones 
	- SELECT = "listame, quiero, dame, busco,etc"
	- WHERE = "donde,que,con,mayor que, entre"
- Diccionario de entidades
	- Campos = "usuario, area, producto, cliente"
- Diccionario de parametros
	- temporales = "mes pasado, este mes, entre la fecha, día"
	- tipo = "pdf,documento,facturas,etc"
- Diccionario de sinonimos
	- factura = "documento, cuenta,etc"
	- producto = "articulos, items, mercancias, etc"
El Analizador depende de los diccionarios o registros para su funcion y necesitan ser constantemente actualizados o mantenidos haciendo uso de los logs.

### Pros
- Arquitectura estructurada
- Control total y local
- Mantenibilidad Mejorada
- Rendimiento optimizado
- Seguridad Robusta
- Sin Costos
### Contras
- Trabajo Manual en construccion de diccionarios
- Dificultad con variaciones no previstas
- Crecimiento lento y manual, necesidad de acutalizar diccionarios manuelmente
- Complejidad

## Opcion 3: PHP + spaCy/Python
```mermaid
flowchart TD

A["Entrada de Texto del Usuario"] --> B["Preprocesamiento con spaCy"]

B --> C["Tokenización"] & D["Lemmatización"] & E["POS Tagging"] & F["Named Entity Recognition"] & G["Dependency Parsing"]

C --> H["Análisis Morfológico"]

D --> H

E --> H

F --> I["Extracción de Entidades"]

G --> J["Análisis Sintáctico"]

H --> K["Normalización de Tokens"]

I --> L["Clasificación de Entidades"]

J --> M["Identificación de Relaciones"]

K --> N["Filtrado de Stop Words"]

L --> O["Mapeo a Campos de BD"]

M --> P["Extracción de Patrones"]

N --> Q["Análisis de Intenciones"]

O --> Q

P --> Q

Q --> R{"Tipo de Consulta?"}

R -- Búsqueda por Contenido --> S["Procesamiento de Consulta de Contenido"]

R -- Búsqueda por Metadatos --> T["Procesamiento de Consulta de Metadatos"]

S --> V["Análisis de Términos de Búsqueda"]

T --> W["Mapeo de Entidades a Campos"]

V --> Y["Expansión Semántica con Word Vectors"]

W --> Z["Validación de Tipos de Datos"]

Y --> BB["Generación de Consulta Full-Text"]

Z --> CC["Construcción de WHERE Clauses"]

BB --> EE["Construcción de Consulta SQL"]

CC --> EE

EE --> YY{"Consulta Válida?"}

FF["Ejecución en MySQL"] --> GG["Resultados de BD"]

GG --> HH["Post-procesamiento con spaCy"]

HH --> II["Cálculo de Relevancia Semántica"]

II --> JJ["Ranking por Similarity Score"]

JJ --> KK["Agrupación por Tipo de Archivo"]

KK --> LL["Aplicación de Filtros Adicionales"]

LL --> MM["Resultados Finales"]

MM --> NN["API Respuesta"] & UU["Análisis de Resultados"]

OO["Modelo spaCy Entrenado"] --> Q

PP["Vectores de Palabras"] --> Y

QQ["Configuración de Entidades Personalizadas"] --> L

RR["Patrones de Intención"] --> Q

SS["Diccionario de Sinónimos"] --> Y

TT["Esquema de BD"] --> W

UU --> VV["Logging de Consultas"]

VV --> WW["Métricas de Rendimiento"]

WW --> XX["Retroalimentación para Mejoras"]

XX --> OO

YY -- No --> ZZ["Manejo de Errores"]

ZZ --> AAA["Sugerencias Alternativas"]

AAA --> BBB["Respuesta de Error Amigable"]

BBB --> n1["Fin"]

NN -- PHP recibe --> n2["Procesamiento de Respuesta"]

n2 --> n3["Presentacion de Resultado"]

n3 --> n4["Fin"]

YY -- Si --> FF

  

style ZZ fill:#FFCDD2
```

### Consideraciones
- Se necesita un servido o Microservicio dedicado a spaCy que procese la busqueda
- Agrega complejidad
- Se necesita mas configuraciones mas complejas
- Creación de codigo Python para manejar las solicitudes
- Mantenimiento de codigo extra

### Pros
- Robusto: Gran manejo de lenguaje natutal
- Mayor Comprension: Entiende contextos y relaciones semanticas
- Escalable: Se adapta a nuevas formas de expresion en busquedas automaticamente
### Contras
- Complejidad alta: integracion del servicio, configuracion y crear una API para conexion con PHP
- Recursos: mayor consumo de recursos de CPU y memoria
- Dependencia: Se requiere mantener y verificar el entorno de Python, se depende que este funcione
- Configuracion: Configuracion compleja de infraestructura y personalizacion
## Opcion 4: PHP + Elasticsearch
```mermaid
flowchart TD

subgraph ES["Elasticsearch - Procesamiento Interno"]

direction TB

G2["Analyzer Pipeline"]

G1["Query Parser"]

G3["Tokenización"]

G4["Normalización"]

G5["Filtros de idioma"]

G6["Stemming"]

G7["Sinónimos automáticos"]

G8["Scoring Algorithm"]

G9["Index Search"]

G10["Relevance Ranking"]

G11["Aggregations"]

G12["Result Formatting"]

end

subgraph DF["Flujo de Datos"]

direction TB

DF2["ETL Process<br>Sincronización periódica"]

DF1["Base de Datos MySQL<br>Metadatos de archivos"]

DF3["Elasticsearch Index<br>Documentos indexados"]

DF4["Mapping Configuration<br>Tipos de campos y analyzers"]

DF5["Index Templates<br>Configuración automática"]

end

subgraph QC["Construcción de Consultas"]

direction TB

QC2["Bool Query<br>Combinación de condiciones"]

QC1["Multi-Match Query<br>Búsqueda en múltiples campos"]

QC3["Function Score<br>Modificación de relevancia"]

QC4["Fuzzy Matching<br>Tolerancia a errores"]

QC5["Phrase Matching<br>Búsqueda de frases exactas"]

QC6["Wildcard/Regex<br>Patrones avanzados"]

QC7["Aggregations<br>Facetas y estadísticas"]

QC8["Highlighting<br>Resaltado de términos"]

end

A["Usuario ingresa consulta en lenguaje natural"] --> B["Recepción en Frontend PHP"]

B --> C{"Validación y sanitización<br>de entrada"}

C -- Inválida --> D["Retornar error"]

C -- Válida --> E["Preprocesamiento básico"]

E --> F["Construcción de consulta<br>Elasticsearch"]

F --> G["Envío a Elasticsearch API"]

G --> H{"Respuesta de<br>Elasticsearch"}

H -- Error --> I["Manejo de errores<br>Log del error"]

H -- Éxito --> J["Procesamiento de resultados"]

J --> K["Formateo de respuesta"]

K --> L["Retorno al usuario"]

I --> M["Consulta de fallback<br>o sugerencias"]

M --> L

G1 --> G2

G2 --> G3

G3 --> G4

G4 --> G5

G5 --> G6

G6 --> G7

G7 --> G8

G8 --> G9

G9 --> G10

G10 --> G11

G11 --> G12

DF1 --> DF2

DF2 --> DF3

DF3 --> DF4

DF4 --> DF5

QC1 --> QC2

QC2 --> QC3

QC3 --> QC4

QC4 --> QC5

QC5 --> QC6

QC6 --> QC7

QC7 --> QC8

F -.-> ES & QC

G -.-> DF3

DF1 -.-> DF2

L --> n1["Fin"]

  

A:::userFlow

B:::userFlow

C:::userFlow

D:::userFlow

E:::userFlow

F:::userFlow

G:::userFlow

H:::userFlow

I:::userFlow

J:::userFlow

K:::userFlow

L:::userFlow

M:::userFlow

ES:::processing

QC:::elasticsearch

classDef userFlow fill:#e1f5fe

classDef processing fill:#f3e5f5

classDef elasticsearch fill:#fff3e0

classDef config fill:#e8f5e8

classDef advanced fill:#fce4ec

style A fill:transparent

style B fill:transparent

style C fill:transparent

style D fill:#FFCDD2

style E fill:#C8E6C9

style F fill:transparent

style G fill:transparent

style H fill:transparent

style I fill:#FFCDD2

style J fill:#C8E6C9

style K fill:transparent

style L fill:transparent

style M fill:transparent

style n1 fill:transparent
```

### Concideraciones
- Infraestructura adicional, se tiene que agregar el servicio de Elasticsearch
- Buen escalado pero agrega costo de rendimiento para consultas simples o peticiones bajas
- Se necesita indexar las tablas de la base de datos a Elasticsearch
- Para indexar debe ser de forma manual y actualizarse con cada nuevo registro en la base

### Pros
- Potencia: maneja de forma automatica tokenizacion, stemming, sinonimos, busqueda difusa y scoring
- Escalabilidad: diseñado para grandes volumenes de datos y consultas concurrentes
- Flexibilidad: maneja multiples idiomas y variaciones naturales de texto
- Catacteristicas avanzadas:  autocompletado, correcciòn ortografica, búsqueda semántica, etc.
### Contras
- Complejidad en la infraestructura: requiere instalar, configurar y mantener el servicio 
- Aprendizaje: se necesita aprender conceptos de elasticsearch como mappings, analyzers, queries DSL, etc
- Recursos: consume mas memoria  y CPU que mysql
- Sincronizacion: se necesita mantener los datos sincronizados entre mysql y elasticsearch de forma constante
- Costo: en caso de necesitar licencia empresarial, aunque este caso puede no ser necesario

## Opcion 5: PHP + Base de Conocimiento Local
```mermaid
---

config:

layout: dagre

look: neo

---

flowchart TB

A["Consulta Natural"] --> n1["Cargar Base de Conocimiento"]

n1 --> n2["Normalizar Consulta"]

n2 --> n3["Tokenizar Consulta"]

n3 --> n4["Calcular Scores por Patron"]

n4 --> n5["Identificar Mejor Coincidencia"]

n5 --> n6["Score Supera Valor Minimo"]

n6 -- No --> n7["Consulta No Reconocida"]

n6 --> n8["Mapear Token a Elementos"]

n7 --> n9["Sugerir Patron mas Similar"]

n8 --> n10["Aplicar Patron SQL"]

n10 --> n11["Sustituir Valores en Patron"]

n11 --> n12["Validar Consulta SQL"]

n9 --> n13["Acepta Patron"]

n13 -- No --> n14["Fin"]

n13 -- Si --> n8

n12 --> n15["Consulta Valida"]

n15 -- Si --> n16["Ejecutar Consulta"]

n15 -- No --> n17["Manejador de Errores"]

n17 --> n18["Retornoar Resultado"]

n18 --> n19["Fin"]

n16 --> n20["Ejecucion Exitosa"]

n20 -- No --> n17

n20 -- Si --> n21["Procesar Resultado"]

n21 --> n22["Retornar Resultado"]

n22 --> n19

n6@{ shape: diam}

n13@{ shape: diam}

n15@{ shape: diam}

n20@{ shape: diam}

style n7 fill:#FFCDD2

style n8 fill:#C8E6C9

style n14 fill:#FFCDD2

style n16 fill:#C8E6C9

style n17 fill:#FFCDD2

style n21 fill:#C8E6C9
```

### Componentes
- Mapas Semanticos
	- Se crean mapas semanticos para cada tabla, operacion y patron posible
	- Formato Json/XML
- Sistema de Puntuacion
	- Evalua la consulta y la puntua de acuerdo a las coincidencias de los mapas semanticos
	- Selecciona el patron con mayor puntuacion
	- Sustituye los valores por defecto en los patrones por los de busqueda

### Pros
- Sin dependecias
- Los Datos sensibles estan en local
- Personalizable
- Sin costo
### Contras
- Desarrollo laborioso
- Limitado solo a patrones creados
- Requiere muchas pruebas
- Escalado muy lento y manual

## Opciones Basicas
### UI Tradicional
```mermaid
flowchart TD

A["Inicio del Sistema"] --> B{"Usuario Autenticado?"}

B -- No --> C["Pantalla de Login"]

C --> D["Validar Credenciales"]

D -- Válido --> E["Explorador de Archivos"]

D -- Inválido --> C

E --> L["Filtro por Tipo de Archivo"] & M["Filtro por Fecha de Creación"] & N["Filtro por Fecha de Modificación"] & O["Filtro por Tamaño"] & P["Filtro por Autor/Creador"] & Q["Filtro por Resolución"] & R["Filtro por Duración"] & S["Búsqueda por Nombre"]

L --> T["Dropdown: PDF, DOC, IMG, VIDEO, etc."]

M --> U["Selector de Rango de Fechas"]

N --> V["Selector de Rango de Fechas"]

O --> W["Slider de Tamaño MB/GB"]

P --> X["Campo de Texto - Autor"]

Q --> Y["Rango de Resolución px"]

R --> Z["Rango de Duración min:seg"]

S --> AA["Campo de Búsqueda de Texto"]

T --> BB{"Aplicar Filtros"}

U --> BB

V --> BB

W --> BB

X --> BB

Y --> BB

Z --> BB

AA --> BB

BB -- Buscar --> CC["Construir Consulta con Filtros"]

BB -- Limpiar --> DD["Resetear Filtros"]

DD --> K["Retornar Al Explorador"]

CC --> EE["Validar Parámetros"]

EE -- Válidos --> FF["Ejecutar Búsqueda"]

EE -- Inválidos --> GG["Mostrar Error de Validación"]

GG --> K

FF --> HH["Mostrar Resultados"]

HH --> II["Lista de Archivos Encontrados"]

II --> JJ["Presentacion de Informacion"] & OO["Acciones sobre Archivos"]

JJ --> KK["Renderizado de Template"]

OO --> PP["Abrir Archivo"] & QQ["Mostrar Ubicación"] & RR["Copiar Ruta"] & SS["Exportar Lista"]

K --> E

PP --> AAA["Fin del Proceso"]

QQ --> AAA

RR --> AAA

SS --> AAA

KK --> AAA
```

### Sistema de Tags
```mermaid
---

config:

layout: fixed

---

flowchart TD

A["Inicio del Sistema"] --> B["Usuario Autenticado"]

B -- No --> C["Login"]

C --> D["Validacion de Credenciales"]

D -- Valido --> E["Busqueda por Tags"]

E --> F["#tipo"] & G["#fecha"] & H["#entidad"] & I["#autor"] & J["#extension"]

F --> K["Tags de Tipo de Archivo"]

K --> L["#tipo:imagen"] & M["#tipo:documento"] & N["#tipo:video"]

G --> P["Tags Temporales"]

P --> Q["#creado:2024"] & R["#modificado:enero"] & S["#accedido:ayer"]

H --> T["Tags de Entidad"]

T --> U["#relacionado:entidadZ"] & V["#dirigido:entidadX"] & W["#creado:entidadY"]

I --> Y["Tags de Autoría"]

Y --> Z["#autor:usuario"] & AA["#creador:aplicacion"] & BB["#editor:programa"]

J --> CC["Tags de Extensión"]

CC --> DD["#ext:pdf"] & EE["#ext:img"] & FF["#ext:csv"] & GG["#ext:docx"]

L --> HH["Tags Específicos de Imagen"]

HH --> II["#resolucion:1920x1080"]

N --> LL["Tags Específicos de Video"]

LL --> MM["#duracion:120min"]

M --> PP["Tags Específicos de Documento"]

PP --> QQ["#paginas:5"] & RR["#palabras:1500"]

II --> XX{"Seleccion de Tags con Valores"}

MM --> XX

QQ --> XX

RR --> XX

Q --> XX

R --> XX

S --> XX

U --> XX

V --> XX

W --> XX

Z --> XX

AA --> XX

BB --> XX

DD --> XX

EE --> XX

FF --> XX

GG --> XX

XX --> YY["Validacion de Valores"]

EEE["Motor de Búsqueda por Tags"] --> FFF["Parsear Consulta de Tags"] & YY

FFF --> GGG["Validar Sintaxis"]

GGG -- Válida --> HHH["Ejecutar Búsqueda en Índice"]

HHH --> JJJ["Resultados Encontrados"]

JJJ --> KKK["Lista de Archivos con Tags"]

KKK --> LLL["Mostrar Metadatos Relevantes"]

LLL --> MMM["Auto-generar Tags de Resultado"]

MMM --> NNN["#resultado:encontrados"] & OOO["#cantidad:archivos"]

QQQ["Creacion de Historial"] --> SSS["Guardar Búsqueda"]

D -- Invalido --> C

SSS --> YYY["Fin del Proceso"]

OOO --> QQQ

NNN --> QQQ

B@{ shape: diam}
```

## Orden de Recomendación
Si se quiere un buscador con texto natural:
1. Opción 1 uso de OpenAI API
2. Opción 2 PHP puro
3. Opción 4 PHP + Elasticsearch
4. Opción 3 PHP + spaCy/Python
5. Opción 5 PHP + Base Conocimiento Local

Si se usa un enfoque mas basico de tipo filtro
1. Tags
2. UI tradicional
# Pruebas de Prompt
## Prompt
Prompt generado automaticamente por un script para adaptarse a cualquier configuracion de metadatos en el sistema keydoc, sin espacios para reducir el numero de tokens.
Tokens promedio por prompt 2400.
```text
Eres un experto en bases de datos. Tu tarea es convertir una pregunta o búsqueda en lenguaje natural a una consulta SQL válida y eficiente. Toma en cuenta este esquema de base de datos: ### CONTEXTO DEL ESQUEMA DE BASE DE DATOS: keydoc_fgj_nvoleon Tabla: cadenacustodia Columnas: - IdUnidadAdministrativa (int(10)) [PRIMARY KEY] - IdInventario (int(10)) [PRIMARY KEY] - IdCadenaCustodia (int(10)) [PRIMARY KEY] - Fecha (datetime) - Custodia (varchar(100)) - Depositario (varchar(100)) - Notas (text) Tabla: cedula Columnas: - caja (varchar(255)) - no_requisicion (varchar(255)) - no_licitacion (varchar(255)) - orden_compra (varchar(255)) - proveedor (varchar(255)) - concepto (varchar(255)) - no_contrato (varchar(255)) - orden_pago (varchar(255)) - facturas (varchar(255)) Tabla: configuracion Columnas: - IdMac (varchar(20)) - IdUsuario (int(10)) - NombreEscaner (varchar(255)) - ConfiguracionColorEscaner (tinyint(3)) - MostrarInterfazEscanerTaiwan (tinyint(1)) - AlimentadorAutomaticoADF (tinyint(1)) - DobleCaraDuplex (tinyint(1)) - MaximoNumeroHojas (int(10)) - Resolucion (int(10)) - RutaAlmacenamientoPDF (text) - CarpetaBusqueda (text) - Filtro (text) - GenerarNombreArchivoAutomatico (tinyint(1)) - NombreUbicacionPDFManual (varchar(255)) - GenerarCodigo1D2D (tinyint(1)) - FormatoCodigo (varchar(20)) - PosicionCodigoX (int(10)) - PosicionCodigoY (int(10)) - RequisitosDocumentales (tinyint(1)) Tabla: fondo Columnas: - idFondo (int(10)) [PRIMARY KEY] - codigo (varchar(20)) - Fondo (varchar(100)) Tabla: inventario Columnas: - idFondo (int(10)) - IdUnidadAdministrativa (int(10)) [PRIMARY KEY] - IdInventario (int(10)) [PRIMARY KEY] - IdSeccion (int(10)) - IdSerie (int(10)) - IdSubserie (int(10)) - Digitalizado (tinyint(1)) - IdLayout (int(10)) - Idi1 (int(10)) - Indice_1 (text) - Idi2 (int(10)) - Indice_2 (text) - Idi3 (int(10)) - Indice_3 (text) - Idi4 (int(10)) - Indice_4 (text) - Idi5 (int(10)) - Indice_5 (text) - Idi6 (int(10)) - Indice_6 (text) - Idi7 (int(10)) - Indice_7 (text) - Idi8 (int(10)) - Indice_8 (text) - IdUsuario (int(10)) - FechaRegistro (datetime) - pasillo (varchar(100)) - estante (varchar(100)) - entrepano (varchar(100)) - caja (varchar(100)) - legajo (varchar(100)) - estatus (varchar(20)) - FechaApertura (datetime) - FechaCierre (datetime) - NumeroFojasCierre (int(10)) - Clasificada (tinyint(4)) - DescripcionClasificada (varchar(100)) - ValorDocumental (varchar(20)) - NumeroLegajos (int(10)) - NumeroFojas (int(10)) - RequisitoDocumentalCompletado (tinyint(1)) Relaciones: - idFondo → fondo.idFondo - IdSeccion → secciones.Idseccion - IdSeccion → subseries.IdSeccion - IdSerie → subseries.IdSerie - IdSubserie → subseries.IdSubserie - IdUnidadAdministrativa → unidad_admtva.IdUnidadAdministrativa Tabla: layout Columnas: - IdLayout (int(10)) - NombreLayout (varchar(300)) - IdUnidadAdministrativa (int(10)) - Idi1 (int(10)) - Field_i1 (varchar(50)) - Idi2 (int(10)) - Field_i2 (varchar(50)) - Idi3 (int(10)) - Field_i3 (varchar(50)) - Idi4 (int(10)) - Field_i4 (varchar(50)) - Idi5 (int(10)) - Field_i5 (varchar(50)) - Idi6 (int(10)) - Field_i6 (varchar(50)) - Idi7 (int(10)) - Field_i7 (varchar(50)) - Idi8 (int(10)) - Field_i8 (varchar(50)) Tabla: requisitos_documentales Columnas: - IdRequisitoDocumental (int(10)) [PRIMARY KEY] - IdLayout (int(10)) - RequisitoDocumental (varchar(500)) Tabla: secciones Columnas: - Idseccion (int(10)) [PRIMARY KEY] - IdUnidadAdministrativa (int(10)) - codigo (varchar(20)) - seccion (varchar(255)) Tabla: series Columnas: - IdSeccion (int(10)) [PRIMARY KEY] - IdSerie (int(10)) [PRIMARY KEY] - codigo (varchar(20)) - serie (varchar(255)) - TotalPlazoConservacion (int(10)) - ValorDocumental (varchar(20)) - TecnicaSeleccion (varchar(20)) - Tramite (int(10)) - Concentracion (int(10)) - PublicaClasificada (tinyint(1)) Tabla: subseries Columnas: - IdSeccion (int(10)) [PRIMARY KEY] - IdSerie (int(10)) [PRIMARY KEY] - IdSubserie (int(10)) [PRIMARY KEY] - codigo (varchar(255)) - subserie (varchar(255)) Tabla: ubicacion_pdf Columnas: - IdUnidadAdministrativa (int(10)) [PRIMARY KEY] - IdInventario (int(10)) [PRIMARY KEY] - IdPDF (int(10)) [PRIMARY KEY] - ArchivoPDF (varchar(255)) - Ubicacion (varchar(255)) - Referencia (varchar(255)) - Hojas (int(11)) - IdRequisitoDocumental (int(11)) Tabla: unidad_admtva Columnas: - IdUnidadAdministrativa (int(10)) [PRIMARY KEY] - IdFondo (int(10)) - codigo (varchar(20)) - UnidadAdministrativa (varchar(120)) Tabla: usuario Columnas: - IdUsuario (int(10)) [PRIMARY KEY] - NombreCompleto (varchar(50)) - Cuenta (varchar(20)) - Password (varchar(50)) - Mail (varchar(20)) - Telefono (varchar(20)) - eliminado (tinyint(1)) - administrador (tinyint(1) unsigned zerofill) - IdFondo (int(10)) - IdUnidadAdministrativa (int(10)) ### CAMPOS DINÁMICOS DEFINIDOS EN LAYOUT Layout #1: - Indice_1 → no_oficio - Indice_2 → enviado_recibido - Indice_3 → fecha - Indice_4 → signatario - Indice_5 → asunto Layout #2: - Indice_1 → no_requisicion - Indice_2 → no_licitacion - Indice_3 → orden_compra - Indice_4 → proveedor - Indice_5 → concepto - Indice_6 → no_contrato - Indice_7 → orden_pago/CL - Indice_8 → facturas Layout #3: - Indice_1 → no_requisicion - Indice_2 → no_licitacion - Indice_3 → orden_compra - Indice_4 → proveedor - Indice_5 → concepto - Indice_6 → no_contrato - Indice_7 → orden_pago/CL - Indice_8 → facturas Layout #4: - Indice_1 → numero_ladudo - Indice_2 → asunto - Indice_3 → resolucion - Indice_4 → fecha Layout #5: - Indice_1 → num_oficio - Indice_2 → fecha - Indice_3 → destinatario - Indice_4 → asunto - Indice_5 → acuse --- **REGLA DE SELECTIVIDAD:** - Si la pregunta solicita UN CAMPO ESPECÍFICO (ej: '¿Qué proveedor...?', '¿Cuál es el asunto...?'), selecciona SOLO ese campo. - Si la pregunta solicita MÚLTIPLES CAMPOS específicos, selecciona únicamente los campos mencionados. - Si la pregunta es GENERAL (ej: 'Muestra información de...', 'Busca documentos...'), incluye los campos más relevantes del contexto. **REGLAS TÉCNICAS:** - Usa JOINs explícitos para vincular las tablas. - **SIEMPRE** incluye JOIN con unidad_admtva para obtener el nombre de la unidad administrativa. - **SIEMPRE** incluye JOIN con layout para identificar el tipo de documento y mapear los campos dinámicos. - Para campos dinámicos, usa SOLO el campo Indice_X con el alias correspondiente del Layout. - NO incluyas tanto Field_iX como Indice_X en el SELECT. - Ejemplo correcto: `i.Indice_3 AS orden_compra` - Ejemplo incorrecto: `l.Field_i3 AS 'Campo_3_Nombre', i.Indice_3 AS 'Orden_Compra'` - Los alias deben usar el nombre definido en el Layout sin espacios ni caracteres especiales. - Limita los resultados a 100 si no se especifica límite. - Siempre incluye un filtro por unidad administrativa si se menciona. **EJEMPLOS DE APLICACIÓN:** - '¿Qué proveedor tiene la orden de compra 151506?' → ```sql SELECT i.Indice_4 AS proveedor FROM inventario i JOIN unidad_admtva ua ON i.IdUnidadAdministrativa = ua.IdUnidadAdministrativa JOIN layout l ON i.IdLayout = l.IdLayout WHERE i.Indice_3 = '151506' AND i.IdLayout IN (2, 3) LIMIT 100; ``` - 'Muestra el proveedor y concepto de la orden 151506' → SELECT proveedor y concepto con JOINs - 'Busca información de la orden 151506' → SELECT campos relevantes del contexto con JOINs DEVUELVE SOLO LA CONSULTA SQL. PREGUNTA DEL USUARIO:
```

## Pruebas
### Pregunta
```text
Muestra todas las órdenes de compra relacionadas con "Servicio de limpieza".
```
### Respuesta
```sql
SELECT 
  i.IdUnidadAdministrativa,
  ua.UnidadAdministrativa,
  i.IdInventario,
  i.IdLayout,
  i.Indice_1 AS no_requisicion,
  i.Indice_2 AS no_licitacion,
  i.Indice_3 AS orden_compra,
  i.Indice_4 AS proveedor,
  i.Indice_5 AS concepto,
  i.Indice_6 AS no_contrato,
  i.Indice_7 AS orden_pago,
  i.Indice_8 AS facturas,
  i.IdUsuario,
  i.FechaRegistro,
  i.pasillo,
  i.estante,
  i.entrepano,
  i.caja,
  i.legajo,
  i.estatus
FROM inventario i
JOIN unidad_admtva ua ON i.IdUnidadAdministrativa = ua.IdUnidadAdministrativa
JOIN layout l ON i.IdLayout = l.IdLayout
WHERE (i.Indice_5 LIKE '%Servicio de limpieza%' OR i.Indice_5 LIKE '%servicio de limpieza%')
  AND i.IdLayout IN (2,3)
LIMIT 100;
```
### Resultado
| IdUnidadAdministrativa | UnidadAdministrativa                   | IdInventario | IdLayout | no_requisicion | no_licitacion           | orden_compra | proveedor                                          | concepto                                                                             | no_contrato                                                          | orden_pago | facturas | IdUsuario | FechaRegistro       | pasillo | estante | entrepano | caja | legajo                                                       | estatus |
| ---------------------- | -------------------------------------- | ------------ | -------- | -------------- | ----------------------- | ------------ | -------------------------------------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------- | ---------- | -------- | --------- | ------------------- | ------- | ------- | --------- | ---- | ------------------------------------------------------------ | ------- |
| 3                      | Dirección de Adquisiciones y Servicios | 19           | 2        |                | DMSG/LPNP-005-2017/01-1 |              |                                                    | Servicio de Limpieza solicitado por la Procuraduría General de Justicia en el Estado |                                                                      |            |          | 4         | 2018-10-09 16:51:27 | piso    |         | 1 de 2    | 9    | Lista de procedimientos de contratación de área de concursos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 66           | 2        | 128253         |                         | 151641       | Beneficio Administrativos Integrales, S.A. de C.V. | Servicio de limpieza y manejo de desechos-personal de limpieza                       | contrato  DMSG/LPNP-005-2017/01-1 Y Addendum DMSG/LPNP-005-2017/01-1 | 303947     | 59       | 4         | 2018-10-15 15:47:30 | piso    |         |           | 1    | relación y copia de contratos                                | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 67           | 2        | 128254         |                         | 151643       | Beneficio Administrativos Integrales, S.A. de C.V. | Servicio de limpieza y manejo de desechos-personal de limpieza                       | contrato  DMSG/LPNP-005-2017/01-1 Y Addendum DMSG/LPNP-005-2017/01-1 | 303939     | 60       | 4         | 2018-10-15 15:51:05 | piso    |         |           | 1    | relación y copia de contratos                                | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 69           | 2        | 128261         |                         | 151644       | Beneficio Administrativos Integrales, S.A. de C.V. | Servicio de limpieza y manejo de desechos-personal de limpieza                       | contrato  DMSG/LPNP-005-2017/01-1 Y Addendum DMSG/LPNP-005-2017/01-1 | 303949     | 61       | 4         | 2018-10-15 15:57:25 | piso    |         |           | 1    | relación y copia de contratos                                | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 70           | 2        | 128266         |                         | 151647       | Beneficio Administrativos Integrales, S.A. de C.V. | Servicio de limpieza y manejo de desechos-personal de limpieza                       | contrato  DMSG/LPNP-005-2017/01-1 Y Addendum DMSG/LPNP-005-2017/01-1 | 303941     | 58       | 4         | 2018-10-15 16:03:10 | piso    |         |           | 1    | relación y copia de contratos                                | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 71           | 2        | 128270         |                         | 151649       | Beneficio Administrativos Integrales, S.A. de C.V. | Servicio de limpieza y manejo de desechos-personal de limpieza                       | contrato  DMSG/LPNP-005-2017/01-1 Y Addendum DMSG/LPNP-005-2017/01-1 | 303945     | 55       | 4         | 2018-10-15 16:05:13 | piso    |         |           | 1    | relación y copia de contratos                                | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 72           | 2        | 128273         |                         | 151650       | Beneficio Administrativos Integrales, S.A. de C.V. | Servicio de limpieza y manejo de desechos-personal de limpieza                       | contrato  DMSG/LPNP-005-2017/01-1 Y Addendum DMSG/LPNP-005-2017/01-1 | 303937     | 56       | 4         | 2018-10-15 16:08:59 | piso    |         |           | 1    | relación y copia de contratos                                | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 73           | 2        | 128252         |                         | 152295       | Beneficio Administrativos Integrales, S.A. de C.V. | Servicio de limpieza y manejo de desechos-personal de limpieza                       | contrato  DMSG/LPNP-005-2017/01-1 Y Addendum DMSG/LPNP-005-2017/01-1 | 303881     | 81       | 4         | 2018-10-15 16:11:11 | piso    |         |           | 1    | relación y copia de contratos                                | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 74           | 2        | 129980         |                         | 153696       | Beneficio Administrativos Integrales, S.A. de C.V. | Servicio de limpieza y manejo de desechos-personal de limpieza                       | contrato  DMSG/LPNP-005-2017/01-1 Y Addendum DMSG/LPNP-005-2017/01-1 | 303943     | 83       | 4         | 2018-10-15 16:14:36 | piso    |         |           | 1    | relación y copia de contratos                                | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 1929         | 2        | 133044         |                         | 158052       | Red Recolector, S.A de C.V                         | Servicio de limpieza y manejo de desechos - basura y residuos Biológicos             |                                                                      |            |          | 4         | 2018-10-22 11:15:12 | piso    |         |           | 2    | comprometido sin devengar                                    | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 1930         | 2        | 129857         |                         | 158053       | Red Recolector, S.A de C.V                         | Servicio de limpieza y manejo de desechos - basura y residuos Biológicos             |                                                                      |            |          | 4         | 2018-10-22 11:15:39 | piso    |         |           | 2    | comprometido sin devengar                                    | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 1931         | 2        | 129851         |                         | 158055       | Red Recolector, S.A de C.V                         | Servicio de limpieza y manejo de desechos - basura y residuos Biológicos             |                                                                      |            |          | 4         | 2018-10-22 11:16:22 | piso    |         |           | 2    | comprometido sin devengar                                    | Trámite |
### Pregunta
```text
¿Qué proveedor tiene la orden de compra 151506?
```
### Respuesta
```sql
SELECT 
  i.Indice_4 AS proveedor
FROM inventario i
JOIN unidad_admtva ua ON i.IdUnidadAdministrativa = ua.IdUnidadAdministrativa
JOIN layout l ON i.IdLayout = l.IdLayout
WHERE i.Indice_3 = '151506'
  AND i.IdLayout IN (2,3)
LIMIT 100;
```
### Resultados

| Proveedor                                |     |
| ---------------------------------------- | --- |
| Comedor Industrial Cumbres, S.A. de C.V. |     |

### Pregunta
```text
¿Qué requisiciones están en la caja número 1?
```
### Respuesta
```sql
SELECT 
  i.IdUnidadAdministrativa,
  ua.UnidadAdministrativa,
  i.IdInventario,
  i.IdLayout,
  i.Indice_1 AS no_requisicion,
  i.Indice_2 AS no_licitacion,
  i.Indice_3 AS orden_compra,
  i.Indice_4 AS proveedor,
  i.Indice_5 AS concepto,
  i.Indice_6 AS no_contrato,
  i.Indice_7 AS orden_pago,
  i.Indice_8 AS facturas,
  i.IdUsuario,
  i.FechaRegistro,
  i.pasillo,
  i.estante,
  i.entrepano,
  i.caja,
  i.legajo,
  i.estatus
FROM inventario i
JOIN unidad_admtva ua ON i.IdUnidadAdministrativa = ua.IdUnidadAdministrativa
JOIN layout l ON i.IdLayout = l.IdLayout
WHERE i.caja = '1' AND i.IdLayout IN (2,3)
LIMIT 100;
```
### Resultado
| IdUnidadAdministrativa | UnidadAdministrativa                   | IdInventario | IdLayout | no_requisicion | no_licitacion | orden_compra | proveedor                                                 | concepto                                                                                                                                                       | no_contrato | orden_pago | facturas    | IdUsuario | FechaRegistro       | pasillo | estante | entrepano | caja | legajo                        | estatus |
| ---------------------- | -------------------------------------- | ------------ | -------- | -------------- | ------------- | ------------ | --------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------- | ----------- | --------- | ------------------- | ------- | ------- | --------- | ---- | ----------------------------- | ------- |
| 3                      | Dirección de Adquisiciones y Servicios | 23           | 2        | 128249         |               | 151506       | Comedor Industrial Cumbres, S.A. de C.V.                  | Servicio de desayuno y comida los días lunes, para 10 personas que acuden a reunión de trabajo con el C. Procurador en periodo del 29 de enero al 12 de marzo. |             | 289592     | 1345        | 4         | 2018-10-15 11:35:03 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 24           | 2        | 128611         |               | 152475       | Comedor Industrial Cumbres, S.A. de C.V.                  | Servicio de desayuno y comida los días lunes, para 10 personas que acuden a reunión de trabajo con el C. Procurador en periodo del 29 de enero al 12 de marzo. |             | 289591     | 1346        | 4         | 2018-10-15 11:38:56 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 25           | 2        | 128264         |               | 152588       | Control de Precisión Automotriz, S.A. de C.V.             | Reparación y mantenimiento equipo transporte -mantenimiento correctivo                                                                                         |             | 288861     | B4409       | 4         | 2018-10-15 11:42:39 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 26           | 2        | 128347         |               | 152622       | Control de Precisión Automotriz, S.A. de C.V.             | Reparación y mantenimiento equipo transporte -mantenimiento preventivo                                                                                         |             | 288849     | B4403       | 4         | 2018-10-15 11:45:36 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 27           | 2        | 128425         |               | 152636       | Control de Precisión Automotriz, S.A. de C.V.             | Reparación y mantenimiento equipo transporte -mantenimiento correctivo                                                                                         |             | 288850     | B4404       | 4         | 2018-10-15 11:48:30 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 28           | 2        | 128461         |               | 152644       | Control de Precisión Automotriz, S.A. de C.V.             | Reparación y mantenimiento equipo transporte -mantenimiento correctivo                                                                                         |             | 288856     | B4406       | 4         | 2018-10-15 11:52:00 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 29           | 2        | 128463         |               | 152645       | Control de Precisión Automotriz, S.A. de C.V.             | Reparación y mantenimiento equipo transporte -mantenimiento correctivo                                                                                         |             | 288859     | B4407       | 4         | 2018-10-15 11:55:41 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 30           | 2        | 128509         |               | 152655       | Control de Precisión Automotriz, S.A. de C.V.             | Reparación y mantenimiento equipo transporte -mantenimiento correctivo                                                                                         |             | 288851     | B4405       | 4         | 2018-10-15 11:57:27 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 31           | 2        | 128650         |               | 152666       | Control de Precisión Automotriz, S.A. de C.V.             | Reparación y mantenimiento equipo transporte -mantenimiento preventivo                                                                                         |             | 288863     | B4410       | 4         | 2018-10-15 12:01:46 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 32           | 2        | 131142         |               | 154619       | Garza Valdés Esther Alicia                                | Conservación y mantenimiento menor de inmuebles-servicios suministros e instalación de cristal                                                                 |             | 290140     | 441         | 4         | 2018-10-15 12:03:48 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 33           | 2        | 128811         |               | 152652       | Rangel Banda Jannet Eugenia                               | Exámenes médicos y Toxicológicos para cuerpos de seguridad                                                                                                     |             | 287110     | 2669        | 4         | 2018-10-15 12:07:10 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 34           | 2        | 133027         |               | 155138       | Calidad y Estrategia en Blindaje Automotriz, S.A. de C.V. | Camioneta blindada                                                                                                                                             |             |            | A245 y A246 | 4         | 2018-10-15 12:10:09 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 35           | 2        | 133026         |               | 155139       | Calidad y Estrategia en Blindaje Automotriz, S.A. de C.V. | Camioneta blindada                                                                                                                                             |             |            | A247 y A248 | 4         | 2018-10-15 12:31:25 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 36           | 2        | 133024         |               | 155140       | Calidad y Estrategia en Blindaje Automotriz, S.A. de C.V. | Camioneta blindada                                                                                                                                             |             |            | A241 y A242 | 4         | 2018-10-15 12:45:42 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
| 3                      | Dirección de Adquisiciones y Servicios | 37           | 2        | 133008         |               | 155142       | Calidad y Estrategia en Blindaje Automotriz, S.A. de C.V. | Camioneta blindada                                                                                                                                             |             |            | A243 Y A244 | 4         | 2018-10-15 12:48:30 | piso    |         |           | 1    | relación y copia de contratos | Trámite |
Muestra de los 100 resultados de la consulta.
### Pregunta
```text
¿Qué proveedor tiene la orden de compra 151506?
```
### Respuesta
```sql
SELECT 
  i.Indice_4 AS proveedor
FROM inventario i
JOIN unidad_admtva ua ON i.IdUnidadAdministrativa = ua.IdUnidadAdministrativa
JOIN layout l ON i.IdLayout = l.IdLayout
WHERE i.Indice_3 = '151506'
  AND i.IdLayout IN (2, 3)
LIMIT 100;
```
### Resultado
| Proveedor                                |
| ---------------------------------------- |
| Comedor Industrial Cumbres, S.A. de C.V. |

### Pregunta
```text
¿Cuáles son los conceptos más repetidos?
```
### Respueta
```sql
SELECT 
  i.Indice_5 AS concepto,
  COUNT(*) AS total
FROM inventario i
JOIN layout l ON i.IdLayout = l.IdLayout
WHERE i.IdLayout IN (2, 3)
GROUP BY i.Indice_5
ORDER BY total DESC
LIMIT 100;
```
### Resultado
| Concepto                                                                                                 | Total |
| -------------------------------------------------------------------------------------------------------- | ----: |
|                                                                                                          |   833 |
| Reparación y Mantenimiento, Equipo Transporte - Mantenimiento correctivo a vehículos                     |   444 |
|                                                                                                          |   361 |
| Reparación y MTTO equipo transporte- mantenimiento correctivo a vehículos                                |   242 |
| Reparación y Mantenimiento de Equipo de Transporte - Mantenimiento Correctivo a Vehiculos                |   219 |
| Reparación y mantenimiento equipo transporte -mantenimiento correctivo                                   |   204 |
| Reparación y Mantto. De equipo de transporte - mantenimiento correctivo a vehículos                      |   155 |
| Reparación y MTTO, equipo transporte- suministro e instalación MTTO de climas                            |    98 |
| Reparación y MTTO equipo transporte suministro e instalación de llantas y cámaras                        |    82 |
| Reparación y Mantto. De equipo de transporte   mantenimiento correctivo a vehículos                      |    79 |
| Reparación y mantenimiento Equipo de transporte-suministro e instalación de llantas y cámaras.           |    59 |
| Reparación y MTTO equipo  transporte- Mantenimiento Preventivo a Vehículos                               |    52 |
| Reparación y Mantenimiento de Equipo de Transporte - Mantenimiento Preventivo a Vehículos                |    50 |
| Reparación y mantenimiento equipo transporte-acumuladores                                                |    49 |
| Reparación y MTTO equipo  transporte- acumuladores                                                       |    47 |
| Reparación Mantenimiento de Equipo de Transporte - Suministro e Instalación de Llantas y Cámaras         |    42 |
| Reparación y mantto. Equipo de transporte - suministro e instalación de llantas y camaras                |    39 |
| Servicios de vigilancia                                                                                  |    33 |
| Reparación y mantenimiento equipo transporte suministro e instalación de llantas y cámaras               |    29 |
| Reparación y mantenimiento equipo transporte -mantenimiento preventivo                                   |    27 |
| Reparación y Mantenimiento, Equipo Transporte- Acumuladores                                              |    27 |
| Conservación y Mantenimiento menor de inmuebles                                                          |    26 |
| Instalación, reparación y mantenimiento de equipo de computo y tecnología  de la información             |    22 |
| Reparación y Mantenimiento de Equipo de Transporte-Mantenimiento Correctivo a Vehiculos                  |    21 |
| Suministro de Materiales y Reactivos                                                                     |    19 |
| Reparación y mantenimiento , equipo transporte- mantenimiento preventivo a vehículos                     |    17 |
| Reparación y Mantenimiento de Equipo de Transporte - Acumuladores                                        |    16 |
| Reparación y  mantenimiento de equipo de transporte - suministro e instalación mantenimiento de climas   |    15 |
| Reparación y mantenimiento equipo transporte . Mantenimiento preventivo a vehículos                      |    13 |
| Reparación y Mantto. De Equipo de transporte -mantenimiento preventivo a vehículos                       |    12 |
| Instalación reparación y mantenimiento de equipo de cómputo y tecnología de la información               |    11 |
| Reparación y Mantenimiento de Equipo de Transporte - Suministro e Instalación Mantenimiento a Climas     |    10 |
| Servicios de limpieza y manejo de desechos                                                               |    10 |
| Reparción y mantenimiento equipo de transporte   Acumuladores                                            |    10 |
| Instalación , reparación y mantenimiento de equipo de computo y tecnología de la información             |     9 |
| Instalación, reparación y mantenimiento de equipo de administración educacional y recreativo             |     9 |
| Reparación y Mantenimiento equipo de transporte - Acumuladores                                           |     9 |
| Suministro de silla de visita fija con asiento y respaldo separado                                       |     9 |
| Autorización de comprobación de gastos                                                                   |     9 |
| Camioneta blindada                                                                                       |     8 |
| Servicio de limpieza y manejo de desechos-personal de limpieza                                           |     8 |
| Reparación y mantenimiento equipo transporte -suministro e instalación mantenimiento de clima            |     8 |
| Servicios de Limpieza y Manejo de Desechos - Basura y Residuos Biológicos                                |     8 |
| Reparación y Mantenimiento Equipo de Transporte-Suministro e Instalación de Llantas y Cámaras            |     8 |
| Servicio de Jardinería y fumigación                                                                      |     8 |
| Conservación y mantenimiento menor de inmuebles -servicios                                               |     8 |
| Varios equipamiento(luces, torretas, porta armas, sistema de elevación de equipo)                        |     8 |
| Garrafones de Agua purificadora                                                                          |     8 |
| Instalación, reparación y mantenimiento de equipo especializado de inmuebles                             |     7 |
| Reparación y Mantenimiento de Equipo de Transporte . Suministro e Instalación  Mantenimiento de Climas   |     7 |
| Instalación, Reparación y Mantenimiento de Equipo Especializado de Inmuebles - Aire Acondicionado        |     7 |
| Servicios de Limpieza y manejo de desechos - Personal de Limpieza                                        |     7 |
| Reparación y mantenimiento transporte - mantenimiento preventivo a vehículos                             |     7 |
| Servicios de Capacitación                                                                                |     7 |
| Reparación y mantenimiento equipo transporte-mantenimiento correctivo                                    |     6 |
| Otros arrendamientos                                                                                     |     6 |
| Estante metálico                                                                                         |     6 |
| Instalación, Reparación y Mantenimiento de Equipo Especializado de Inmuebles- Aire Acondicionado         |     6 |
| Instalación, reparación y mantenimiento de equipo de computo y tecnología de la información.             |     6 |
| Reparación y mantto. Equipo de transporte - acumuladores                                                 |     6 |
| Reparación y mantto, equipo de transporte - acumuladores                                                 |     6 |
| cámara de video vigilancia                                                                               |     6 |
| licencia de software                                                                                     |     6 |
| Teléfono con Tecnología IP                                                                               |     6 |
| Servicios de jardinería y fumigación                                                                     |     5 |
| Radio Portátil                                                                                           |     5 |
| Suministro de silla operativa respaldo y asiento separados                                               |     5 |
| Instalación, Reparación y Mantenimiento de Equipo de Cómputo y Tecnología de la Información              |     4 |
| Conservación y mantenimiento menor de inmuebles- servicios de tubería de agua, materiales y mano de obra |     4 |
| Servicio de apoyo Administrativo, fotocopiado e impresión - Impresos                                     |     4 |
| Arrendamiento de equipo de transporte                                                                    |     4 |
| Reparación y Mantto. De equipo de transporte  mantenimiento correctivo a vehículos                       |     4 |
| Reparación y mantto. Equipo de transporte -acumuladores                                                  |     4 |
| Reparación y Mantto. Equipo de transporte - mantenimiento preventivo a vehículos                         |     4 |
| Chapa Magnética                                                                                          |     4 |
| Pantalla LED                                                                                             |     4 |
| Artículos Varios                                                                                         |     4 |
| Suministro de Unidad de ininterrumpido de energía eléctrica UPS                                          |     4 |
| Suministro de Replica de arma inerte para entrenamiento                                                  |     4 |
| Suministro de archivero metálico tipo HON                                                                |     4 |
| Materiales y Útiles de Oficina                                                                           |     4 |
| Material de Limpieza                                                                                     |     4 |
| Exámenes médicos y Toxicológicos para cuerpos de seguridad                                               |     3 |
| Conservación y mantenimiento menor de inmuebles-instalaciones eléctricas                                 |     3 |
| Servicio de apoyo administrativo, fotocopiado e impresión                                                |     3 |
| Garrafón de agua purificada de 19Lts                                                                     |     3 |
| Reparación y Mantenimiento de Equipo de Transporte- Suministro e Instalación Mantenimiento de Climas     |     3 |
| Instalación, Reparación y Mantenimiento de Equipo de Cómputo de Tecnología de la Información             |     3 |
| Servicio de Vigilancia                                                                                   |     3 |
| Reparación y MTTO equipo transporte- servicio vulcanizadora, alineación y balanceo                       |     3 |
| Computadora de Escritorio                                                                                |     3 |
| Servicio de limpieza y manejo de desechos - basura y residuos Biológicos                                 |     3 |
| Servicios de apoyo administrativo, fotocopiado e impresión - impresos                                    |     3 |
| Impresión  formato tamaño oficio bond                                                                    |     3 |
| Repación y mantenimiento de equipo de transporte                                                         |     3 |
| Instalación reparación y mantenimiento de Especializado de Inmuebles                                     |     3 |
| Suministro de Cámara Profesional                                                                         |     3 |
| Suministro de computadora Portátil                                                                       |     3 |
| Adquisición de 1 campana de extracción de vapores                                                        |     3 |
| Suministro de video cámara digital                                                                       |     3 |
### Pregunta
```text
¿Qué conceptos tienen un contrato asignado pero no tienen orden de pago?
```
### Respuesta
```sql
SELECT 
  i.Indice_5 AS concepto,
  i.Indice_6 AS no_contrato,
  i.Indice_7 AS orden_pago
FROM inventario i
JOIN layout l ON i.IdLayout = l.IdLayout
WHERE i.IdLayout IN (2, 3)
  AND i.Indice_6 IS NOT NULL AND TRIM(i.Indice_6) <> ''
  AND (i.Indice_7 IS NULL OR TRIM(i.Indice_7) = '')
LIMIT 100;
```
### Resultado
| Concepto                                                                                         | No_Contrato                                              | Orden_Pago |
| ------------------------------------------------------------------------------------------------ | -------------------------------------------------------- | ---------- |
| Camioneta blindada                                                                               | DASG/CXIR-013-2017/01                                    |            |
| Reparación Mantenimiento de Equipo de Transporte - Suministro e Instalación de Llantas y Cámaras | DGASG/LPIP-041-2017/01-2                                 |            |
| Reparación Mantenimiento de Equipo de Transporte - Suministro e Instalación de Llantas y Cámaras | DGASG/LPIP-041-2017/01-2                                 |            |
| Reparación Mantenimiento de Equipo de Transporte - Suministro e Instalación de Llantas y Cámaras | DGASG/LPIP-041-2017/01-2                                 |            |
| Reparación Mantenimiento de Equipo de Transporte - Suministro e Instalación de Llantas y Cámaras | DGASG/LPIP-041-2017/01-2                                 |            |
| Reparación Mantenimiento de Equipo de Transporte - Suministro e Instalación de Llantas y Cámaras | DGASG/LPIP-041-2017/01-2                                 |            |
| Reparación Mantenimiento de Equipo de Transporte - Suministro e Instalación de Llantas y Cámaras | DGASG/LPIP-041-2017/01-2                                 |            |
| Reparación Mantenimiento de Equipo de Transporte - Suministro e Instalación de Llantas y Cámaras | DGASG/LPIP-041-2017/01-2                                 |            |
| Reparación Mantenimiento de Equipo de Transporte - Suministro e Instalación de Llantas y Cámaras | DGASG/LPIP-041-2017/01-2                                 |            |
| Servicios de Limpieza y manejo de desechos - Personal de Limpieza                                | DMSG/LNP-005-2017/01-1¶ADDENDUM DMSG/LPNP-005-2017/01-1¶ |            |
| Servicios de Limpieza y manejo de desechos - Personal de Limpieza                                | DMSG/LNP-005-2017/01-1¶ADDENDUM DMSG/LPNP-005-2017/01-1¶ |            |
| Reactivo Miseq                                                                                   | DGASG/LPIP-027-2017/02-5                                 |            |
### Pregunta con errores
```text
Cual son ls 4 provedres con mas contatos?
```
### Respuesta
```sql
SELECT 
  i.Indice_4 AS proveedor,
  COUNT(DISTINCT i.Indice_6) AS total_contratos
FROM inventario i
JOIN layout l ON i.IdLayout = l.IdLayout
WHERE i.IdLayout IN (2, 3)
  AND i.Indice_6 IS NOT NULL AND TRIM(i.Indice_6) <> ''
GROUP BY i.Indice_4
ORDER BY total_contratos DESC
LIMIT 4;
```
### Resultados
| proveedor                                          | total_contratos |
| -------------------------------------------------- | --------------- |
| Comercializadora Alfin, S.A. de C.V.               | 12              |
| Comercializadora ALFIN, S. A. de C. V.             | 9               |
| Control Técnico y representaciones, S. A. de C. V. | 7               |
| Control técnico y representaciones, S.A. de C.V.   | 5               |

### Pregunta
```text
¿Cuántas órdenes de compra están asociadas al proveedor "Designer, S.A. de C.V."?
```
### Respuesta
```sql
SELECT 
  COUNT(*) AS total_ordenes_compra
FROM inventario i
JOIN layout l ON i.IdLayout = l.IdLayout
WHERE i.IdLayout IN (2, 3)
  AND i.Indice_4 = 'Designer, S.A. de C.V.';
```
### Resultado

| total_ordenes_compra |     |
| -------------------- | --- |
| 147                  |     |

# Estructura General.
## Vision General.
``` mermaid
---

config:

layout: dagre

---

flowchart LR

subgraph s1["Keydoc"]

n1["DB"]

end

subgraph s2["Sistema Buscador"]

n2["Modulo Autentificacion"]

n4["Sistema DB"]

n5["Modulo Buscador"]

n8["Modulo Conexiones"]

n9["Modulo Administrador"]

end

subgraph s3["Subscripciones"]

n3["DB"]

n6["Datos de la base cliente"]

end

n2 <-- A que sistema conectarse --> n3

n5 <-- Consulta sobre --> n1

n4 --> n5

n3 --> n6

n2 --> n8

n8 -- Base especifica --> n4

n5 --> n9

n1@{ shape: db}

n2@{ shape: proc}

n4@{ shape: db}

n3@{ shape: db}

n6@{ shape: internal-storage}
```

## Modulos - Componentes del sistema.
### Autentificacion.
#### Funciones:
- Login.
- Logout.
- Crear Sesion.
- Cerrar Sesion.
- Validar Credenciales.
- Verificar Roles.
- Obtener datos de conexion.

### Conexion.
#### Funciones:
- Crear Conexiones.
- Validar Conexiones.
- Actualizar Conexiones.
- Eliminar Conexiones sin usar.

### Buscador.
#### Funciones:
- Conectar con Keydoc.
- Enviar busqueda a IA.
- Ejecutar Consulta.
- Validar Consulta.
- Recibir datos de consulta.
- Formatear Datos de acuerdo a la consulta.
- Presentar los al usuario.
- Registrar historial de busquedas.
- Historial de busquedas.
### Administrador.
#### Funciones:
- Registrar consumo de tokens.
- Restringir uso de consultas.
- Verificar disponibilidad de tokens.
- Analisis de consumo.

### Roles y Permisos.
#### Funciones:
- Crear Roles.
- Definir Permisos.
- Verificar permisos.
- Permisos a nivel sistema.
- Permisos de acceso a la informacion.
- Asignar roles y permisos.

---
## Modulo Conexion.
```mermaid
flowchart TB

n1["Inicio"] --> n2["Recibe Token"]

n2 --> n3["Existe Conexion"]

n3 -- Si --> n4["Retorna Datos de Conexion"]

n3 -- No --> n5["Conexion a Subscripciones"]

n5 --> n6["Consultar Datos Token"]

n5 <--> n10["Subscripciones"]

n6 --> n7["Almacena Datos"]

n7 --> n8["Crea Conexion"]

n8 --> n9["Retorna Datos Conexion"]

n11["Verifica Conexiones"] --> n12["Elimina Conexiones sin Usar"] & n13["Actualiza Datos Conexion"]

n1@{ shape: terminal}

n3@{ shape: diam}

n10@{ shape: db}

n11@{ shape: subproc}

n12@{ shape: subproc}

n13@{ shape: subproc}
```

## Modulo Autentificacion.
```mermaid
flowchart TB

n1["Inicio"] --> n2["Sesion Activa"]

n2 -- si --> n3["Redireccion Dashboard"]

n2 -- No --> n4["Redireccion Login"]

n4 --> n5["Datos de Logueo"]

n5 --> n6["Token a Modulo Conexion"]

n6 --> n7["Conexion a DB"]

n7 --> n13["Obtiene Datos de Usuario"]

n8["Credenciales Correctas"] -- No --> n10["Redireccion Login"]

n9["Crear Sesion"] --> n11["Redireccionar Dashboard"] & n12["Redireccion Buscador"]

n13 --> n8

n14["Logout"] --> n15["Eliminar Sesion"]

n15 --> n16["Login"]

n8 -- Si --> n17["Obtener Permisos"]

n17 --> n9

  

n1@{ shape: terminal}

n2@{ shape: decision}

n6@{ shape: subproc}

n8@{ shape: diam}

n14@{ shape: subproc}
```

## Modulo Buscador.
```mermaid
flowchart TB

n1["Recibe Busqueda"] --> n2["Envia Busqueda"]

n2 --> n3["Modulo Consultas"]

n3 --> n4["Recibe la Consulta"]

n4 --> n5["Consulta Valida"] & n8["Registro de Consumo"]

n5 -- Si --> n6["Permisos Acceso Info"]

n5 -- No --> n7["Respuesta Error"]

n7 --> n10["Registro de Errores"]

n9["Envia Respuesta"] --> n11(["Fin"])

n6 -- No --> n12["Respuesta Error"]

n6 -- Si --> n13["Consulta Ejecutada"]

n12 --> n10

n13 -- No --> n14["Error en Consulta"]

n10 --> n9

n13 -- Si --> n15["Modulo Formateo Informacion"]

n14 --> n10

n15 --> n16["Respuesta Formateada"] & n20["Modulo Historial"]

n16 --> n17["Envio de Respues y Datos"]

n17 --> n18["Presentacion al Usuario"]

n18 --> n19(["Fin"])

n1@{ shape: terminal}

n3@{ shape: subproc}

n5@{ shape: diam}

n8@{ shape: subproc}

n6@{ shape: decision}

n10@{ shape: subproc}

n13@{ shape: diam}

n15@{ shape: subproc}

n20@{ shape: subproc}
```

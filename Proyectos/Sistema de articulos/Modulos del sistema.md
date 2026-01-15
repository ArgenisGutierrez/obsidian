# Estructura MVC - Sistema de Transparencia

## MODELOS (Models)

### Usuario.php

- `crear($datos)`
- `obtenerPorId($id)`
- `obtenerTodos()`
- `actualizar($id, $datos)`
- `eliminar($id)`
- `validarCredenciales($usuario, $password)`
- `cambiarPassword($id, $nuevoPassword)`

### UnidadAdministrativa.php

- `crear($datos)`
- `obtenerTodas()`
- `actualizar($id, $datos)`
- `eliminar($id)`

### Articulo.php

- `crear($datos)`
- `obtenerTodos()`
- `actualizar($id, $datos)`
- `eliminar($id)`
- `obtenerConFracciones()`

### Fraccion.php

- `crear($datos)`
- `obtenerPorId($id)`
- `obtenerTodas()`
- `actualizar($id, $datos)`
- `eliminar($id)`
- `obtenerPorUnidadAdministrativa($idUnidad)`
- `reasignarUnidad($idFraccion, $nuevaUnidad)`

### Contenido.php

- `crear($datos)`
- `obtenerPorId($id)`
- `actualizar($id, $datos)`
- `eliminar($id)`
- `obtenerPorFraccion($idFraccion)`
- `cambiarEstadoPublicacion($id, $estado)`

### Configuracion.php

- `obtenerConfiguracion()`
- `actualizarConfiguracion($datos)`
- `obtenerEntidad()`
- `actualizarEntidad($datos)`

## CONTROLADORES (Controllers)

### AuthController.php

- `login()`
- `logout()`
- `validarSesion()`
- `mostrarFormularioLogin()`
- `procesarLogin()`

### UsuarioController.php

- `index()` - Listar usuarios
- `crear()` - Mostrar formulario crear
- `guardar()` - Procesar creación
- `editar($id)` - Mostrar formulario editar
- `actualizar($id)` - Procesar actualización
- `eliminar($id)` - Eliminar usuario
- `perfil()` - Ver/editar perfil propio
- `cambiarPassword()`

### UnidadAdministrativaController.php

- `index()` - Listar unidades
- `crear()` - Mostrar formulario crear
- `guardar()` - Procesar creación
- `editar($id)` - Mostrar formulario editar
- `actualizar($id)` - Procesar actualización
- `eliminar($id)` - Eliminar unidad
- `ver($id)` - Ver detalle con usuarios

### ArticuloController.php

- `index()` - Listar artículos
- `crear()` - Mostrar formulario crear
- `guardar()` - Procesar creación
- `editar($id)` - Mostrar formulario editar
- `actualizar($id)` - Procesar actualización
- `eliminar($id)` - Eliminar artículo
- `ver($id)` - Ver artículo con fracciones

### FraccionController.php

- `index()` - Listar fracciones
- `crear()` - Mostrar formulario crear
- `guardar()` - Procesar creación
- `editar($id)` - Mostrar formulario editar
- `actualizar($id)` - Procesar actualización
- `eliminar($id)` - Eliminar fracción
- `reasignar($id)` - Reasignar a otra unidad
- `misFracciones()` - Fracciones del usuario logueado

### ContenidoController.php

- `index()` - Listar contenidos (admin)
- `misContenidos()` - Contenidos del usuario
- `crear($idFraccion)` - Mostrar formulario crear
- `guardar()` - Procesar creación
- `editar($id)` - Mostrar formulario editar
- `actualizar($id)` - Procesar actualización
- `eliminar($id)` - Eliminar contenido
- `subirArchivo($id)` - Subir archivo
- `descargarArchivo($id)` - Descargar archivo
- `publicar($id)` - Cambiar estado publicación

### ConfiguracionController.php

- `index()` - Mostrar configuración
- `actualizar()` - Procesar actualización
- `subirImagen()` - Subir imagen
- `eliminarImagen()` - Eliminar imagen

### DashboardController.php

- `index()` - Dashboard principal
- `adminDashboard()` - Dashboard administrador
- `usuarioDashboard()` - Dashboard usuario

### PublicController.php

- `inicio()` - Página pública inicio
- `articulo($id)` - Ver artículo público
- `fraccion($id)` - Ver fracción pública
- `buscar()` - Búsqueda pública
- `descargar($id)` - Descarga pública de archivos

## VISTAS (Views)

### auth/

- `login.php` - Formulario de login

### dashboard/

- `home.php` - Dashboard segun rol

### usuarios/

- `index.php` - Listar usuarios
- `crear.php` - Formulario crear usuario
- `editar.php` - Formulario editar usuario
- `perfil.php` - Ver/editar perfil

### unidades/

- `index.php` - Listar unidades por fraccion
- `crear.php` - Formulario crear contenido
- `editar.php` - Formulario editar contenido

### articulos/

- `index.php` - Listar articulos
- `crear.php` - Formulario crear articulos
- `editar.php` - Formulario editar articulos

### fracciones/

- `index.php` - Listar fracciones
- `crear.php` - Formulario crear fraccion
- `editar.php` - Formulario editar fraccion
- `asignar.php` - Formulario asignar fraccion a unidad

### contenidos/

- `index.php` - Listar contenidos por fraccion
- `crear.php` - Formulario crear contenido
- `editar.php` - Formulario editar contenido

### configuracion/

- `entidad.php` - Formulario configuracion entidad
- `config.php` - Formulario configuracion imagenes

## CLASES DE SOPORTE

### Database.php

- `getConnection()`

### Router.php

- `get($route, $callback)`
- `post($route, $callback)`
- `run()`
- `redirect($url)`

### Session.php

- `start()`
- `set($key, $value)`
- `get($key)`
- `destroy()`
- `isLoggedIn()`
- `isAdmin()`
- `getUnidadAdministrativa()`

### FileManager.php

- `subirArchivo($archivo, $destino)`
- `eliminarArchivo($ruta)`
- `validarArchivo($archivo)`
- `generarNombreUnico($nombre)`

### Validator.php

- `validarPasswordFuerza($password)`
- `validarArchivo($archivo, $tipos, $tamaño)`

### Security.php

- `hashPassword($password)`
- `verifyPassword($password, $hash)`
- `generateToken()`
- `sanitizeInput($input)`
- `validateCSRF($token)`
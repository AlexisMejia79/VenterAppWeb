# Informe técnico — módulo web de VenterApp

## Objetivo
Implementar una versión web del módulo de gestión de productos de VenterApp mediante Servlets, JSP, HTML, JDBC, MariaDB y control de versiones Git, conservando el proyecto Java de consola como entrega independiente.

## Alcance implementado
- Consultar productos (GET).
- Registrar productos (POST).
- Cargar producto por ID para edición (GET).
- Actualizar productos (POST).
- Eliminar productos (POST con confirmación en la interfaz).
- Validar campos básicos y usar PreparedStatement.

## Arquitectura
- Modelo: `co.venterapp.model.Producto`.
- Acceso a datos: `co.venterapp.dao.ProductoDAO` y `ProductoDAOImpl`.
- Configuración JDBC: `co.venterapp.config.ConexionBaseDatos`.
- Controlador: `co.venterapp.web.ProductoServlet`.
- Vista: `src/main/webapp/WEB-INF/vistas/productos.jsp`.

## Trazabilidad inicial
- Requisito de gestión de productos/inventario → formulario y tabla de productos.
- Caso de uso Registrar producto → formulario POST y DAO.insertar.
- Caso de uso Consultar productos → GET y DAO.consultarTodos.
- Caso de uso Actualizar producto → enlace de edición GET y envío POST.
- Caso de uso Eliminar producto → formulario POST con confirmación.
- Diagrama de clases → Producto, ProductoDAO/ProductoDAOImpl, ProductoServlet.
- Prototipos → la JSP es una interfaz inicial y debe compararse con los prototipos previos de VenterApp.

## Plan de pruebas
1. Compilación Maven.
2. Conexión a MariaDB.
3. Consulta GET de productos existentes.
4. Registro de producto de prueba.
5. Edición de producto de prueba.
6. Eliminación de producto de prueba, verificando dependencias.
7. Validación de entradas vacías, precio inválido e ID no numérico.
8. Revisión del historial Git.

## Limitaciones y mejoras siguientes
- Los IDs de categoría/proveedor/vendedor se ingresan numéricamente; reemplazarlos por listas desplegables alimentadas por la base de datos.
- Mejorar los mensajes de error para que no expongan detalles internos en una instalación pública.
- Configurar credenciales fuera del código.
- Agregar pruebas automatizadas y protección CSRF antes de un despliegue real.
- El módulo no implementa ventas, descuentos automáticos de inventario, reportes ni sincronización offline; son funciones del alcance general y requieren historias/iteraciones propias.

## Registro de ejecución
Completar con fecha, equipo, versión de Java/Tomcat, resultado real de cada prueba y capturas. No declarar una prueba exitosa hasta ejecutarla.

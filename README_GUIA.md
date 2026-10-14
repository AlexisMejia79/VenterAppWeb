# VenterAppWeb — guía de instalación

## Qué contiene
Proyecto web Maven independiente del proyecto de consola `VenterAppProductos`. Usa Java 21 como versión de compilación, Jakarta Servlet 6, JSP/JSTL, MariaDB JDBC y Tomcat 10.1. Incluye alta, consulta, edición y eliminación de productos.

## Antes de comenzar
1. Conserva intacta la carpeta original `VenterAppProductos`.
2. Asegúrate de tener JDK instalado, Maven integrado en NetBeans, XAMPP/MariaDB y Tomcat 10.1.
3. En phpMyAdmin importa `venterapp_db.sql` del ZIP original si la base aún no existe. No vuelvas a importar sobre una base con datos que quieras conservar.
4. Verifica que existan la categoría, el proveedor y el vendedor con ID 1. El dump incluido contiene esos registros.
5. Revisa `ConexionBaseDatos.java`; si tu usuario MariaDB tiene contraseña, cambia `CLAVE` localmente. No publiques credenciales.

## Abrir en NetBeans
1. Descomprime el archivo del proyecto.
2. En NetBeans elige File > Open Project y selecciona la carpeta `VenterAppWeb` que contiene `pom.xml`.
3. Agrega Tomcat 10.1 desde Tools > Servers si aún no aparece.
4. Clic derecho al proyecto > Clean and Build. Debe terminar con BUILD SUCCESS.
5. Clic derecho > Run. Abre `/venterapp-web/` o `/venterapp-web/productos` en el puerto que muestre NetBeans.

## Pruebas
- GET `/productos`: lista los productos.
- POST `/productos` con accion=registrar: crea producto.
- GET `/productos?accion=editar&id=1`: carga edición.
- POST con accion=actualizar e idProducto: actualiza.
- POST con accion=eliminar e idProducto: elimina.

Prueba primero con un producto no esencial. La eliminación es real y puede estar restringida por inventario u otras relaciones; no elimines productos de uso real sin copia de seguridad.

## Notas importantes
- Las columnas se basan en `producto.sql`/`venterapp_db.sql` del ZIP original: id_categoria, id_proveedor, id_vendedor, nombre, categoria, descripcion, precio, codigo_barras y estado.
- Los campos de IDs se muestran como números para mantener el ejemplo sencillo. La mejora recomendada es cargarlos en listas desplegables consultando las tablas categoria, proveedor y vendedor.
- No se incluyen aquí los diagramas ni historias del enlace compartido, porque el ZIP recibido no los contiene y la página compartida no expone el texto de la conversación al lector web. Usa los artefactos previos como referencia al redactar la trazabilidad.
- Git no sube la base de datos ni credenciales; versiona el código fuente.

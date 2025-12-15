A Milímetros de Tu Hogar – Examen App
Descripción del Proyecto
A Milímetros de Tu Hogar es un sistema desarrollado como proyecto académico, basado en una arquitectura de microservicios para el backend y un frontend en Kotlin. El objetivo del sistema es apoyar a una organización dedicada a la adopción de animales y a la venta de productos para mascotas.
El backend está construido en Java 21 con Spring Boot y permite gestionar usuarios, animales en adopción, productos de una tienda, un carrito de compras y el flujo de orden/compra, manteniendo una separación de responsabilidades mediante microservicios independientes que se comunican entre sí por API REST.

Integrantes
Marco Bona
Lorena Ormeño

Arquitectura del Sistema
Backend: Microservicios Spring Boot
Frontend: Kotlin
Comunicación entre servicios: REST (WebClient)
Persistencia: Spring Data JPA + Hibernate
Base de datos: MySQL (Laragon)
Documentación: Swagger / OpenAPI 3

Tecnologías Utilizadas
Java 21
Spring Boot
Spring Web
Spring Data JPA
Hibernate ORM
MySQL (Laragon)
Swagger / OpenAPI 3
Spring Security
BCrypt
Jakarta Validation
Lombok
Android Studio
Microservicios Implementados
usuarios
catalogo
animales
carrito
orden
formulario

Funcionalidades Implementadas
Gestión de Usuarios
Registro de usuarios
Inicio de sesión
Gestión de roles (usuario / administrador)
Obtención de usuarios por ID
Obtención de usuarios por correo electrónico
Actualización de perfil de usuario
Creación automática de un usuario administrador al iniciar el microservicio
Gestión de Animales
Registro de animales
Listado de animales
Listado de animales disponibles
Listado de animales adoptados
Obtención de animales por ID
Búsqueda de animales por nombre
Filtro por especie
Actualización de animales
Eliminación de animales
Marcado como adoptado
Gestión de imágenes de animales
Validación de administrador mediante consumo del microservicio de usuarios
Gestión de Productos
Registro de productos
Listado de productos
Obtención de productos por ID
Búsqueda de productos por nombre
Filtro por categoría
Actualización de productos
Eliminación de productos
Gestión de imágenes de productos
Validaciones de negocio (precio mínimo, campos obligatorios)
Validación de administrador mediante consumo del microservicio de usuarios
Gestión de Carrito
Obtención del carrito por usuario
Obtención de detalles del carrito (usuario + items + total)
Agregar productos al carrito
Actualizar cantidad de un item
Eliminar item del carrito
Vaciar carrito
Calcular total del carrito
Validación de usuario y producto mediante consumo de microservicios externos
Gestión de Orden
Creación de orden a partir del carrito
Listado de órdenes por usuario
Obtención de orden por ID
Actualización de estado de la orden
Validación de usuario mediante consumo del microservicio de usuarios
Integración con carrito para generar el detalle de compra
Gestión de Formulario
Registro de formularios asociados al usuario
Listado de formularios
Obtención de formulario por ID
Actualización de formulario
Eliminación de formulario
Validación de usuario mediante consumo del microservicio de usuarios

Endpoints Implementados

Microservicio Usuarios
POST /auth/register
POST /auth/login
GET /auth/usuarios
GET /auth/usuarios/{id}
GET /auth/usuario/correo/{correo}
PUT /auth/usuarios/{id}

Microservicio Animales
GET /animales
GET /animales/disponibles
GET /animales/adoptados
GET /animales/{id}
GET /animales/especie/{especie}
GET /animales/buscar
POST /animales
PUT /animales/{id}
PUT /animales/{id}/adoptar
POST /animales/{id}/imagen
GET /animales/{id}/imagen
DELETE /animales/{id}

Microservicio Productos (Catálogo)
GET /productos
GET /productos/{id}
GET /productos/categoria/{categoria}
GET /productos/buscar
POST /productos
PUT /productos/{id}
POST /productos/{id}/imagen
GET /productos/{id}/imagen
DELETE /productos/{id}

Microservicio Carrito
GET /carrito/usuario/{usuarioId}
GET /carrito/usuario/{usuarioId}/detalles
POST /carrito/agregar
PUT /carrito/item/{itemId}
DELETE /carrito/item/{itemId}
DELETE /carrito/usuario/{usuarioId}
GET /carrito/usuario/{usuarioId}/total

Microservicio Orden
POST /ordenes
GET /ordenes/usuario/{usuarioId}
GET /ordenes/{id}
PUT /ordenes/{id}/estado

Microservicio Formulario
POST /formularios
GET /formularios
GET /formularios/{id}
PUT /formularios/{id}
DELETE /formularios/{id}

Endpoints Externos Consumidos entre Microservicios

Usuarios:
GET /auth/usuarios/{id}
GET /auth/usuario/correo/{correo}

Catálogo:
GET /productos/{id}

Carrito:
GET /carrito/usuario/{usuarioId}
GET /carrito/usuario/{usuarioId}/detalles
GET /carrito/usuario/{usuarioId}/total

Documentación de la API
Swagger disponible por microservicio:
http://localhost:{8090}/doc/swagger-ui/index.html hay hasta el puerto 8095

Instrucciones para Ejecutar el Proyecto
Clonar el repositorio del proyecto.
Crear las bases de datos MySQL correspondientes a cada microservicio (Laragon).
Configurar credenciales y nombre de base de datos en cada application.properties.
Ejecutar los microservicios Spring Boot.
Acceder a Swagger de cada microservicio para validar endpoints.
Ejecutar el frontend Kotlin desde Android Studio.

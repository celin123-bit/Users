 Proyecto Final — Sistema de Gestión de Productos con Usuarios y Roles
Contexto
La empresa ficticia CompuStore requiere un sistema compuesto por dos microservicios que permita autenticación de usuarios con JWT y gestión de productos con control de acceso por roles.

Objetivos del sistema
Permitir que los usuarios se registren y autentiquen mediante JWT.
Definir roles:
ADMIN → puede crear, editar y eliminar productos.
CLIENT → puede listar y ver detalles de productos, pero no modificarlos.
Proteger los endpoints con Spring Security y validación de tokens entre microservicios.
🖥 Microservicio 1: users-service
Endpoints obligatorios
POST /api/users/register → Registro de usuario.
POST /api/users/login → Autenticación y generación de token JWT.
GET /api/users/profile → Obtiene el perfil del usuario autenticado (requiere token válido).
Requisitos técnicos
Spring Boot con Spring Security.
Autenticación con JWT.
Base de datos MySQL para guardar usuarios.
Roles: ADMIN y CLIENT.
Endpoint /profile solo accesible si el token es válido.
Microservicio 2: products-service
Endpoints obligatorios
GET /api/products → Lista todos los productos (rol: CLIENT o ADMIN).
GET /api/products/{id} → Muestra detalle de un producto (rol: CLIENT o ADMIN).
POST /api/products → Crea un producto (rol: ADMIN).
PUT /api/products/{id} → Actualiza un producto (rol: ADMIN).
DELETE /api/products/{id} → Elimina un producto (rol: ADMIN).
Requisitos técnicos
Spring Boot con Spring Security.
Validar JWT emitido por users-service.
Base de datos MySQL con tabla de productos.
Seguridad y JWT
El token JWT se genera en el users-service.
El products-service debe validar el token antes de procesar cualquier petición.
Si el token es inválido o el usuario no tiene permisos, responder con:
401 Unauthorized
403 Forbidden

EJEMPLO
<img width="487" height="491" alt="image" src="https://github.com/user-attachments/assets/aab5b8ac-3ca7-4e36-ac80-a8f187abbbf8" />
<img width="482" height="547" alt="image" src="https://github.com/user-attachments/assets/325e9303-27ca-49d9-acb7-5048be039622" />


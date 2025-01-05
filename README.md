Proyecto: Sistema de Gestión de Tareas basado en Microservicios
Descripción
Este proyecto consta de siete microservicios diseñados para gestionar un sistema de tareas utilizando arquitectura de microservicios. Incluye autenticación mediante JWT, configuración centralizada, descubrimiento de servicios, y enrutamiento mediante un API Gateway.
________________________________________
Microservicios
1.	service-config
https://github.com/kelvin-Penafiel/service-configuration.git  
Microservicio encargado de almacenar los archivos de configuración (.properties) de los demás microservicios.
2.	config-server
https://github.com/kelvin-Penafiel/config-server.git 
Microservicio que actúa como un servidor de configuración centralizado. Consulta y sirve los archivos de configuración almacenados en service-config.
3.	discovery-server
 https://github.com/kelvin-Penafiel/discovery-service.git 
Implementación de Eureka para el descubrimiento dinámico de microservicios.
4.	api-gateway
https://github.com/kelvin-Penafiel/api-gateway.git 
Actúa como puerta de entrada para las solicitudes a los microservicios. Incluye funciones de enrutamiento y validación de tokens de acceso.
5.	auth-service
https://github.com/kelvin-Penafiel/auth-service.git 
Microservicio para la autenticación de usuarios y generación de tokens JWT.
6.	gestion-usuarios
https://github.com/kelvin-Penafiel/gestion-usuarios.git 
Microservicio para gestionar usuarios del sistema, incluyendo CRUD de usuarios.
7.	gestion-tareas
https://github.com/kelvin-Penafiel/gestion-tareas.git 
Microservicio para gestionar tareas, incluyendo creación, actualización y eliminación de tareas.
________________________________________
Tecnologías Utilizadas
•	Spring Boot: Framework principal para cada microservicio.
•	Spring Cloud Config: Configuración centralizada.
•	Spring Cloud Gateway: Enrutamiento y gateway API.
•	Spring Security: Seguridad y autenticación.
•	Eureka Server/Client: Descubrimiento de servicios.
•	JWT (JSON Web Tokens): Autenticación y autorización.
•	PostgreSQL: Base de datos para los microservicios.
________________________________________

Estructura del Proyecto
├── service-config/
│   ├── gestion-usuarios.properties  
│   ├── gestion-tareas.properties  
│   ├── application.properties  
│   └── ...  
├── config-server/  
├── discovery-server/  
├── api-gateway/  
├── auth-service/  
├── gestion-usuarios/  
├── gestion-tareas/  
└── README.md  
________________________________________
Instalación
Prerrequisitos
1.	Java 17 o superior
2.	Maven
3.	Docker (opcional para contenedores)
4.	PostgreSQL Server
Configuración Inicial
1.	Clona este repositorio:
bash
Copiar código
git clone https://github.com/kelvin-Penafiel?tab=repositories  
cd nombre-del-repositorio  
2.	Configura las bases de datos requeridas para los microservicios:
o	gestion-usuarios-db
o	gestion-tareas-db
3.	Modifica los archivos de configuración en service-config según tus credenciales y entorno.
________________________________________
Instrucciones para Levantar el Proyecto
1. Levantar el service-config
Este servicio almacena los archivos .properties.
bash
Copiar código
cd service-config  
mvn spring-boot:run  
2. Levantar el config-server
Se conecta a service-config para servir configuraciones centralizadas.
bash
Copiar código
cd config-server  
mvn spring-boot:run  
3. Levantar el discovery-server
Inicia el servidor Eureka para el descubrimiento de servicios.
bash
Copiar código
cd discovery-server  
mvn spring-boot:run  
4. Levantar el api-gateway
Se encarga del enrutamiento y la validación de tokens JWT.
bash
Copiar código
cd api-gateway  
mvn spring-boot:run  
5. Levantar el auth-service
Genera y valida tokens JWT para autenticación.
bash
Copiar código
cd auth-service  
mvn spring-boot:run  
6. Levantar gestion-usuarios y gestion-tareas
Ejecuta los servicios de gestión de usuarios y tareas.
bash
Copiar código
cd gestion-usuarios  
mvn spring-boot:run  
bash
Copiar código
cd gestion-tareas  
mvn spring-boot:run  
________________________________________
Ejemplo de Uso
1. Registrar un Usuario
Endpoint: POST /auth/register
json
Copiar código
{  
  "username": "test",  
  "password": "12345"  
}  
2. Autenticación de Usuario
Endpoint: POST /auth/login
json
Copiar código
{  
 "username": "test",  
  "password": "12345"  
}  
3. Gestión de Tareas
•	Crear una tarea: POST / http://localhost:8080/api/tareas
•	Listar tareas: GET /http://localhost:8080/api/tareas
•	Actualizar tarea: PUT /http://localhost:8080/api/tareas/62
•	Eliminar tarea: DELETE /http://localhost:8080/api/tareas/62
•	Actualizar un unico campo tarea: Patch /http://localhost:8080/api/tareas/62/estado?nuevoEstado=InReview
•	Actualizar tarea: Put / http://localhost:8080/api/tareas/62

5. Gestión de Usuarios
•	Crear una usarios: POST / http://localhost:8080/api/usuarios
•	Listar usuarios: GET /http://localhost:8080/api/usuarios
•	Actualizar usuarios: PUT /http://localhost:8080/api/usuarios/6
•	Eliminar usuarios: DELETE /http://localhost:8080/api/usuarios/6
•	Actualizar usuarios: Put / http://localhost:8080/api/usuarios/6

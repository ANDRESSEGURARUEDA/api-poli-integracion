# Proyecto de Integración Continua: API REST y Base de Datos en Docker

Este proyecto muestra cómo desplegar una API REST desarrollada en Spring Boot y una base de datos MySQL utilizando Docker. Los servicios están contenedorizados y se comunican entre ellos a través de una red compartida de Docker, permitiendo un entorno de desarrollo reproducible y fácil de gestionar.

## Tabla de Contenidos

- [Requisitos](#requisitos)
- [Instalación y Configuración](#instalación-y-configuración)
- [Comandos Docker](#comandos-docker)
- [Validación de la Conexión](#validación-de-la-conexión)
- [Evidencias](#evidencias)
- [Referencias](#referencias)

## Requisitos

- **Docker Desktop**: Asegúrate de tener Docker Desktop instalado. Puedes descargarlo desde [Docker](https://www.docker.com/products/docker-desktop).

## Instalación y Configuración

1. **Clona el Repositorio**:
   ```bash
   git clone https://github.com/ANDRESSEGURARUEDA/api-poli-integracion.git
   cd api-poli-integracion
   ```

2. **Crea el Archivo Dockerfile** para la API:
   Dentro del repositorio encontrarás un archivo `Dockerfile` que configura la API REST.

3. **Configura las Propiedades de la Base de Datos**:
   - En el archivo `application.properties` de la API, asegúrate de configurar la URL de la base de datos:
     ```properties
     spring.datasource.url=jdbc:mysql://<nombre-del-contenedor>/appday
     ```

## Comandos Docker

1. **Construye y Lanza los Contenedores**:
   - Asegúrate de ejecutar los comandos en el archivo `ComandsDocker.txt` para construir y lanzar los contenedores.
   
2. **Validación de la Red**:
   - Para comprobar la conexión entre los contenedores, usa:
     ```bash
     docker network inspect network-api-mysql
     ```

3. **Verificación de Imágenes y Contenedores**:
   - Verifica que las imágenes y contenedores estén activos y funcionando:
     ```bash
     docker images
     docker ps
     ```

## Validación de la Conexión

1. **Acceso a la Base de Datos**:
   - Conéctate a la base de datos en el contenedor de MySQL y ejecuta los queries necesarios para crear y visualizar la estructura de la base de datos.

2. **Prueba la API con Postman**:
   - Realiza peticiones HTTP a la API desde Postman para validar que puede acceder y consultar la base de datos.

3. **Revisión de Logs**:
   - Verifica en los logs de Docker que la API se haya conectado exitosamente a la base de datos.

## Evidencias

Incluye capturas de pantalla de:
- Los contenedores en ejecución
- La conexión a la base de datos desde la consola de Docker
- Las peticiones exitosas en Postman y la respuesta de la API

## Referencias

- Documentación de Docker: [Docker Docs](https://docs.docker.com/)
- Repositorio en GitHub para el proyecto de ejemplo: [api-poli-integracion](https://github.com/ANDRESSEGURARUEDA/api-poli-integracion)

---

Este README proporciona una guía completa para cualquier persona que desee comprender y reproducir el entorno del proyecto.

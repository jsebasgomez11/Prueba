#  Prueba Técnica Backend -- Franquicias

API REST desarrollada con **Spring Boot 3, Java 21, JPA (Hibernate)** y
**MySQL**, siguiendo principios de **Clean Architecture** y buenas
prácticas de diseño.\
La solución se ejecuta de forma reproducible usando **Docker y Docker
Compose**.

------------------------------------------------------------------------

##  Tecnologías

-   Java 21\
-   Spring Boot 3\
-   Spring Data JPA (Hibernate)\
-   MySQL 8\
-   Docker & Docker Compose\
-   Gradle\
-   JUnit 5 / Mockito (tests unitarios)

------------------------------------------------------------------------

##  Arquitectura

Estructura basada en capas (inspirada en Clean Architecture):

    com.empresa.franquicia
    ├── controller        # Capa de entrada (API REST)
    ├── service           # Lógica de negocio
    ├── domain            # Entidades de dominio
    ├── repository        # Acceso a datos (JPA)
    ├── dto               # Objetos de transferencia
    └── exception         # Excepciones y manejadores globales

Principios aplicados: - Separación de responsabilidades\
- DTOs para evitar exponer entidades JPA\
- Manejo centralizado de excepciones\
- Código legible y mantenible

------------------------------------------------------------------------

## 🐳 Ejecución con Docker (Recomendado)

### Requisitos

-   Docker Desktop instalado y corriendo

### Pasos

Desde la raíz del proyecto:

``` bash
docker compose up --build
```

Esto levantará: - MySQL en `localhost:3306` - API en
`http://localhost:8080`

Para detener:

``` bash
docker compose down
```

------------------------------------------------------------------------

## Ejecución local (sin Docker)

Requisitos: - Java 21 - MySQL corriendo en `localhost:3306`

Configura `application.yml` (ya viene preparado con valores por defecto)
y ejecuta:

``` bash
./gradlew bootRun
```

------------------------------------------------------------------------

##  Endpoints principales

> Los endpoints pueden ajustarse según la implementación final.

### Franquicias

-   `POST /franchises` -- Crear franquicia\
-   `GET /franchises` -- Listar franquicias\
-   `GET /franchises/{franchiseId}/top-products` -- Obtener el producto
    con mayor stock por sucursal

### Sucursales

-   `POST /branches` -- Crear sucursal

### Productos

-   `POST /products` -- Crear producto\
-   `PUT /products/{productId}/stock` -- Actualizar stock

------------------------------------------------------------------------

##  Pruebas

Ejecución de pruebas unitarias:

``` bash
./gradlew test
```

Las pruebas cubren principalmente la lógica de negocio en la capa de
servicios, utilizando mocks de repositorios.

------------------------------------------------------------------------

## Base de Datos

-   Motor: MySQL 8\
-   Esquema: `franquicias`\
-   Las tablas se crean automáticamente usando Hibernate
    (`ddl-auto=update`)

Variables de entorno utilizadas en Docker:

-   `DB_HOST`
-   `DB_PORT`
-   `DB_NAME`
-   `DB_USER`
-   `DB_PASSWORD`

------------------------------------------------------------------------

## Consideraciones

-   La solución utiliza JPA para la persistencia en MySQL.\
-   Docker Compose permite levantar todo el entorno de forma
    reproducible.\
-   No se despliega en nube real (según alcance de la prueba técnica).

------------------------------------------------------------------------

##  Notas finales

Este proyecto fue desarrollado como parte de una **prueba técnica
backend**, priorizando:

-   Claridad del diseño\
-   Buenas prácticas de arquitectura\
-   Reproducibilidad del entorno\
-   Mantenibilidad del código

# 🌐 EcoMarket - API Gateway

Punto de entrada centralizado para enrutar solicitudes a los microservicios del sistema **EcoMarket**, desarrollado con **Spring Cloud Gateway** y configurado con YAML.

---

## 📋 Tabla de Contenidos

- [📖 Descripción](#-descripción)
- [🛠 Tecnologías](#-tecnologías)
- [⚙️ Configuración](#-configuración)
- [🚀 Instalación y Ejecución](#-instalación-y-ejecución)
- [🛣 Rutas Configuradas](#-rutas-configuradas)
- [📊 Ejemplos de Uso](#-ejemplos-de-uso)
- [🔗 Enlaces Relacionados](#-enlaces-relacionados)

---

## 📖 Descripción

Este API Gateway actúa como un enrutador para los microservicios del sistema EcoMarket. Ofrece:

- Enrutamiento centralizado
- Configuración declarativa vía `application.yml`
- Escalabilidad y mantenimiento desacoplado
- Soporte para múltiples microservicios como Productos, Inventario y Usuarios

---

## 🛠 Tecnologías

- **Java:** OpenJDK 17  
- **Frameworks:** Spring Boot 3.2.5, Spring Cloud Gateway (2023.0.1)  
- **Gestión de Dependencias:** Maven 3.9.9  


---

## ⚙️ Configuración

### `application.yml` (rutas)

```yaml
server:
  port: 8080

spring:
  application:
    name: api-gateway
  cloud:
    gateway:
      routes:
        - id: productos
          uri: http://localhost:8081
          predicates:
            - Path=/api/v1/productos/**
        - id: inventario
          uri: http://localhost:8081
          predicates:
            - Path=/api/v1/inventario/**
        - id: usuarios
          uri: http://localhost:8082
          predicates:
            - Path=/api/v1/usuarios/**
```
# Variables de entorno
| Variable               | Descripción               | Valor por defecto         |
|------------------------|---------------------------|--------------------------|
| SERVER_PORT            | Puerto del API Gateway    | 8080                     |
| PRODUCTOS_SERVICE_URL  | URL del servicio de productos | http://localhost:8081 |
| USUARIOS_SERVICE_URL   | URL del servicio de usuarios  | http://localhost:8082 |

---

## 🚀 Instalación y Ejecución
### Prerrequisitos
-Java 17+

-Maven 3.6+

-Microservicios correspondientes en ejecución

### 1. Clonar el repositorio
```bash
git clone https://github.com/tuusuario/api-gateway.git
cd api-gateway
```
### 2. Compilar el proyecto
```bash
./mvnw clean compile
# o con Maven instalado
mvn clean compile
```
### 3. Ejecutar la aplicación
```bash
./mvnw spring-boot:run

# o con el JAR generado
java -jar target/api-gateway-0.0.1-SNAPSHOT.jar
```
---

## 🛣 Rutas Configuradas
Ruta	Servicio Destino	Puerto	Descripción
/api/v1/productos/**	Servicio de Productos	8081	Gestión de productos
/api/v1/inventario/**	Servicio de Inventario	8081	Gestión de inventario
/api/v1/usuarios/**	Servicio de Usuarios	8082	Gestión de usuarios

---

## 📊 Ejemplos de Uso
```bash
# Obtener lista de productos
curl -X GET http://localhost:8080/api/v1/productos/lista
```
```bash
# Obtener información de usuario
curl -X GET http://localhost:8080/api/v1/usuarios/123
```
```bash
# Consultar inventario
curl -X GET http://localhost:8080/api/v1/inventario/producto/456
```
---
## 🔗 Enlaces Relacionados

- [Repositorio Microservicio Productos](https://github.com/JorgeToledoIporre/producto-ms)  
  Documentación completa del microservicio Productos, con API y ejemplos.

<div align="center">

  <h1>menu-service</h1>

  <p align="center">
    <strong>Cristian Camilo Ortiz Sánchez</strong><br />
    DOSW 1 · Semana 14<br />
    Escuela Colombiana de Ingeniería Julio Garavito<br />
    cristian.ortiz-s@mail.escuelaing.edu.co
  </p>

  <p align="center">
    <strong>Arepa Express · API Gateway y RabbitMQ en Azure</strong><br />
    <em>Microservicio que expone el menú de la arepería.</em>
  </p>

</div>

---

## Descripción

- Devuelve la lista de arepas disponibles con su id, nombre y precio.
- Es el servicio más simple del sistema: solo responde consultas y no depende de ningún otro componente.
- Se despliega en Azure Container Apps y se publica a través del API Gateway (Azure API Management) bajo el prefijo `/menu-api`.

## Tecnologías

- Java 21
- Spring Boot 3.5.9 (Spring Web)
- Maven
- Docker

## Endpoints

| Método | Ruta | Descripción |
|---|---|---|
| `GET` | `/menu` | Lista el menú de arepas |

**Ejemplo de respuesta:**

```json
[
  { "id": 1, "nombre": "Arepa de choclo con queso", "precio": 9000 },
  { "id": 2, "nombre": "Arepa rellena de pollo", "precio": 11000 },
  { "id": 3, "nombre": "Arepa de huevo", "precio": 7000 }
]
```

A través del gateway: `GET https://arepas-gw-<alias>.azure-api.net/menu-api/menu` (requiere el header `Ocp-Apim-Subscription-Key`).

## Docker

```bash
mvn -q package -DskipTests
docker build -t menu-service .
docker run -p 8080:8080 menu-service
```

## Contexto

Forma parte de Arepa Express junto con `pedidos-service`, `cocina-service` y `notificaciones-service`.

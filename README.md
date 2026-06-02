# PostContenido 2 - Unidad 7

## API REST CRUD con Spring Boot

### Autor

Camilo Sánchez

### Descripción del Proyecto

Este proyecto corresponde al laboratorio PostContenido 2 de la Unidad 7 de Programación Web.

El objetivo fue desarrollar una API REST completa utilizando Spring Boot y `@RestController`, implementando operaciones CRUD sobre una colección de productos en memoria y utilizando los códigos HTTP adecuados para cada operación.

La API permite:

* Listar productos.
* Buscar productos por ID.
* Crear productos.
* Actualizar productos.
* Eliminar productos.
* Manejar errores mediante `@RestControllerAdvice`.

---

## Arquitectura del Proyecto

```text
Cliente (Postman / Navegador)
            |
            v
+----------------------+
| ProductoApiController|
+----------------------+
            |
            v
+----------------------+
|   ProductoService    |
+----------------------+
            |
            v
+----------------------+
|      Producto        |
+----------------------+
```

---

## Estructura del Proyecto

```text
src
└── main
    ├── java
    │   └── com.universidad.apiproductos
    │       ├── controller
    │       ├── model
    │       └── service
    │
    └── resources
        └── application.properties
```

---

## Controlador REST

Se implementó la clase:

```java
@RestController
@RequestMapping("/api/productos")
public class ProductoApiController
```

Utilizando `ResponseEntity` para devolver códigos HTTP apropiados según el resultado de cada operación.

Códigos implementados:

| Operación | Código         |
| --------- | -------------- |
| GET       | 200 OK         |
| POST      | 201 Created    |
| PUT       | 200 OK         |
| DELETE    | 204 No Content |
| Error     | 404 Not Found  |

---

```bash
mvn spring-boot:run
```

---

## Flujo de Pruebas con Postman

### 1. Listar productos

```http
GET http://localhost:8080/api/productos
```

Resultado esperado:

```http
200 OK
```

---

### 2. Crear producto

```http
POST http://localhost:8080/api/productos
```

Body:

```json
{
  "nombre": "Monitor",
  "descripcion": "Monitor 27 pulgadas 4K",
  "precio": 499.99
}
```

Resultado esperado:

```http
201 Created
```

---

### 3. Actualizar producto

```http
PUT http://localhost:8080/api/productos/3
```

Resultado esperado:

```http
200 OK
```

---

### 4. Eliminar producto

```http
DELETE http://localhost:8080/api/productos/3
```

Resultado esperado:

```http
204 No Content
```

---

### 5. Verificar producto eliminado

```http
GET http://localhost:8080/api/productos/3
```

Resultado esperado:

```http
404 Not Found
```

---

## Conclusiones

Se desarrolló una API REST CRUD completa utilizando Spring Boot y `@RestController`. Se implementaron correctamente los métodos HTTP GET, POST, PUT y DELETE utilizando `ResponseEntity` para devolver códigos HTTP apropiados. Además, se añadió un manejador global de excepciones mediante `@RestControllerAdvice`, mejorando la calidad de las respuestas de error y siguiendo buenas prácticas para el desarrollo de APIs REST.

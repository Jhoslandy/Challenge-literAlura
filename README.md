# Bibliura: Un Catálogo de Libros y Autores 📚✍️

¡Bienvenido a **Bibliura**, una aplicación de consola en Java para explorar y gestionar un catálogo de libros y autores! Este proyecto fue desarrollado con **Spring Boot** y **JPA** para interactuar de manera eficiente con la API de Gutendex y almacenar los datos en una base de datos local.

---

## Características Principales

**Bibliura** te permite realizar las siguientes acciones de forma intuitiva:

* **Búsqueda y registro de libros**: Busca libros por título a través de la API de Gutendex y guárdalos en tu base de datos local para consultarlos sin conexión.
* **Catálogo completo**: Visualiza listas de todos los libros y autores registrados en tu base de datos.
* **Gestión inteligente de autores**: El programa evita duplicar autores. Al listar los libros de un autor, todos los títulos se muestran bajo una única entrada para una mejor organización.
* **Filtro por idioma**: Busca y muestra libros filtrados por su idioma.
* **Autores vivos por año**: ¿Tienes curiosidad por saber qué autores estaban vivos en un año específico? Con esta funcionalidad puedes averiguarlo fácilmente.

---

## Estructura del Proyecto

El proyecto está organizado en una arquitectura de capas clara y modular:

* `model`: Contiene las **entidades** principales (`Autor.java`, `Libro.java`, `Idioma.java`) que se mapean a la base de datos, así como los `records` que modelan las respuestas de la API (`DatosLibro.java`, `DatosAutor.java`).
* `repository`: Incluye las interfaces de los **repositorios** (`LibroRepository.java`, `AutorRepository.java`) que extienden `JpaRepository` para la capa de acceso a datos.
* `principal`: La clase principal (`Principal.java`) gestiona el menú interactivo y la lógica de negocio para la interacción con el usuario.
* `service`: Contiene la lógica de negocio, incluyendo la clase para consumir la **API** (`ConsumoAPI.java`) y la clase para convertir datos JSON a objetos Java (`ConvierteDatos.java`).

---

## Relaciones de la Base de Datos

### `Libro` y `Autor`

Se estableció una relación **`ManyToOne`** de `Libro` a `Autor`, lo que permite que múltiples libros se asocien con un único autor. Para mantener la base de datos limpia, la aplicación primero verifica si el autor ya existe antes de registrar un nuevo libro, evitando así duplicaciones.

### `Libro` e `Idioma`

Para gestionar los idiomas, se utilizó la anotación `@ElementCollection` en la entidad `Libro`, lo que permite almacenar una lista de idiomas. El idioma se representa como un `enum`, mapeando los códigos de idioma de la API a su nombre completo, lo que simplifica las búsquedas.

---

## Tecnologías Utilizadas

Este proyecto fue construido utilizando herramientas y tecnologías robustas para garantizar un rendimiento óptimo:

| **Tecnología** | **Descripción** |
| :--- | :--- |
| **Java 21** | Lenguaje de programación. |
| **Spring Boot** | Framework que simplifica el desarrollo de aplicaciones. |
| **Spring Data JPA** | Abstrae la capa de persistencia con el uso de repositorios. |
| **Hibernate** | Implementación de JPA que realiza el mapeo objeto-relacional (ORM). |
| **Maven** | Herramienta para la gestión de dependencias y construcción del proyecto. |
| **H2 Database** | Base de datos en memoria para un desarrollo ágil. |
| **Jackson** | Biblioteca para el manejo y mapeo de datos JSON. |

---

## Autor

Este proyecto fue creado por **Jose Aruquipa**.

¡Gracias por revisar este proyecto! Si tienes alguna pregunta o sugerencia, no dudes en contactar al autor.

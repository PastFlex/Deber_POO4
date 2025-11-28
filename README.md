# 🎬 Sistema de Gestión de Contenido Audiovisual

## 📝 Descripción General del Proyecto

Este proyecto es un sistema robusto desarrollado en **Java** para la **gestión de un catálogo de contenido audiovisual** (Películas, Series de TV, Cortometrajes, Podcasts, etc.).

El diseño del sistema se centra en la aplicación rigurosa de principios de **Ingeniería de Software** avanzados, incluyendo:

* **Principios SOLID** para un diseño extensible y mantenible.
* El **Patrón de Diseño Modelo-Vista-Controlador (MVC)** para la separación de responsabilidades.
* **Código Limpio** y modularidad.
* Uso de **Pruebas Unitarias** con JUnit y Mockito para asegurar la calidad.

---

## 🚀 Características y Estándares de Ingeniería

### 1. Persistencia de Datos y Manejo de Archivos

Se implementó una funcionalidad sólida para la persistencia del catálogo a través de un archivo **CSV (`contenidos.csv`)**:

* **Lectura:** Inicializa el sistema leyendo y analizando los datos del CSV para crear los objetos `ContenidoAudiovisual`.
* **Escritura:** Guarda el estado actual del catálogo de vuelta al archivo CSV.
* **Gestión de Errores:** Incluye un manejo controlado de excepciones (`IOException`, `FileNotFoundException`) para garantizar un funcionamiento seguro frente a errores de I/O.

### 2. Principios SOLID: Un Diseño Escalar

La arquitectura del proyecto está diseñada para ser **flexible y fácil de escalar**:

* **✅ SRP (Principio de Responsabilidad Única):** Las responsabilidades están bien delimitadas: `ContentService` (lógica de negocio), `ConsoleView` (interfaz de usuario) y `CsvFileHandler` (persistencia).
* **✅ OCP (Principio Abierto/Cerrado):** La jerarquía de `ContenidoAudiovisual` permite añadir nuevos tipos de contenido (como un 'Documental') simplemente extendiendo la clase base, sin modificar el código existente.
* **✅ LSP (Principio de Sustitución de Liskov):** Todas las subclases de `ContenidoAudiovisual` pueden usarse indistintamente donde se espere la clase base.
* **✅ DIP (Principio de Inversión de Dependencias):** El servicio principal (`ContentService`) se acopla a la abstracción (`IFileHandler`), permitiendo un cambio en el mecanismo de persistencia sin alterar la lógica de negocio.



[Image of SOLID principles diagram]


---

### 3. Patrón de Diseño MVC

La estructura del proyecto separa claramente las preocupaciones:

| Componente | Clases/Paquetes | Responsabilidad |
| :--- | :--- | :--- |
| **Modelo** | `Pelicula`, `SerieDeTV`, etc. | Contiene los datos y la lógica de los objetos de contenido. |
| **Vista** | `ConsoleView` | Maneja la presentación (salida a consola) y la entrada del usuario. |
| **Controlador** | `ContentService` | Actúa como intermediario, orquestando la interacción entre el Modelo y la Vista. |



[Image of Model-View-Controller pattern diagram]


---

### 4. Código Limpio y Modularidad

El código ha sido refactorizado activamente para garantizar su **mantenibilidad y legibilidad**:

* **Nomenclatura Clara:** Se emplean nombres descriptivos (`ContentService`, `mostrarDetalles`) que indican el propósito de cada elemento.
* **Métodos Modulares:** Se refactorizó la lógica de visualización para que los métodos de detalle devuelvan un `String` formateado en lugar de imprimir directamente.
* **Refactorización de Constructores:** Se eliminaron parámetros redundantes y se estandarizó la inicialización en las clases de contenido especializadas.

### 5. Pruebas Unitarias de Calidad

Se implementaron pruebas exhaustivas para verificar la fiabilidad del código:

* **Frameworks:** Se utilizan **JUnit 5** como framework de pruebas y **Mockito** para la simulación (mocking) de dependencias.
* **Aislamiento de Lógica:** Las pruebas simulan el acceso al sistema de archivos (`IFileHandler`) para validar el comportamiento de la lógica de negocio en `ContentService` de forma aislada.

---

## 🛠️ Guía de Ejecución

### Requisitos

* **Java Development Kit (JDK) 16** o superior.
* Un IDE compatible (ej. **IntelliJ IDEA**).

### Pasos para Ejecutar la Aplicación

1.  **Clonar el Repositorio:**
    ```bash
    git clone <URL_DEL_REPOSITORIO>
    ```

2.  **Abrir en el IDE:**
    * En IntelliJ IDEA, selecciona **`Open`** y navega a la carpeta del proyecto clonado.

3.  **Configuración del JDK:**
    * Asegúrate de que el **`Project Structure`** (Menú `File`) tenga configurado el JDK 16 o superior.

4.  **Ejecutar:**
    * Ejecuta el método `main()` de la clase **`MainController.java`**.

### Ejecución de Pruebas Unitarias

1.  **Verificar Dependencias:**
    * Asegúrate de que las librerías necesarias para las pruebas estén en el classpath del proyecto: **`junit-jupiter-api`**, **`junit-jupiter-engine`**, **`mockito-core`**, `byte-buddy`, `byte-buddy-agent` y `objenesis`.

2.  **Ejecutar en IntelliJ IDEA:**
    * Navega a la clase **`ContentServiceTest.java`** dentro de la carpeta `test`.
    * Haz clic en el ícono de **"Play"** (ejecutar) junto a la clase o el método para iniciar las pruebas.

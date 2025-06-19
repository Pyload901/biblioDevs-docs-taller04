# Cómo usar BiblioDevs

Esta guía te mostrará paso a paso cómo aprovechar al máximo BiblioDevs para gestionar tu biblioteca personal.

## Instalación

BiblioDevs requiere un servidor web con PHP y MySQL. Sigue estos pasos según tu sistema operativo:

=== "Windows"

    ```bash
    # Usar XAMPP (recomendado)
    1. Descarga XAMPP desde https://www.apachefriends.org/
    2. Instala XAMPP y ejecuta Apache + MySQL
    3. Clona el repositorio en htdocs/
    git clone https://github.com/Pyload901/biblioDevs C:/xampp/htdocs/bibliodevs
    4. Importa la base de datos desde phpMyAdmin
    ```

=== "Linux"

    ```bash
    # Instalar dependencias
    sudo apt update
    sudo apt install apache2 php mysql-server php-mysql

    # Clonar el proyecto
    cd /var/www/html
    sudo git clone https://github.com/Pyload901/biblioDevs

    # Configurar permisos
    sudo chown -R www-data:www-data bibliodevs/
    sudo chmod -R 755 bibliodevs/
    ```

=== "macOS"

    ```bash
    # Usar Homebrew
    brew install php mysql

    # Iniciar servicios
    brew services start mysql
    php -S localhost:8000 -t /path/to/bibliodevs
    ```

!!! warning "Configuración de base de datos"
    No olvides crear la base de datos `bibliodevs` y importar el archivo `database.sql` incluido en el proyecto.

## Primeros pasos

### 1. Registro de usuario

Al acceder a BiblioDevs por primera vez, debes crear una cuenta:

1. Haz clic en "Registrarse"
2. Completa el formulario con tu información
3. Verifica tu email (si está configurado)
4. ¡Ya puedes comenzar a usar la aplicación!

### 2. Añadir tu primer libro

Una vez dentro de la aplicación:

1. Ve a la sección **"Mis Libros"**
2. Haz clic en **"Añadir Libro"**
3. Completa la información:
   - Título del libro
   - Autor(es)
   - Género
   - Fecha de lectura
   - Valoración (1-5 estrellas)
   - Notas personales

### 3. Explorar tus estadísticas

BiblioDevs genera automáticamente estadísticas de tu actividad lectora. Puedes ver:

- Libros leídos por mes/año
- Géneros favoritos
- Autores más leídos
- Tiempo promedio de lectura

## Funcionalidades avanzadas

### Gestión de listas

Organiza tus libros en listas personalizadas:

| Tipo de Lista | Descripción | Ejemplo |
|---------------|-------------|---------|
| **Leídos** | Libros que ya terminaste | "1984" por George Orwell |
| **Leyendo** | Libros en progreso | "El Quijote" por Cervantes |
| **Por leer** | Tu lista de deseos | "Sapiens" por Yuval Noah Harari |
| **Favoritos** | Tus mejores calificaciones | "Cien años de soledad" |
| **Recomendados** | Libros sugeridos por amigos | "The Pragmatic Programmer" |

### Búsqueda y filtros

Utiliza las opciones de búsqueda para encontrar libros específicos:

- **Búsqueda por texto**: Busca en títulos, autores y notas
- **Filtro por género**: Novela, Técnico, Biografía, etc.
- **Filtro por valoración**: Solo libros de 4-5 estrellas
- **Filtro por fecha**: Libros leídos en un periodo específico

### Exportar datos

BiblioDevs te permite exportar tu biblioteca en varios formatos:

```php
// Ejemplo de exportación via API
$libros = $biblioDevs->exportar([
    'formato' => 'json',
    'filtro' => 'leidos',
    'desde' => '2024-01-01'
]);
```

!!! tip "Consejo Pro"
    Usa la función de backup automático para mantener tus datos seguros. Ve a **Configuración > Backup** para programar copias de seguridad regulares.

## Configuración avanzada

### Personalización de la interfaz

1. Ve a **Configuración > Apariencia**
2. Selecciona tu tema preferido (claro/oscuro)
3. Ajusta el número de libros por página
4. Configura las columnas visibles en las listas

### Integración con APIs externas

BiblioDevs puede conectarse con servicios externos para obtener información de libros:

- **Google Books API**: Para obtener portadas y descripções
- **OpenLibrary**: Para datos bibliográficos adicionales
- **Goodreads**: Para importar valoraciones existentes

Para más detalles sobre configuración avanzada, consulta nuestra sección de [Preguntas Frecuentes](faq.md).

---

¿Tienes dudas? Visita nuestras [Preguntas Frecuentes](faq.md) o contacta con soporte técnico.

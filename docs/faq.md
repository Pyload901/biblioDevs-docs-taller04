# Preguntas Frecuentes

Aquí encontrarás respuestas a las preguntas más comunes sobre BiblioDevs.

## Instalación y configuración

### ¿Cuáles son los requisitos del sistema?

BiblioDevs requiere:

- **PHP 7.4 o superior**
- **MySQL 5.7 o superior** (o MariaDB 10.2+)
- **Apache o Nginx** como servidor web
- **2GB de RAM mínimo** (recomendado 4GB)
- **500MB de espacio en disco**

!!! info "Compatibilidad"
    BiblioDevs ha sido probado en Ubuntu 20.04+, CentOS 8+, Windows 10+ y macOS Big Sur+.

### ¿Puedo instalar BiblioDevs en un hosting compartido?

Sí, siempre que tu proveedor de hosting soporte:

- PHP con extensiones PDO y MySQL
- Acceso a base de datos MySQL
- Posibilidad de subir archivos via FTP/SFTP

Muchos hostings económicos como Hostinger, SiteGround o HostGator son compatibles.

### ¿Cómo migro mis datos desde otra aplicación?

BiblioDevs incluye importadores para:

| Aplicación | Formato soportado | Instrucciones |
|------------|-------------------|---------------|
| **Goodreads** | CSV export | Configuración > Importar > Seleccionar CSV |
| **LibraryThing** | Tab-delimited | Convertir a CSV primero |
| **Excel/Sheets** | CSV/XLSX | Mapear columnas manualmente |
| **Calibre** | XML export | Usar conversor incluido |
| **StoryGraph** | JSON export | Importador automático |

## Uso de la aplicación

### ¿Cómo agrego un libro sin ISBN?

Para libros sin ISBN (ej: manuscritos, ebooks personales):

1. Ve a **"Añadir Libro"**
2. Marca la casilla **"Libro sin ISBN"**
3. Completa manualmente todos los campos
4. Sube una imagen de portada personalizada (opcional)

### ¿Puedo añadir libros en lote?

¡Sí! BiblioDevs soporta importación masiva:

=== "Via CSV"

    ```csv
    titulo,autor,genero,fecha_lectura,valoracion
    "1984","George Orwell","Ficción","2024-01-15","5"
    "Clean Code","Robert Martin","Técnico","2024-02-20","4"
    ```

=== "Via API"

    ```php
    $biblioDevs->importarLote([
        [
            'titulo' => 'El Principito',
            'autor' => 'Antoine de Saint-Exupéry',
            'genero' => 'Infantil',
            'fecha_lectura' => '2024-03-10',
            'valoracion' => 5
        ],
        // ... más libros
    ]);
    ```

### ¿Cómo organizo mis libros por colecciones?

BiblioDevs permite crear colecciones personalizadas:

1. Ve a **"Colecciones"** en el menú principal
2. Haz clic en **"Nueva Colección"**
3. Dale un nombre (ej: "Clásicos de la Literatura")
4. Arrastra libros desde tu biblioteca a la colección
5. ¡Listo! Ahora puedes filtrar por colección

!!! tip "Colecciones inteligentes"
    Crea colecciones automáticas basadas en criterios como género, autor o valoración. Ve a **Colecciones > Crear Inteligente**.

## Problemas técnicos

### La aplicación se ve lenta, ¿qué puedo hacer?

Prueba estas optimizaciones:

1. **Índices de base de datos**: Ejecuta el script `optimize_db.sql`
2. **Caché**: Habilita el caché en `config/app.php`
3. **Imágenes**: Comprime las portadas en **Configuración > Optimización**
4. **Límites de memoria**: Aumenta `memory_limit` en PHP a 512M

### ¿Cómo hago backup de mis datos?

BiblioDevs ofrece múltiples opciones de respaldo:

| Método | Frecuencia | Ubicación | Automático |
|--------|------------|-----------|------------|
| **MySQL dump** | Diario | `/backups/mysql/` | ✅ |
| **Exportación completa** | Semanal | Descarga local | ❌ |
| **Sync en la nube** | Tiempo real | Google Drive/Dropbox | ✅ |
| **Git backup** | Por cambios | Repositorio privado | ✅ |

### Error: "No se puede conectar a la base de datos"

Este error suele indicar problemas de configuración:

1. Verifica las credenciales en `config/database.php`
2. Asegúrate de que MySQL esté ejecutándose
3. Comprueba que el usuario tenga permisos adecuados
4. Revisa el firewall (puerto 3306)

```bash
# Comandos útiles para diagnóstico
mysql -u usuario -p -h localhost
SHOW DATABASES;
GRANT ALL PRIVILEGES ON bibliodevs.* TO 'usuario'@'localhost';
```

### ¿Cómo actualizo BiblioDevs a una nueva versión?

!!! warning "Importante"
    **Siempre haz backup antes de actualizar**. Las actualizaciones pueden incluir cambios en la base de datos.

Proceso de actualización:

1. **Descarga** la nueva versión desde GitHub
2. **Backup** de archivos y base de datos
3. **Detén** el servidor web temporalmente
4. **Reemplaza** los archivos (preserva `config/`)
5. **Ejecuta** las migraciones: `php artisan migrate`
6. **Reinicia** el servidor web

## Funcionalidades específicas

### ¿Puedo compartir mi biblioteca con otros usuarios?

BiblioDevs soporta bibliotecas compartidas:

- **Modo familiar**: Hasta 5 usuarios pueden compartir una biblioteca
- **Modo público**: Tu biblioteca es visible para otros (solo lectura)
- **Recomendaciones**: Comparte listas específicas con amigos

### ¿Hay una app móvil?

Actualmente BiblioDevs es una aplicación web responsiva que funciona perfectamente en móviles. Una app nativa está en desarrollo para 2025.

### ¿Puedo personalizar los géneros?

¡Por supuesto! Ve a **Configuración > Géneros** para:

- Añadir géneros personalizados
- Modificar géneros existentes
- Crear subcategorías
- Asignar colores a cada género

## Soporte y comunidad

### ¿Dónde puedo reportar bugs o sugerir mejoras?

- **GitHub Issues**: [github.com/bibliodevs/app/issues](https://github.com/bibliodevs/app/issues)
- **Discord**: [discord.gg/bibliodevs](https://discord.gg/bibliodevs)
- **Email**: soporte@bibliodevs.com
- **Documentación**: Siempre actualizada en este sitio

### ¿BiblioDevs es gratuito?

Sí, BiblioDevs es completamente **gratuito y open source** bajo licencia MIT. Puedes:

- Usar la aplicación sin limitaciones
- Modificar el código fuente
- Contribuir al proyecto
- Crear tu propia versión personalizada

!!! question "¿No encuentras tu pregunta?"
    Si tu duda no está aquí, consulta nuestra [guía de uso](uso.md) o contacta con la comunidad en Discord. ¡Estaremos encantados de ayudarte!

---

*Última actualización: Junio 2025*

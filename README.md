# CREADO POR: SANTIAGO VALENCIA AGUDELO

# API de Música

Una **API RESTful** desarrollada con [Flask](https://flask.palletsprojects.com/en/stable/), [Flask-RESTX](https://flask-restx.readthedocs.io/en/latest/), [Flask-SQLAlchemy](https://flask-sqlalchemy.readthedocs.io/en/stable/) y [SQLAlchemy](https://www.sqlalchemy.org/) para gestionar usuarios, canciones y relaciones de favoritos.

## Descripción

Esta API permite:
- **Usuarios**: Crear y gestionar perfiles de usuarios.
- **Canciones**: Agregar, actualizar y eliminar canciones con sus metadatos.
- **Favoritos**: Gestionar las canciones favoritas de cada usuario.

Incluye una interfaz de documentación interactiva generada automáticamente con [Swagger](https://swagger.io/) disponible en el endpoint `/docs`.

## Estructura del Proyecto

```
lp3-taller2
├── README.md            # Documentación del proyecto
├── .env                 # Variables de entorno
├── .gitignore           # Archivos y directorios ignorados por Git
├── app.py               # Script principal para ejecutar la aplicación
├── instance
│   └── musica.db        # Base de datos SQLite
├── musica_api
│   ├── __init__.py      # Inicialización del módulo
│   ├── api_models.py    # Modelos de API para serialización/deserialización
│   ├── config.py        # Configuración de entornos
│   ├── extensions.py    # Extensiones de Flask (API, SQLAlchemy, JWT)
│   ├── models.py        # Modelos de datos con SQLAlchemy
│   └── resources.py     # Recursos y endpoints de la API
├── requirements.txt     # Dependencias del proyecto
├── tests
│   └── test_api.py      # Pruebas unitarias
└── utils.py             # Funciones auxiliares
```

## Ejecución

1. Ejecuta la aplicación:
   ```bash
   flask run
   ```

2. Accede a la API:
   - **API**: [http://127.0.0.1:5000/api/](http://127.0.0.1:5000/api/)
   - **Documentación Swagger**: [http://127.0.0.1:5000/docs](http://127.0.0.1:5000/docs)

## Uso de la API

### Usuarios

- **Listar usuarios**: `GET /api/usuarios`
- **Crear usuario**: `POST /api/usuarios`
- **Obtener usuario**: `GET /api/usuarios/{id}`
- **Actualizar usuario**: `PUT /api/usuarios/{id}`
- **Eliminar usuario**: `DELETE /api/usuarios/{id}`

### Canciones

- **Listar canciones**: `GET /api/canciones`
- **Crear canción**: `POST /api/canciones`
- **Obtener canción**: `GET /api/canciones/{id}`
- **Actualizar canción**: `PUT /api/canciones/{id}`
- **Eliminar canción**: `DELETE /api/canciones/{id}`
- **Buscar canciones**: `GET /api/canciones/buscar?titulo=value&artista=value&genero=value`

### Favoritos

- **Listar favoritos**: `GET /api/favoritos`
- **Marcar favorito**: `POST /api/favoritos`
- **Obtener favorito**: `GET /api/favoritos/{id}`
- **Eliminar favorito**: `DELETE /api/favoritos/{id}`
- **Listar favoritos de usuario**: `GET /api/usuarios/{id}/favoritos`
- **Marcar favorito específico**: `POST /api/usuarios/{id_usuario}/favoritos/{id_cancion}`
- **Eliminar favorito específico**: `DELETE /api/usuarios/{id_usuario}/favoritos/{id_cancion}`

## Modelo de Datos

1. **Usuario**:
   - `id`: Identificador único
   - `nombre`: Nombre del usuario
   - `correo`: Correo electrónico (único)
   - `fecha_registro`: Fecha de registro

2. **Canción**:
   - `id`: Identificador único
   - `titulo`: Título de la canción
   - `artista`: Artista o intérprete
   - `album`: Álbum al que pertenece
   - `duracion`: Duración en segundos
   - `año`: Año de lanzamiento
   - `genero`: Género musical
   - `fecha_creacion`: Fecha de creación del registro

3. **Favorito**:
   - `id`: Identificador único
   - `id_usuario`: ID del usuario (clave foránea)
   - `id_cancion`: ID de la canción (clave foránea)
   - `fecha_marcado`: Fecha en que se marcó como favorito
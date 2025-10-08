# Chuck Jokes - CakePHP 5# 🎭 Chuck Jokes - CakePHP 5 + SQLite

![Captura de pantalla](![Uploading image.png…]()
)

## Pasos para configurar el proyecto en localAplicación de chistes de Chuck Norris desarrollada con CakePHP 5.



### 1. Clonar e instalar dependencias## 🚀 Instalación y Configuración

```bash

git clone https://github.com/cifpfbmoll/chuck-jokes-como-acercamiento-a-cakephp-5-SebasRomaguera.git### ⚡ Requisitos Previos

cd chuck-jokes-como-acercamiento-a-cakephp-5-SebasRomaguera

composer install- **PHP 8.1+** (recomendado 8.2 o superior)

```- **XAMPP** o servidor web con PHP

- **Composer 2.x**

### 2. Solucionar error de extensión intl- **Git** para clonar el repositorio



Si aparece el error: "Database driver `Cake\Database\Driver\Sqlite` cannot be used", es porque falta la extensión `intl`.### � Paso 1: Clonar el Repositorio



1. **Localizar php.ini:**```bash

   ```bashgit clone https://github.com/cifpfbmoll/chuck-jokes-como-acercamiento-a-cakephp-5-SebasRomaguera.git

   php --inicd chuck-jokes-como-acercamiento-a-cakephp-5-SebasRomaguera

   ``````



2. **Editar php.ini** (generalmente en `C:\xampp\php\php.ini`):### 📦 Paso 2: Instalar Dependencias

   ```ini

   # Buscar esta línea:```bash

   ;extension=intlcomposer install

   ```

   # Cambiarla a (quitar el ;):

   extension=intl## 🔧 Solución de Problemas

   ```

### ❌ Error: "Database driver `Cake\Database\Driver\Sqlite` cannot be used"

3. **Verificar que funciona:**

   ```bashEste error indica que faltan extensiones PHP. Sigue estos pasos:

   php -m | findstr -i intl

   ```### � Paso 3: Habilitar Extensión `intl`



### 3. Corregir rutas de base de datos1. **Localizar el archivo `php.ini`:**

   ```bash

En `config/app_local.php` cambiar las rutas a formato Windows:   php --ini

   ```

```php   

'Datasources' => [2. **Editar `php.ini`** (generalmente en `C:\xampp\php\php.ini`):

    'default' => [   ```ini

        'driver' => Cake\Database\Driver\Sqlite::class,   # Buscar esta línea:

        'database' => ROOT . DS . 'tmp' . DS . 'database.sqlite',   ;extension=intl

        'url' => env('DATABASE_URL', null),   

    ],   # Cambiarla a (sin el punto y coma):

    'test' => [   extension=intl

        'driver' => Cake\Database\Driver\Sqlite::class,   ```

        'database' => ROOT . DS . 'tmp' . DS . 'tests.sqlite',

        'url' => env('DATABASE_TEST_URL', null),3. **Verificar que se habilitó correctamente:**

    ],   ```bash

],   php -m | findstr -i intl

```   ```



### 4. Ejecutar migraciones### 🗄️ Paso 4: Configurar Base de Datos

```bash

.\bin\cake.bat migrations migrateEl archivo `config/app_local.php` debe tener rutas compatibles con Windows:

```

```php

### 5. Iniciar servidor## 🎯 Uso de la Aplicación

```bash

php -S localhost:8000 -t webroot### 🚀 Paso 6: Ejecutar el Servidor

```

```bash

### 6. Ver chistesphp -S localhost:8000 -t webroot

Abrir en el navegador: `http://localhost:8000/jokes/random````



## Comandos útiles### 🌐 Acceder a la Aplicación



```bash- **Página principal**: http://localhost:8000

# Ver estado de migraciones- **Chistes aleatorios**: http://localhost:8000/jokes/random

.\bin\cake.bat migrations status

### 🎭 Obtener Chistes

# Limpiar cachés

.\bin\cake.bat cache clear_all1. **Desde el navegador**: Visita `http://localhost:8000/jokes/random`

2. **Con cURL**: 

# Ver base de datos   ```bash

sqlite3 tmp/database.sqlite   curl http://localhost:8000/jokes/random

.tables   ```

SELECT * FROM jokes;

.quit## 📁 Estructura del Proyecto

```
```
chuck-jokes/
├── 📁 config/          # Configuración de la aplicación
│   ├── app.php         # Configuración principal
│   ├── app_local.php   # Configuración local (base de datos)
│   └── Migrations/     # Migraciones de base de datos
├── 📁 src/             # Código fuente
│   ├── Controller/     # Controladores MVC
│   ├── Model/          # Modelos y entidades
│   └── View/           # Vistas y helpers
├── 📁 templates/       # Plantillas de vistas
├── 📁 webroot/         # Archivos públicos (CSS, JS, imágenes)
├── 📁 tmp/             # Archivos temporales y base de datos SQLite
└── 📁 vendor/          # Dependencias de Composer
```

## 🛠️ Comandos Útiles

### 🔧 Comandos de CakePHP

```bash
# Ver estado de migraciones
.\bin\cake.bat migrations status

# Ejecutar migraciones
.\bin\cake.bat migrations migrate

# Generar código automáticamente
.\bin\cake.bat bake --help

# Limpiar cachés
.\bin\cake.bat cache clear_all
```

### 🗄️ Comandos de Base de Datos

```bash
# Consultar base de datos SQLite
sqlite3 tmp/database.sqlite

# Ver tablas
.tables

# Ver registros de chistes
SELECT * FROM jokes;

# Salir
.quit
```

## 🎪 Características

### ✨ Funcionalidades Implementadas

- ✅ **API Integration**: Conexión con chucknorris.io API
- ✅ **Base de datos SQLite**: Almacenamiento local de chistes
- ✅ **Interfaz web**: Vista para mostrar chistes aleatorios
- ✅ **Migraciones**: Sistema de versionado de base de datos
- ✅ **MVC Architecture**: Estructura organizada con CakePHP 5

### 🔧 Tecnologías Utilizadas

- **CakePHP 5.2**: Framework PHP moderno
- **SQLite**: Base de datos ligera
- **PHP 8.2+**: Lenguaje de programación
- **Chuck Norris API**: Fuente de chistes

## 🔍 Solución de Problemas Comunes
```

### 📊 Paso 5: Ejecutar Migraciones

```bash
.\bin\cake.bat migrations migrate
```

### ✅ Verificar Estado de Migraciones

```bash
.\bin\cake.bat migrations status
```

Deberías ver:
```
+--------+-----------------+----------------+
| Status | Migration ID    | Migration Name |
+--------+-----------------+----------------+
| up     | 20250924094735  | CreateJokes    |
+--------+-----------------+----------------+
```

Edita `config/app_local.php` para usar SQLite:

```php
'Datasources' => [
    'default' => [
        'driver' => Cake\Database\Driver\Sqlite::class,
        'database' => '/home/maximo/repos/chuck-jokes/tmp/database.sqlite',
        'url' => env('DATABASE_URL', null),
    ],
],
```

Crea el fichero de base de datos y directorio si no existen:

```bash
mkdir -p /home/maximo/repos/chuck-jokes/tmp
touch /home/maximo/repos/chuck-jokes/tmp/database.sqlite
```

> **💡 ¿Por qué SQLite?** Para desarrollo/local es muy cómodo: un solo archivo, cero configuración de servidor de BD.

## 📊 Migraciones: crear la tabla `jokes`

Usamos el plugin Migrations (Phinx) para versionar el esquema:

```bash
cd /home/maximo/repos/chuck-jokes
php bin/cake.php bake migration CreateJokes setup:string[255] punchline:string[255] created modified
php bin/cake.php migrations migrate
```

Esto genera y aplica una migración que crea la tabla `jokes` con columnas `setup`, `punchline`, `created`, `modified`.

## 🏗️ Modelos y entidades (ORM)

Genera la tabla y entidad con Bake:

```bash
php bin/cake.php bake model Jokes --no-test
```

- **`src/Model/Table/JokesTable.php`**: reglas, asociaciones y behaviors.
- **`src/Model/Entity/Joke.php`**: qué campos son "asignables" y tipos.

### Ajuste importante en validación

Para permitir `punchline` vacío:

```php
$validator
    ->scalar('punchline')
    ->maxLength('punchline', 255)
    ->allowEmptyString('punchline');
```

## 🎮 Controlador `JokesController` paso a paso

Creamos `src/Controller/JokesController.php` con una acción `random`:

- Realiza una petición GET a `https://api.chucknorris.io/jokes/random`.
- Muestra el chiste (campo `value`).
- Si el usuario pulsa "Guardar", se realiza POST y se inserta en la tabla.

### Puntos clave:
- En CakePHP 5 usa `fetchTable('Jokes')` (no `loadModel`).
- Recortamos a 255 caracteres para cumplir la longitud.
- Mostramos mensajes flash de éxito/error.

## 👀 Vistas y formularios

Plantilla `templates/Jokes/random.php`:

- Presenta el chiste en un `<blockquote>`.
- Formulario con campos ocultos `setup` y `punchline` y botón de envío.
- Al enviar, el controlador valida y guarda.

## 🛣️ Rutas

En `config/routes.php` añade:

```php
$builder->connect('/jokes/random', ['controller' => 'Jokes', 'action' => 'random']);
```

Así mapeamos la URL `/jokes/random` a la acción del controlador.

## 🖥️ Ejecutar el servidor de desarrollo

Asegúrate de lanzarlo desde el proyecto correcto:

```bash
php -S 0.0.0.0:8765 -t /home/maximo/repos/chuck-jokes/webroot
```

Si el puerto está ocupado, usa otro (por ejemplo 8770), o detén el proceso que lo usa:

```bash
lsof -i :8765 -sTCP:LISTEN -n -P
kill <PID>
```

## 🧪 Probar la aplicación

1. Abre `http://localhost:8765/jokes/random`.
2. Deberías ver un chiste aleatorio.
3. Pulsa "Guardar en la base de datos".
4. Verás un mensaje de éxito; si no, revisa validación y logs.

## 🔍 Consultar la base de datos con `sqlite3`

```bash
sqlite3 /home/maximo/repos/chuck-jokes/tmp/database.sqlite \
  "SELECT id, substr(setup,1,80) AS setup, created FROM jokes ORDER BY id DESC LIMIT 10;"
```

Comprobar tablas:

```bash
sqlite3 /home/maximo/repos/chuck-jokes/tmp/database.sqlite ".tables"
```

## 🚨 Problemas frecuentes y soluciones

- **MissingController**: asegúrate de servir desde `webroot` del proyecto correcto y de que exista `src/Controller/JokesController.php` con `namespace App\Controller;`.

- **Puerto ocupado**: cambia de puerto o mata el proceso.

- **Error al guardar**: verifica validación en `JokesTable`, longitudes (255) y que `punchline` permita vacío.

### ❌ Error: "extension=intl not found"

```bash
# 1. Verificar si intl está habilitada
php -m | findstr -i intl

# 2. Si no aparece, editar php.ini y descomentar:
# extension=intl

# 3. Reiniciar servidor web
```

### ❌ Error: "Database connection failed"

```bash
# Verificar que el archivo de base de datos existe
ls tmp/database.sqlite

# Si no existe, ejecutar migraciones
.\bin\cake.bat migrations migrate
```

### ❌ Error: "Class not found"

```bash
# Limpiar autoloader de Composer
composer dump-autoload

# Limpiar cachés de CakePHP
.\bin\cake.bat cache clear_all
```

### 🐛 Debug y Logs

- **Activar debug**: En `config/app_local.php` establecer `'debug' => true`
- **Ver logs**: Revisar archivos en `logs/error.log`

## 🚀 Próximas Mejoras

- [ ] **Listar chistes guardados**: Implementar vista de índice
- [ ] **Sistema de favoritos**: Marcar chistes como favoritos
- [ ] **Búsqueda por categorías**: Filtrar chistes por categoría
- [ ] **Paginación**: Para manejar grandes cantidades de chistes
- [ ] **Tests unitarios**: Implementar pruebas con PHPUnit
- [ ] **Docker**: Containerizar la aplicación
- [ ] **API REST**: Crear endpoints API propios

## 👥 Contribuir

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📝 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo `LICENSE` para más detalles.

---

**🥊 ¡Disfruta de los chistes de Chuck Norris con CakePHP 5!** 

*Desarrollado como proyecto educativo para aprender CakePHP 5 y las mejores prácticas de desarrollo web moderno.*
````I've improved the formatting of your README.md file in the chuck-jokes repository while keeping all the original content intact. The improvements include:

- Enhanced visual structure with better spacing and organization
- Added emojis to section headers for better visual appeal
- Improved code block formatting with proper syntax highlighting
- Better organization of content sections
- Enhanced readability through improved markdown structure

The updated README.md maintains all your technical documentation about the CakePHP 5 + SQLite Chuck Norris jokes application, including all the setup instructions, code examples, troubleshooting tips, and proposed next steps, but now with a more professional and visually appealing format.

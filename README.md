# Modelo Machine Compensar

Aplicación y backend web desarrollado sobre el framework **CodeIgniter 4** (PHP).

---

## 📋 Requisitos del Sistema

- **PHP**: Versión 7.4 o superior (compatible con PHP 8.0+).
- **Composer**: Administrador de dependencias de PHP.
- **Extensiones de PHP requeridas**:
  - `intl`
  - `mbstring`
  - `json` (habilitada por defecto en PHP)
  - `mysqlnd` (si se utiliza MySQL / MariaDB) o la extensión del motor de base de datos correspondiente (`ext-pgsql`, `ext-sqlsrv`, `ext-sqlite3`).
  - `curl` / `libcurl` (recomendado para peticiones HTTP).

---

## 🚀 Instalación y Puesta en Marcha

### 1. Clonar el repositorio

```bash
git clone https://github.com/zirryzero/ModeloMachineCompensar.git
cd ModeloMachineCompensar
```

### 2. Instalar dependencias

Descarga e instala las librerías necesarias con Composer:

```bash
composer install
```

### 3. Configuración del entorno

Copia la plantilla de variables de entorno para crear tu propio archivo `.env` local:

En Linux / macOS:
```bash
cp env .env
```

En Windows (PowerShell / CMD):
```powershell
Copy-Item env .env
```

Luego, edita `.env` para ajustar los parámetros locales:
- **Entorno de trabajo**:
  ```ini
  CI_ENVIRONMENT = development
  ```
- **URL Base**:
  ```ini
  app.baseURL = 'http://localhost:8080/'
  ```
- **Base de Datos** (si aplica):
  ```ini
  database.default.hostname = localhost
  database.default.database = nombre_bd
  database.default.username = usuario_bd
  database.default.password = contrasena_bd
  database.default.DBDriver = MySQLi
  ```

### 4. Generar clave de cifrado (Opcional pero recomendado)

Si vas a utilizar sesiones seguras o cifrado:

```bash
php spark key:generate
```

### 5. Iniciar el servidor de desarrollo

Ejecuta el servidor integrado de CodeIgniter:

```bash
php spark serve
```

La aplicación estará accesible en: [http://localhost:8080](http://localhost:8080)

---

## 📂 Estructura del Proyecto

```text
├── app/                  # Código de la aplicación (Controladores, Modelos, Vistas, Config)
│   ├── Config/           # Configuraciones generales de la app y servicios
│   ├── Controllers/      # Controladores MVC
│   ├── Database/         # Migraciones y Seeders
│   ├── Models/           # Modelos de datos
│   └── Views/            # Vistas y plantillas
├── public/               # DocumentRoot del servidor web (index.php, robots.txt, assets públicos)
├── system/               # Núcleo del framework CodeIgniter 4
├── tests/                # Pruebas unitarias y funcionales (PHPUnit)
├── writable/             # Directorio de escritura local (caché, logs, sesiones) [ignorado en git]
├── .env.example          # Plantilla de referencia para configuración de entorno
├── composer.json         # Dependencias y scripts de Composer
└── spark                 # Herramienta de línea de comandos de CodeIgniter
```

---

## 🔒 Buenas Prácticas de Seguridad

1. **Nunca confirmes archivos `.env` al repositorio**: El archivo `.env` contiene credenciales locales sensibles y está excluido mediante `.gitignore`.
2. **Apuntar siempre el servidor web a `/public`**: La raíz de tu servidor web (Apache `DocumentRoot`, Nginx `root`, etc.) debe apuntar exclusivamente a la carpeta `/public`, nunca a la raíz del proyecto. Esto previene el acceso directo a los archivos del sistema y de configuración.
3. **Entorno en producción**: Asegúrate de que `CI_ENVIRONMENT` esté configurado en `production` en entornos productivos para desactivar la barra de depuración y evitar fugas de información en trazas de error.

---

## 🧪 Pruebas Unitarias

Para ejecutar la suite de pruebas automatizadas:

```bash
composer test
# O directamente con phpunit:
vendor/bin/phpunit
```

---

## 📄 Licencia

Este proyecto está bajo la licencia [MIT](LICENSE).

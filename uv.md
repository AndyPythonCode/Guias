# Ejemplos de Comandos uv

Aquí tienes ejemplos prácticos para varios comandos de la herramienta `uv`.

## `uv run`

* **Descripción**: Ejecutar un comando o script dentro del entorno del proyecto.
* **Ejemplo:** `uv run python manage.py runserver`
* **Explicación:** Ejecuta el comando `python manage.py runserver` utilizando el intérprete de Python y las dependencias gestionadas por `uv` para el proyecto actual (común en proyectos Django).

## `uv init`

* **Descripción**: Crear un nuevo proyecto gestionado por `uv`.
* **Ejemplo:** `uv init`
* **Explicación:** Crea un archivo `pyproject.toml` básico en el directorio actual, configurándolo para ser gestionado por `uv`. Si ya existe, puede que te pregunte antes de sobrescribir o modificar.

## `uv add`

* **Descripción**: Añadir dependencias al proyecto.
* **Ejemplo:** `uv add requests`
* **Explicación:** Añade la librería `requests` como dependencia en tu archivo `pyproject.toml`, la instala en el entorno virtual (si está activo o lo crea) y actualiza el archivo `uv.lock`.

## `uv remove`

* **Descripción**: Eliminar dependencias del proyecto.
* **Ejemplo:** `uv remove requests`
* **Explicación:** Elimina la librería `requests` de tu archivo `pyproject.toml`, la desinstala del entorno virtual y actualiza el archivo `uv.lock`.

## `uv sync`

* **Descripción**: Sincronizar (instalar/desinstalar) paquetes en el entorno para que coincidan con el archivo de bloqueo (`uv.lock`).
* **Ejemplo:** `uv sync`
* **Explicación:** Lee el archivo `uv.lock` (o `pyproject.toml` si no existe el lockfile) y asegura que el entorno virtual actual tenga exactamente esas dependencias instaladas, ni más ni menos.

## `uv lock`

* **Descripción**: Generar o actualizar el archivo de bloqueo (`uv.lock`).
* **Ejemplo:** `uv lock`
* **Explicación:** Resuelve todas las dependencias especificadas en `pyproject.toml` y escribe las versiones exactas y sus subdependencias en el archivo `uv.lock`. Esto asegura instalaciones reproducibles.

## `uv export`

* **Descripción**: Exportar el archivo de bloqueo a otro formato.
* **Ejemplo:** `uv export --output-file requirements.txt`
* **Ejemplo:** `uv export --no-hashes --output-file requirements.txt`
* **Explicación:** Genera un archivo `requirements.txt` (formato estándar de pip) a partir del contenido del archivo `uv.lock`.

## `uv tree`

* **Descripción**: Mostrar el árbol de dependencias del proyecto.
* **Ejemplo:** `uv tree`
* **Explicación:** Muestra una vista jerárquica de las dependencias instaladas en el entorno, mostrando qué paquete depende de cuál.

## `uv tool`

* **Descripción**: Ejecutar o instalar comandos proporcionados por paquetes Python.
* **Ejemplo:** `uv tool run black --check .`
* **Explicación:** Ejecuta la herramienta `black` (un formateador de código) para verificar el formato de los archivos en el directorio actual. `uv` se encarga de descargar `black` si es necesario en un entorno aislado para herramientas. También puedes usar `uv tool install <tool>` para tenerla disponible de forma persistente dentro del gestor de herramientas de `uv`.

## `uv python`

* **Descripción**: Gestionar versiones e instalaciones de Python.
* **Ejemplo:** `uv python find`
* **Explicación:** Busca e informa sobre las instalaciones de Python disponibles en tu sistema que `uv` puede detectar y potencialmente usar para crear entornos.

## `uv pip`

* **Descripción**: Interfaz compatible con `pip` para gestionar paquetes.
* **Ejemplo:** `uv pip install "flask>=2.0"`
* **Explicación:** Instala la librería `flask` (versión 2.0 o superior) directamente en el entorno virtual activo gestionado por `uv`. Funciona de manera muy similar al comando `pip install`. Es útil para instalaciones rápidas o experimentales, aunque para dependencias de proyecto es preferible usar `uv add`.

## `uv venv`

* **Descripción**: Crear un entorno virtual.
* **Ejemplo:** `uv venv .venv -p 3.11`
* **Explicación:** Crea un nuevo entorno virtual llamado `.venv` en el directorio actual, utilizando específicamente el intérprete de Python 3.11 (si está disponible). Si omites `-p`, usará una versión de Python por defecto o la especificada en `pyproject.toml`.

## `uv build`

* **Descripción**: Construir distribuciones de paquetes Python (wheels y sdist).
* **Ejemplo:** `uv build`
* **Explicación:** Construye los paquetes de distribución (archivos `.whl` y `.tar.gz`) para el proyecto definido en `pyproject.toml` y los coloca en el directorio `dist/`.

## `uv publish`

* **Descripción**: Subir distribuciones a un índice de paquetes (como PyPI).
* **Ejemplo:** `uv publish`
* **Explicación:** Sube los archivos de distribución encontrados en el directorio `dist/` al índice de paquetes configurado (por defecto PyPI). Necesitarás tener las credenciales configuradas.

## `uv cache`

* **Descripción**: Gestionar la caché de `uv`.
* **Ejemplo:** `uv cache clean`
* **Explicación:** Elimina los archivos almacenados en la caché de `uv`, lo cual puede incluir paquetes descargados o metadatos. Útil para liberar espacio o solucionar problemas relacionados con la caché.

## `uv self`

* **Descripción**: Gestionar la propia instalación de `uv`.
* **Ejemplo:** `uv self update`
* **Explicación:** Busca la última versión disponible de `uv` y, si hay una nueva, la descarga y actualiza la instalación actual.

## `uv version`

* **Descripción**: Mostrar la versión de `uv`.
* **Ejemplo:** `uv version`
* **Explicación:** Imprime la versión actualmente instalada del ejecutable `uv`.

## `uv help`

* **Descripción**: Mostrar documentación para un comando específico.
* **Ejemplo:** `uv help sync`
* **Explicación:** Muestra información detallada sobre el comando `sync`, incluyendo sus opciones y argumentos disponibles.

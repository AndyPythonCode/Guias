* ## poetry add <paquete>: Añade una dependencia.
    - poetry add requests (dependencias)
    - poetry add pytest --dev (dependencias de desarrollo)

* ## poetry remove <paquete>: Quita una dependencia.
    - poetry remove requests 
    - poetry remove pytest --dev 

* ## poetry show: Lista las dependencias.
    - poetry show
    - poetry show --no-dev
    - poetry show --tree (Muestra las dependencias instaladas en el proyecto en arbol)

* ## poetry update: Actualiza las dependencias.
    - poetry update (Actualiza las dependencias a las versiones más recientes compatibles con las restricciones en pyproject.toml)
    - poetry update requests (Actualizar una dependencia específica)
    - poetry update --no-dev

* ## poetry install: Instala todo.
    - poetry install (Instala todas las dependencias listadas en pyproject.toml y configura el entorno virtual)
    - poetry install --no-root (Sin instalar el proyecto como paquete)
    - poetry install --remove-untracked (Reinstalar todo desde cero)

* ## poetry env: entorno virtual 
    - poetry env info (Confirma que el entorno virtual se creó)

* ## poetry self add poetry-plugin-export: plugin para exportar
    - poetry export -o requirements.txt (Esto genera un requirements.txt basado en poetry.lock)
    - poetry export -o requirements.txt --with dev (incluir dependencias)
    - poetry export -o requirements.txt --without-hashes

```bash
# Si tu intención es que el proyecto NO sea un paquete instalable (por ejemplo, para desarrollar una librería o aplicación)
[tool.poetry]
package-mode = false
```


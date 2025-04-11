__En ciertas ocasiones ocurre un problema con bun y android studios a la hora de hacer un (live reload)__

## Configuración del Host en Vite

Si necesitas especificar un host diferente, puedes configurarlo en el archivo vite.config.js. Por ejemplo, para escuchar en 0.0.0.0, puedes agregar lo siguiente:

```javascript
import { defineConfig } from 'vite'
import { svelte } from '@sveltejs/vite-plugin-svelte'

export default defineConfig({
  plugins: [svelte()],
  server: {
    host: true, // Esto permite que el servidor escuche en 0.0.0.0
    port: 5173,
  },
})
```

Sin embargo, si deseas usar Bun para ejecutar tu proyecto, asegúrate de que Bun esté instalado y configurado correctamente para trabajar con Vite.

## Uso de Bun con Vite

Para usar Bun con Vite, puedes intentar ejecutar el siguiente comando, aunque no es común especificar --host directamente con Bun:


```bash
bun run --bun vite
```

Ve a android studio y ejecuta tu emulador en tu dispositivo fisico.

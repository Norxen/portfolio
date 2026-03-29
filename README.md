# GitHub Pages Repo

Esta carpeta está pensada para usarse como repositorio de publicación en GitHub Pages.

La idea es simple: aquí no se desarrolla la aplicación. Aquí solo se copia el resultado final del build de producción para publicarlo.

## Uso recomendado

Si tu portfolio Angular vive en `frontend`, el flujo normal sería:

1. Construir la aplicación en modo producción.
2. Copiar el contenido generado por el build a esta carpeta.
3. Inicializar aquí un repositorio Git independiente o usar esta carpeta dentro de un repo ya preparado para GitHub Pages.
4. Subir su contenido a GitHub y activar Pages.

## Qué app publicar

Según la estructura actual de `frontend`, la candidata más lógica para actuar como portfolio publicado sería `apps/web-shell`, salvo que decidas crear una app específica para el portfolio.

## Comandos orientativos

Si estás trabajando con Nx, el build suele tener esta forma:

```powershell
cd frontend
npx nx build web-shell --configuration=production
```

Después tendrás que localizar la carpeta de salida del build y copiar su contenido aquí. En proyectos Angular o Nx suele quedar dentro de `dist/`, aunque la ruta exacta depende de la configuración del proyecto.

## Importante sobre rutas

Si el sitio se publica en un repositorio de proyecto, la URL final tendrá una subruta, por ejemplo:

`https://tu-usuario.github.io/tu-repo/`

En ese caso tendrás que revisar el `base href` del build para que los assets y la navegación funcionen correctamente.

## Importante sobre SPA en GitHub Pages

Si usas rutas como `/projects/:id`, GitHub Pages puede fallar al recargar una URL interna porque sirve archivos estáticos.

Tienes dos opciones razonables:

1. Usar `HashLocationStrategy` para que las rutas sean del tipo `/#/projects/mi-proyecto`.
2. Mantener rutas limpias y montar una estrategia de fallback con `404.html`.

Para un despliegue sencillo en GitHub Pages, la opción más robusta suele ser hash routing.

## Estructura esperada de esta carpeta

Cuando vayas a publicar, aquí deberían quedar archivos como:

- `index.html`
- `assets/`
- `styles.*`
- `main.*`
- `404.html` si decides usar fallback para SPA
- `.nojekyll`

## Activación de GitHub Pages

Una vez subido el contenido a GitHub:

1. Entra en el repositorio.
2. Ve a `Settings`.
3. Abre `Pages`.
4. Selecciona la rama desde la que quieres publicar.
5. Guarda la configuración y espera a que GitHub genere la URL pública.

## Recomendación práctica

No trabajes aquí directamente sobre el código fuente del portfolio. Usa esta carpeta solo como destino de publicación, para mantener separado el desarrollo del despliegue.

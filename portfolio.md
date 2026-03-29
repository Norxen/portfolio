# Portfolio profesional en Angular

## Visión del proyecto

Este ejercicio plantea el desarrollo de un portfolio personal con Angular desde una perspectiva profesional. No se trata únicamente de publicar una web atractiva, sino de construir una aplicación que refleje criterio técnico, orden arquitectónico y una forma de trabajar madura. El resultado debe transmitir no solo qué proyectos has hecho, sino también cómo piensas, cómo organizas una interfaz y cómo conviertes una idea en un producto frontend sólido.

La intención es que el portfolio funcione como una carta de presentación real. Quien entre en la aplicación debería entender con rapidez quién eres, a qué te dedicas, qué tipo de proyectos desarrollas y por qué merece la pena dedicar tiempo a explorar tu trabajo. A partir de ahí, la navegación debe acompañar al usuario con naturalidad hacia tus proyectos, tu perfil técnico y, por último, una vía de contacto clara.

## Objetivo principal

El objetivo es desarrollar una aplicación moderna, mantenible y escalable que sirva como portfolio profesional y, al mismo tiempo, como demostración de dominio de Angular actual. La aplicación debe estar bien estructurada, apoyarse en componentes reutilizables y ofrecer una experiencia fluida tanto en escritorio como en móvil.

Más que acumular funcionalidades, lo importante es resolver bien lo esencial. Por eso, el proyecto debe abordarse con una lógica de producto real: primero se define un alcance razonable, después se construye una base técnica fiable y, solo cuando esa base está firme, se añaden mejoras o extras.

## Principios del proyecto

Para que el portfolio tenga coherencia, conviene trabajar con unos pocos principios claros desde el inicio. El primero es la claridad: tanto la interfaz como la arquitectura deben ayudar a entender el proyecto con rapidez. El segundo es la mantenibilidad: cada decisión técnica debería facilitar la evolución del código en lugar de complicarla. El tercero es la reutilización: si un patrón visual o de comportamiento aparece varias veces, debe convertirse en una pieza reusable y no repetirse de forma improvisada. El cuarto es la intención: cada componente, cada animación y cada decisión visual deberían responder a una necesidad concreta, no a la voluntad de añadir complejidad por aparentar más nivel.

Estos principios son importantes porque permiten tomar decisiones con criterio cuando aparecen dudas. Si en algún momento una solución parece vistosa pero dificulta la legibilidad, o una mejora técnica añade complejidad sin aportar valor real, lo más razonable será descartarla.

## Orden de preparación del proyecto

Este documento está organizado siguiendo el orden más lógico de trabajo. Primero se define el contenido y el alcance real del portfolio. Después se prepara la arquitectura y la librería de diseño. A continuación se construyen las pantallas principales y su lógica. Solo cuando el núcleo está resuelto tiene sentido entrar en pruebas, internacionalización, optimización, despliegue y extras.

Dicho de otro modo, el orden correcto no es empezar por embellecer la home ni dejar cuestiones importantes para el final. Lo adecuado es preparar primero aquello que condiciona todo lo demás y dejar para el cierre únicamente lo que de verdad depende de tener la aplicación ya montada.

## Fase 1. Definición y preparación del contenido

Antes de empezar a implementar, merece la pena dejar resuelto un mínimo de contenido real. En un portfolio, el contenido no se añade al final como relleno, sino que condiciona la estructura, las decisiones de interfaz y el tipo de componentes que tendrá sentido construir. Por eso, es recomendable preparar con antelación una presentación breve para la home, una descripción más desarrollada para la sección “Sobre mí”, una lista de tecnologías o fortalezas que quieras destacar y, sobre todo, la información base de cada proyecto.

Cada proyecto debería contar, al menos, con un título, una descripción corta, una explicación más completa, un listado de tecnologías, un identificador para la ruta dinámica y, si existen, enlaces a repositorio, demo o imágenes. Cuanto más cerrado esté ese material al principio, menos improvisado será el resultado final.

### Alcance del MVP

La primera versión funcional debe cubrir cinco áreas principales. La página de inicio tendrá que actuar como una presentación breve pero eficaz: debe introducir tu perfil, explicar de forma sintética qué haces y ofrecer una llamada a la acción clara para visitar tus proyectos o contactar contigo. Es una sección especialmente importante, porque marca el tono del resto de la experiencia y debe dar sensación de cuidado visual sin caer en artificios innecesarios.

La sección de proyectos será el núcleo del portfolio. Ahí es donde realmente se pone en valor el trabajo realizado, así que debe estar planteada con más intención que una simple cuadrícula de tarjetas. Lo razonable es mostrar un listado dinámico, permitir filtrar por tecnologías y ofrecer un buscador que facilite localizar proyectos concretos. Cada tarjeta debería resumir bien el proyecto y servir de puerta de entrada a una vista más detallada.

Cada proyecto contará con su propia página de detalle, accesible mediante una ruta dinámica como `/projects/:id`. En esa vista no basta con repetir el resumen de la tarjeta: debe explicarse el contexto del proyecto, el problema que resuelve, las tecnologías utilizadas y, cuando tenga sentido, incluir imágenes, capturas o enlaces a GitHub y a una demo.

La sección “Sobre mí” debe aportar contexto profesional. No hace falta convertirla en una autobiografía, pero sí conviene que explique tu recorrido, tus fortalezas y tu forma de trabajar. Puede apoyarse en una línea temporal, una presentación de skills o una combinación de ambas, siempre que el resultado sea claro y no parezca una acumulación de bloques desconectados.

Por último, la sección de contacto debe cerrar el recorrido de forma limpia. El formulario tiene que ser sencillo, comprensible y estar bien validado, con mensajes de error y de éxito que ayuden al usuario en lugar de entorpecerlo.

## Fase 2. Arquitectura base

La estructura del proyecto debería distinguir con claridad entre la lógica transversal, las piezas reutilizables y las funcionalidades de negocio. Una base razonable sería la siguiente:

```text
src/app/
  core/
  shared/
  features/
    home/
    projects/
    project-detail/
    about/
    contact/

libs/
  ui/
```

Dentro de `core` deberían vivir los servicios globales, la configuración y aquellas utilidades que afectan a toda la aplicación. `shared` puede reservarse para piezas reutilizables que no pertenezcan a una funcionalidad concreta, como directivas, pipes o pequeños componentes de apoyo. La carpeta `features`, en cambio, debe organizar las pantallas principales y la lógica específica de cada sección. La carpeta `libs/ui` tendrá un papel especial, porque servirá para aislar el sistema visual y los componentes de interfaz reutilizables.

En esta fase también conviene dejar definidas las rutas principales de la aplicación. Aunque las pantallas todavía no estén terminadas, es buena idea dejar preparadas las rutas base de la home, proyectos, detalle, sobre mí, contacto y 404. Eso evita improvisar la navegación cuando el proyecto ya ha empezado a crecer.

## Fase 3. Sistema visual y librería de diseño

La librería de diseño debe implementarse principalmente con Atomic Design, Angular y SCSS. Esa combinación permite que la construcción visual tenga una lógica clara: Angular se encarga de la composición y de la API de los componentes, SCSS da soporte al sistema de estilos, temas y tokens, y Atomic Design aporta una forma coherente de organizar las piezas sin mezclar niveles de complejidad.

No se trata de aplicar Atomic Design de forma rígida o académica, sino de utilizarlo con sentido. Lo importante es que los componentes más pequeños se definan como base reutilizable, que las combinaciones intermedias formen patrones reconocibles y que los bloques más complejos se compongan a partir de esas piezas.

Una organización razonable para `libs/ui` podría ser esta:

```text
libs/ui/
  atoms/
    button/
    input/
    badge/
  molecules/
    form-field/
    project-card/
    theme-toggle/
  organisms/
    header/
    project-grid/
    contact-form/
  styles/
    _variables.scss
    _mixins.scss
    _themes.scss
  tokens/
    colors.ts
    spacing.ts
    typography.ts
```

En esta fase el trabajo debería empezar por los tokens y la base SCSS: colores, tipografías, espaciados, mixins, temas y comportamiento responsive. Después tiene sentido construir los átomos fundamentales, como botón, input o badge. A partir de ahí se pueden crear moléculas y organismos que luego usarán las páginas principales.

Además, la librería debería contar al menos con un sistema de tema claro y oscuro. Ese cambio de tema puede controlarse mediante signals desde Angular, mientras que SCSS se encarga de centralizar variables, mixins y reglas visuales.

## Fase 4. Implementación técnica del núcleo

La aplicación debe construirse con Angular moderno y aprovechar las herramientas que hoy forman parte de su enfoque principal. Eso implica trabajar con componentes standalone, apoyarse en signals para el estado de interfaz, utilizar el nuevo control flow con `@if` y `@for` cuando proceda y estructurar la navegación con Angular Router, incluyendo lazy loading en las secciones principales. RxJS puede aparecer, pero solo cuando aporte algo real.

El objetivo en esta fase no es cerrar todavía todos los detalles visuales, sino construir una base funcional limpia. La home debe dejar claro quién eres y qué puede hacer el usuario a continuación. La sección de proyectos debe mostrar el listado y permitir navegar a cada detalle. El detalle de proyecto debe cargar correctamente mediante una ruta dinámica. “Sobre mí” debe presentar tu perfil con claridad. Y la parte de contacto debe quedar montada con Reactive Forms y sus validaciones principales.

### Uso de Angular en cada sección

La página de inicio es un buen lugar para aplicar signals como base del estado visual y añadir animaciones de entrada que refuercen la presentación sin distraer. También puede aprovechar `@if` para mostrar o no ciertos bloques según el estado de la interfaz. La sección de proyectos, por su parte, encaja bien con `@for`, el uso de `track` y señales derivadas para filtros y búsqueda.

En el detalle de proyecto será necesario trabajar con rutas dinámicas y con `ActivatedRoute`, además de aprovechar lazy loading para que cada sección cargue cuando realmente se necesita. En “Sobre mí” tendrá sentido apoyarse en componentes reutilizables y, si la composición lo requiere, usar `@Input()` y `@Output()` con moderación y criterio. La parte de contacto debe construirse con Reactive Forms, validaciones personalizadas cuando sean necesarias y una respuesta visual clara ante errores o envíos correctos.

## Fase 5. Experiencia de usuario y comportamiento

Cuando la estructura principal ya existe, toca trabajar la experiencia. La navegación debe ser sencilla, predecible y estar organizada por secciones cargadas de forma diferida. Además de las rutas principales, conviene incluir una página 404 personalizada para cerrar correctamente la experiencia y evitar que la aplicación parezca inacabada.

En esta fase también deben entrar las animaciones, los estados de interacción y la revisión responsive. Las animaciones deben acompañar, no distraer. El diseño tiene que mantenerse claro tanto en escritorio como en móvil, y la navegación debe seguir siendo comprensible en cualquier tamaño de pantalla.

## Fase 6. Internacionalización

Si el portfolio quiere proyectar una imagen más completa y profesional, tiene sentido contemplar la internacionalización como una capacidad real del producto y no como un añadido superficial. En este caso, el objetivo no debería limitarse a traducir unos cuantos textos, sino a permitir que la aplicación se presente en el idioma más adecuado para quien la visita.

Ahora bien, conviene plantearlo con precisión técnica. En un despliegue estático como GitHub Pages no suele existir una detección fiable del país de origen a nivel de servidor. Por eso, lo razonable es que la carga inicial del idioma dependa principalmente de la configuración regional del navegador o del idioma preferido por la persona usuaria. Si en el futuro el proyecto se desplegara sobre una infraestructura con soporte de cabeceras, edge middleware o geolocalización, entonces sí podría ampliarse la lógica para responder por país o mercado.

Para este ejercicio, la solución más sólida consiste en definir al menos dos idiomas, establecer uno por defecto y resolver la selección inicial a partir del locale del navegador. A partir de ahí, el portfolio debería permitir cambiar manualmente de idioma y recordar esa preferencia para visitas posteriores.

## Fase 7. Rendimiento, mantenibilidad y testing

En cuanto al rendimiento, es importante que desde el inicio se adopten medidas básicas de eficiencia, pero la revisión consciente suele llegar cuando la aplicación ya está montada. El uso de `ChangeDetectionStrategy.OnPush`, la optimización de listas con `trackBy` o `track` y la reducción de renders innecesarios deberían formar parte de la implementación habitual y no aparecer solo al final como parche.

La mantenibilidad dependerá de que los componentes sean pequeños, tengan responsabilidades claras y eviten duplicar lógica o estilos. En este punto también conviene revisar nombres, orden de carpetas y consistencia en los estilos.

El testing puede mantenerse en un nivel básico, pero debe existir. Basta con cubrir al menos un componente y un servicio, siempre que esas pruebas validen comportamiento relevante y no se queden en simples comprobaciones superficiales.

## Fase 8. Publicación en GitHub Pages

Como se trata de un portfolio, la publicación no debería considerarse un detalle secundario, sino parte del propio ejercicio. Una aplicación de este tipo solo queda verdaderamente cerrada cuando puede consultarse en una URL pública y funciona de forma razonable fuera del entorno local.

Antes de publicar, la aplicación debe estar preparada para producción. Eso implica generar una build estable, revisar que los assets cargan bien y confirmar que la configuración del proyecto es compatible con el entorno de despliegue. Si el portfolio se publica en un repositorio de proyecto y no en un repositorio de usuario, será necesario revisar el `base href` para que los recursos estáticos y las rutas funcionen correctamente desde la subruta correspondiente.

También conviene comprobar cómo se comporta la aplicación al recargar una ruta interna, especialmente en páginas como el detalle de proyecto. La publicación en GitHub Pages debería incluir una revisión final en entorno real: comprobar que la URL pública carga correctamente, que los enlaces funcionan, que el detalle dinámico no rompe la navegación y que la experiencia general sigue siendo sólida una vez desplegada.

## Errores comunes que conviene evitar

Uno de los errores más frecuentes en este tipo de ejercicios es empezar por el diseño de la home sin haber definido antes ni el contenido ni la arquitectura. Eso suele generar una interfaz vistosa al principio, pero difícil de sostener cuando el resto del proyecto empieza a crecer. También es habitual construir demasiados componentes demasiado pronto, sin saber todavía si realmente van a reutilizarse.

Otro error común es sobreactuar la parte técnica. Añadir complejidad solo para demostrar conocimiento suele producir el efecto contrario: en lugar de transmitir dominio, transmite falta de criterio. Esto puede ocurrir al introducir RxJS donde no hace falta o al usar patrones demasiado sofisticados para un portfolio pequeño.

En la parte visual, conviene evitar tanto la rigidez como el exceso. Un portfolio demasiado plano da sensación de poca intención, pero uno cargado de efectos, animaciones o bloques innecesarios pierde claridad y resulta menos profesional.

## Criterios de evaluación

Si este documento se utiliza como guía de trabajo o incluso como referencia de entrega, conviene dejar claro cómo debería evaluarse el resultado. El proyecto tendrá valor si demuestra una arquitectura comprensible, una interfaz consistente, un uso sensato de Angular moderno y una experiencia de usuario bien resuelta. No se trata de medir solo cuántas funcionalidades incluye, sino cómo están planteadas.

También debería valorarse la calidad de las decisiones. Un portfolio técnicamente sobrio pero bien organizado tiene más fuerza que uno lleno de extras mal integrados. Del mismo modo, una pequeña librería UI coherente y útil aporta más que una estructura enorme de Atomic Design si luego no está bien aplicada.

## Checklist de objetivos y criterios de aceptación

La siguiente checklist traduce el ejercicio a objetivos verificables. No todos tienen el mismo peso, pero en conjunto sirven para comprobar si el portfolio responde de verdad a lo que se pide y si el resultado final puede considerarse profesional.

### 1. Definición y contenido

- [ ] Existe una propuesta de valor clara.
- [ ] Existe un contenido real para la home.
- [ ] Existe contenido real para la sección “Sobre mí”.
- [ ] Existe una lista de proyectos definida antes de diseñar la UI final.
- [ ] Cada proyecto tiene `id`, título, resumen, descripción extensa, tecnologías y enlaces relevantes.
- [ ] El contenido mantiene un tono coherente en toda la aplicación.

### 2. Alcance funcional del MVP

- [ ] Existe una home funcional.
- [ ] Existe una sección de proyectos funcional.
- [ ] Existe un detalle de proyecto mediante ruta dinámica.
- [ ] Existe una sección “Sobre mí”.
- [ ] Existe una sección de contacto con formulario funcional.

### 3. Arquitectura

- [ ] El proyecto está separado en `core`, `shared`, `features` y `libs/ui`.
- [ ] Cada capa tiene una responsabilidad clara.
- [ ] La estructura de carpetas es consistente.
- [ ] Las rutas principales están definidas desde una fase temprana.
- [ ] `libs/ui` está desacoplada de la lógica de negocio.

### 4. Angular moderno

- [ ] La aplicación usa standalone components.
- [ ] Se utilizan `signals` cuando tiene sentido.
- [ ] Se usan `@if` y `@for` donde corresponde.
- [ ] Las listas están optimizadas con `track` o equivalente.
- [ ] Angular Router está bien configurado.
- [ ] Existe lazy loading en las secciones principales.
- [ ] `ActivatedRoute` se utiliza correctamente en el detalle de proyecto.
- [ ] RxJS solo aparece cuando está justificado.

### 5. Librería de diseño

- [ ] La librería está construida con Angular y SCSS.
- [ ] La organización responde a Atomic Design.
- [ ] Existen átomos, moléculas y organismos cuando aportan valor.
- [ ] La librería tiene una API clara de componentes.
- [ ] Los componentes son reutilizables.
- [ ] Existe un sistema de tema claro y oscuro.
- [ ] Los tokens y estilos base están definidos antes de cerrar las pantallas.

### 6. Experiencia y diseño

- [ ] La home comunica con claridad quién eres y qué haces.
- [ ] La sección de proyectos permite explorar el trabajo con facilidad.
- [ ] Existen filtros y buscador funcionales.
- [ ] El detalle de proyecto amplía realmente la información.
- [ ] La sección “Sobre mí” aporta contexto profesional.
- [ ] El formulario de contacto está bien validado.
- [ ] El diseño es responsive.
- [ ] Las animaciones aportan valor sin recargar.
- [ ] Existe una página 404 coherente con el resto de la aplicación.

### 7. Internacionalización

- [ ] Existe un idioma por defecto.
- [ ] La selección inicial del idioma usa el locale del navegador o una lógica equivalente realista.
- [ ] La aplicación permite cambiar manualmente de idioma.
- [ ] La preferencia de idioma puede persistirse.
- [ ] Los textos principales están internacionalizados.
- [ ] El diseño soporta variaciones de longitud entre idiomas.

### 8. Rendimiento y calidad técnica

- [ ] Se utiliza `OnPush` donde tiene sentido.
- [ ] Se evitan renders innecesarios.
- [ ] No hay duplicación evidente de lógica.
- [ ] Los componentes tienen responsabilidades claras.
- [ ] El código mantiene una estructura legible y mantenible.

### 9. Testing

- [ ] Existe al menos una prueba de componente.
- [ ] Existe al menos una prueba de servicio.
- [ ] Las pruebas cubren comportamiento relevante.

### 10. Publicación

- [ ] Existe una build de producción funcional.
- [ ] El proyecto puede desplegarse en GitHub Pages.
- [ ] El `base href` se ha revisado si hay subruta.
- [ ] La navegación funciona en la URL publicada.
- [ ] Los assets cargan correctamente en producción.
- [ ] El portfolio puede compartirse públicamente sin errores evidentes.

## Criterio de éxito

El ejercicio estará realmente bien planteado si el resultado final transmite dos ideas con claridad. La primera, que dominas Angular moderno y sabes utilizar sus herramientas con criterio. La segunda, que eres capaz de estructurar una aplicación frontend como un producto real, con una base técnica coherente, una interfaz consistente y una experiencia de usuario cuidada.

En definitiva, el portfolio no debería limitarse a enseñar proyectos. Debería dejar ver cómo entiendes el desarrollo frontend y qué nivel de madurez aplicas al construir software.

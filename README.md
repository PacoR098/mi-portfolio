# Portfolio / CV de Francisco Romero

CV interactivo de una sola página, diseñado en Figma y maquetado con Astro, HTML y CSS. Contiene una navbar de navegación y cinco secciones: Home, About me, Experience, Projects y Contact.

## Secciones

| Sección | Qué contiene |
|---|---|
| **Home** | Presentación con nombre, cargo, dos botones de acceso rápido, foto e indicador "Scroll down" animado |
| **About me** | Texto de presentación y tarjeta de skills con iconos que crecen y brillan al pasar el ratón |
| **Experience** | Tarjeta con la formación en empresa (Soltel Group) y sus puntos clave |
| **Projects** | Tres tarjetas de proyectos destacados, con botones de Live Demo y Code |
| **Contact** | Tres cubos con enlaces a GitHub, LinkedIn y correo electrónico |

## Funcionalidades

- Navbar fija en la parte superior, con enlaces que llevan a cada sección mediante `id`.
- El enlace de la sección en la que estás queda marcado automáticamente (se usa `IntersectionObserver` de JavaScript, que detecta qué sección está en el centro de la pantalla).
- Desplazamiento suave entre secciones (`scroll-behavior: smooth`).
- Efectos `:hover` con transiciones suaves en la navbar, los iconos de skills, las tarjetas de Experience y Projects, los botones y los cubos de Contact.
- Contenido repetido (skills, experiencia, proyectos y contacto) generado desde un único archivo de datos.
- Diseño adaptable: en pantallas estrechas las columnas pasan a una sola.

## Tecnologías

- [Astro](https://astro.build/)
- HTML y CSS (variables CSS, Flexbox y Grid)
- JavaScript (solo para el enlace activo de la navbar)
- Figma (diseño original)
- Fuente DM Sans (Google Fonts)
- Git y GitHub

## Estructura del proyecto

```
mi-portfolio/
├── public/
│   └── images/
│       ├── skills/        # Iconos de las tecnologías
│       ├── projects/      # Iconos de los proyectos
│       ├── contact/       # Cubos de la sección Contact
│       ├── Home.png       # Foto de la sección Home
│       ├── logo.png
│       └── raton.gif      # Animación de "Scroll down"
├── src/
│   ├── components/
│   │   ├── Navbar.astro
│   │   ├── Home.astro
│   │   ├── About.astro
│   │   ├── Experience.astro
│   │   ├── Projects.astro
│   │   └── Contact.astro
│   ├── data/
│   │   └── cv.json        # Textos y enlaces del CV
│   ├── layout/
│   │   └── Layout.astro   # Estructura HTML común y estilos globales
│   └── pages/
│       └── index.astro    # Página única que monta todos los componentes
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

## Cómo ejecutarlo

Requisito: tener [Node.js](https://nodejs.org/) instalado.

```bash
# 1. Instalar las dependencias (solo la primera vez)
npm install

# 2. Arrancar el servidor de desarrollo
npm run dev
```

Después abre `http://localhost:4321` en el navegador. La página se actualiza sola cada vez que guardas un archivo.

Otros comandos:

```bash
npm run build     # Genera la versión final en la carpeta dist/
npm run preview   # Sirve en local la versión generada por build
```

## Decisiones de diseño y desarrollo

- **Una sola página con componentes.** `index.astro` solo monta las piezas, y cada sección vive en su propio componente. Así, si algo falla en el CSS, se localiza enseguida.
- **Datos separados del diseño.** Los textos y enlaces repetidos están en `src/data/cv.json`. Cada componente lo lee y pinta lo que le corresponde con un bucle (`map`), de modo que cambiar un dato no obliga a tocar el HTML.
- **Estilos globales en el Layout.** Las variables de color (paleta tomada de Figma), la fuente, el reset y la altura de las secciones están en `Layout.astro` con `<style is:global>`. Los estilos de cada componente están en su propio `<style>`, que solo le afecta a él.
- **Paleta con nombres descriptivos.** Los colores se guardan como variables CSS (`--azul-noche`, `--azul-claro`, `--rojo`...) y los usos (`--color-fondo`, `--color-texto`, `--color-principal`) apuntan a ellas. Cambiar un color en un único sitio lo cambia en toda la web.

## Cómo editar el contenido

Abre `src/data/cv.json` y modifica lo que necesites:

- `skills`: nombre e icono de cada tecnología.
- `experiencia`: empresa, detalle y lista de puntos.
- `proyectos`: nombre, subtítulo, descripción, icono, enlace de demo y enlace del código.
- `contacto`: nombre, imagen y enlace de cada cubo (usa `mailto:` para el correo).

Si añades un elemento nuevo a cualquiera de estas listas, aparece solo en la página.

## Flujo de trabajo con Git

- El trabajo se desarrolló en la rama `feature/navbar-layout`, separada de `main`.
- Se hizo un commit por cada sección terminada.
- Al finalizar, los cambios se integraron en `main` mediante un Pull Request, con la descripción de lo realizado.

## Autor

Francisco Romero, proyecto realizado como estudiante de 2.º de Desarrollo de Aplicaciones Web (DAW).

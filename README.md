# CAP — Consultoría Adaptativa Pymes

Web estática de **CAP** lista para desplegar en **GitHub Pages**. El formulario
de contacto envía los mensajes por email mediante **Formspree** (servicio
gratuito, 50 envíos/mes en el plan gratis), con fallback a `mailto:` si
Formspree no está configurado o falla la red.

## Estructura

```
.
├── index.html              ← Web completa (imágenes embebidas en Base64)
├── styles.css              ← Todos los estilos
├── images/                 ← Fuente de las imágenes (por si quieres editar
│   ├── logo.png               el HTML y volver a referenciarlas como archivos)
│   ├── team-1.jpeg         ← Wei/Juan — Contabilidad
│   ├── team-2.jpeg         ← Jun — Marketing
│   ├── team-3.jpeg         ← Anaya — IA
│   └── team-4.jpeg         ← Ishita — Datos
├── .nojekyll               ← Evita que Pages procese el sitio como Jekyll
├── .gitignore
└── README.md               ← Este archivo
```

**Importante:** las imágenes van **embebidas en Base64 dentro del `index.html`**,
así que la web se ve correctamente aunque GitHub Pages no sirva bien la carpeta
`images/`. La carpeta se incluye solo como fuente editable, pero el HTML no la
necesita para funcionar.

## Paso 1 · Subir a GitHub

1. Crea un repositorio nuevo en <https://github.com/new>
   (público o privado; Pages funciona con ambos en plan gratuito).
2. Arrastra todos estos archivos al repo desde la web, o súbelos con `git`:

   ```bash
   git init
   git add .
   git commit -m "Primera versión CAP web"
   git branch -M main
   git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
   git push -u origin main
   ```

## Paso 2 · Activar GitHub Pages

En el repo → **Settings** → **Pages**:

- **Source:** `Deploy from a branch`
- **Branch:** `main` · carpeta `/ (root)`
- Pulsa **Save**.

En 30–60 segundos tu web estará disponible en:

```
https://TU_USUARIO.github.io/TU_REPO/
```

Si compraste un dominio (cap-consultoria.com, etc.) puedes conectarlo en la
misma pantalla en **Custom domain**.

## Paso 3 · Configurar el formulario de contacto (Formspree)

El formulario viene con un **placeholder**. Para que los mensajes lleguen a tu
email, crea una cuenta gratis en Formspree:

1. Ve a <https://formspree.io> y regístrate con `lluismoxo@gmail.com`.
2. Pulsa **New Form**, nómbralo "CAP Contacto".
3. Formspree te dará un endpoint tipo `https://formspree.io/f/xabcdwxyz`.
4. Abre `index.html` y busca esta línea cerca del final:

   ```js
   const FORMSPREE_ID = 'REEMPLAZAR_CON_TU_ID';
   ```

5. Reemplaza `REEMPLAZAR_CON_TU_ID` por la parte final del endpoint (solo el
   código `xabcdwxyz`).
6. Guarda, haz commit y push:

   ```bash
   git add index.html
   git commit -m "Configurar Formspree"
   git push
   ```

7. La primera vez que envíes el formulario, Formspree te enviará un email de
   confirmación para activarlo. Una vez confirmado, todos los envíos llegan a
   tu bandeja.

### ¿Qué pasa si no configuro Formspree?

El formulario sigue siendo funcional: detecta que no está configurado y abre
el cliente de email del usuario (Mail, Gmail web, etc.) con el mensaje
pre-rellenado a `lluismoxo@gmail.com`. El usuario solo tiene que pulsar
"Enviar".

## Probar en local

Como es web estática pura, basta con hacer doble clic en `index.html` o servir
la carpeta con un servidor ligero:

```bash
# Opción 1: Python (viene con macOS)
python3 -m http.server 8000
# → http://localhost:8000

# Opción 2: Node (si lo tienes instalado)
npx serve
```

## Personalización rápida

- **Logo y fotos del equipo:** reemplaza los archivos en `images/`.
- **Email y teléfono de contacto:** busca `lluismoxo@gmail.com` y `+34 660 380 592`
  en `index.html` y edítalos.
- **Colores:** edita las variables `--blue`, `--ink`, etc. al principio de
  `styles.css`.
- **Textos:** todos en `index.html`.

## Tecnologías

- HTML5 + CSS3 puro (sin frameworks).
- Google Fonts: Space Grotesk (titulares) + Inter (texto).
- Formspree para el formulario (gratis hasta 50 envíos/mes).
- GitHub Pages para el hosting (gratis, sin límite de tráfico razonable).

---

© 2026 CAP — Consultoría Adaptativa Pymes.

# Guía para publicar y editar el sitio

## 0. Cómo sacar los archivos de este chat

Los archivos viven en el espacio de trabajo de esta conversación, no en tu computadora.
Para subirlos a GitHub primero hay que bajarlos:

1. En el visor de archivos, abre el archivo y usa el **botón de descarga** (⬇).
2. O descarga el paquete completo: **`sabores-del-pasado.zip`** (un solo archivo con todo).
3. Descomprímelo en tu computadora (clic derecho → *Extraer todo*).

> Si estás en el celular es más incómodo. Para esta parte conviene hacerlo desde una computadora.
> Alternativa sin descargar nada: crear el archivo directamente en GitHub y **pegar** el contenido
> (ver sección 5, Opción C).

---

## 1. Crear el repositorio

En github.com, botón **`+`** (arriba a la derecha) → **Nuevo repositorio**.

| Campo | Valor |
|---|---|
| Propietario | la organización `Sabores-Del-Pasado` |
| Nombre del repositorio | `sabores-del-pasado.github.io` |
| Descripción | Recetario digital de la gastronomía tradicional de Calkiní, Campeche. |
| Visibilidad | **Público** |
| README / .gitignore / licencia | todos en **Off** |

Botón verde **Crear repositorio**.

> La URL final será: `https://sabores-del-pasado.github.io/`
> Debe crearse dentro de la organización y el repositorio debe llamarse `sabores-del-pasado.github.io`.

## 2. Subir los archivos

En la página del repositorio vacío, clic en el enlace **“subir un archivo existente”**.

Arrastra todos los archivos:

- `index.html`  ← el sitio
- `README.md`
- `GUIA.md`
- `robots.txt`
- `sitemap.xml`
- `.nojekyll`

> El archivo `.nojekyll` empieza con punto y algunos sistemas lo ocultan. Si no lo ves, en el explorador de archivos activa “mostrar archivos ocultos”. Si no lo subes, el sitio igual funciona; solo evita que GitHub ignore carpetas que empiecen con `_`.

Abajo, botón verde **Confirmar cambios**.

## 3. Activar GitHub Pages

1. En el repositorio: **Settings** (⚙️, arriba a la derecha).
2. Columna izquierda: **Pages**.
3. *Source*: **Deploy from a branch**.
4. Branch: **`main`** · carpeta: **`/ (root)`** → **Save**.
5. Espera 1–2 minutos y recarga. Arriba aparece: *“Your site is live at …”*.

## 4. Dar acceso al equipo

Todos deben tener su propia cuenta de GitHub (una por persona; no se comparten contraseñas).

1. En el repositorio: **Settings → Collaborators** (en algunas cuentas aparece como *Colaboradores*).
2. Botón **Add people** → escribe el usuario o el correo de cada compañero.
3. Rol: **Write** (para que puedan subir cambios sin poder borrar el repositorio).
4. Cada invitado recibe un correo o una notificación en GitHub y debe **aceptar** la invitación.

En repositorios **públicos** los colaboradores son gratis e ilimitados en el plan gratuito. En repos privados el plan gratuito limita a 3, y además Pages no publica desde repos privados.

## 5. Editar el sitio después

**Opción A — desde el navegador (la más fácil).**
Abre `index.html` en GitHub → icono del lápiz (✏️) → Edit. Cambia lo que necesites → **Commit changes**. En ~1 minuto se actualiza el sitio.

**Opción B — desde la computadora con Git.**

```bash
git clone https://github.com/Sabores-Del-Pasado/sabores-del-pasado.github.io.git
cd sabores-del-pasado.github.io
# editar archivos
git add .
git commit -m "Agrego la receta de ..."
git push
```

**Opción C — pegar el archivo directo en GitHub (sin descargar nada).**
En el repositorio: **Add file → Create new file** → en el nombre escribe `index.html` → pega todo el contenido del archivo → **Commit changes**. Sirve igual, pero es más tardado con archivos largos.

## 6. Agregar un platillo nuevo

Dentro de `index.html`, busca `const RECETAS = [` y copia un objeto completo. El formato es este:

```js
  {
    id: "pan-de-cazon",              // único, sin espacios ni acentos
    nombre: "Pan de cazón",
    emoji: "🐟",                     // se usa mientras no haya foto
    foto: "",                        // ej. "fotos/pan-de-cazon.jpg"
    comunidad: "Calkiní",
    region: "Calkiní (cabecera municipal)",
    categoria: "Plato fuerte",
    estado: "vigente",               // vigente | riesgo | pendiente
    dificultad: 3,                   // 1 a 4 (se dibuja con cucharitas)
    tiempo: "2 h (estimado)",
    resumen: "Una o dos líneas que describan el platillo.",
    ingredientes: ["Tortillas", "Cazón guisado", "Frijol negro", "Salsa de jitomate"],
    preparacion: ["Paso 1", "Paso 2", "Paso 3"],
    dificultadTexto: "Por qué es difícil de preparar.",
    dificultadResumen: ["3 pasos principales", "Ingredientes específicos", "Tiempo: 2 h"],
    variantes: [
      { nombre: "Otra versión", desc: "Cómo cambia.", emoji: "🍲" }
    ],
    cocinera: {                      // o null si aún no hay entrevista
      nombre: "Doña ...",
      iniciales: "EC",
      edad: 68,
      comunidad: "Nunkiní",
      etiquetas: ["Cocinera tradicional", "40 años de experiencia"],
      testimonio: "Lo que contó en la entrevista...",
      demo: false                    // true = datos de ejemplo (se muestra un aviso)
    },
    historia: "Contexto del platillo.",
    fuente: "Entrevista de trabajo de campo, 2026."
  },
```

La tarjeta, el buscador, los filtros, las pestañas y las cucharitas de dificultad se actualizan solos.

> **Ojo con el campo `demo`:** la ficha de Chamchames viene con `demo: true` porque la cocinera es un ejemplo inventado. Cuando hagan la entrevista real, cambien los datos y pongan `demo: false` (o borren esa línea) para que desaparezca el aviso rojo.

## 7. Fotos de los platillos

Las tarjetas muestran por ahora un emoji con la etiqueta *“Foto por documentar”*. Cuando tengan las fotografías:

1. Crea una carpeta `fotos/` en el repositorio y sube las imágenes en `.jpg` (que pesen menos de 300 KB cada una).
2. En cada receta pon la ruta en el campo `foto`, por ejemplo `foto: "fotos/chamchames.jpg"`. La imagen sustituye al emoji en la tarjeta y en la ficha (para el retrato de la persona se usa la inicial; si quieres foto, se agrega igual).

## 8. Recibir las recetas que envíe la gente

El formulario de la sección **Comunidad** hoy solo muestra un mensaje de confirmación en pantalla, no manda nada a ningún lado.

Para que sí lleguen:

1. Crea una cuenta gratis en [formspree.io](https://formspree.io).
2. Copia el endpoint que te dan (algo como `https://formspree.io/f/abcdwxyz`).
3. En `index.html`, busca `<form id="form-aporte"` y cámbialo a:
   `<form id="form-aporte" action="https://formspree.io/f/TU_CODIGO" method="POST">`
4. Y en el `<script>`, borra el bloque que empieza con `$("#form-aporte").addEventListener("submit"` para que el navegador envíe el formulario de verdad.

## 9. Para que la gente la encuentre en internet

Publicar la página **no** la vuelve famosa de un día para otro. Son dos cosas distintas:

### a) Compartir el enlace (inmediato)

Ya con Pages activo, tu dirección es pública y cualquiera con ese enlace la abre desde
cualquier teléfono o computadora. Pásalo por WhatsApp, en el grupo del salón, en el cartel
del proyecto, en un código QR. Eso funciona desde el primer minuto.

### b) Aparecer en Google (tarda días o semanas)

Google no conoce los sitios nuevos solo porque existan; hay que avisarle:

1. Entra a [search.google.com/search-console](https://search.google.com/search-console) con tu cuenta de Google.
2. **Añadir propiedad → Prefijo de URL** → escribe tu dirección completa
   (`https://sabores-del-pasado.github.io/`).
3. Te va a pedir verificar. Como el sitio es tuyo pero no puedes subir archivos de verificación
   fácilmente, usa la opción **Etiqueta HTML**: te da una línea como
   `<meta name="google-site-verification" content="ABC123...">` y esa línea se pega dentro del
   `<head>` de `index.html`. (Pídelo y te la inserto.)
4. Ya verificado, ve a **Inspección de URL**, pega tu enlace y pulsa **Solicitar indexación**.
5. Espera. Puede tardar de unos días a varias semanas en aparecer en los resultados.

Lo que ya tiene el sitio y ayuda: título y descripción propios, `sitemap.xml`, `robots.txt`,
etiquetas Open Graph (para que al compartir el enlace en WhatsApp se vea título y descripción)
y contenido en español con palabras que la gente sí busca (“recetas de Calkiní”, “comida tradicional de Campeche”).

> Búsquese tal cual: si alguien escribe *“recetas tradicionales de Calkiní”* en Google,
> la meta es que ahí salga. Eso depende de que Google la indexe, y de que la página tenga
> contenido suficiente (por eso importa seguir agregando recetas y entrevistas).

### c) El dominio propio (opcional, cuesta dinero)

Si algún día quieren algo como `saboresdelpasado.com`, se compra en Namecheap, GoDaddy o similar
(unos 200–400 pesos al año) y se conecta en **Settings → Pages → Custom domain**.
Para el proyecto escolar no es necesario.

## Problemas comunes

| Síntoma | Causa |
|---|---|
| 404 al entrar | Pages todavía no termina de publicar, o el archivo no se llama `index.html` |
| Se ve sin estilos | Se subió solo una parte del archivo, o se editó y se rompió una etiqueta |
| Los cambios no aparecen | Espera 1 minuto y recarga con Ctrl+F5 (Cmd+Shift+R en Mac) |
| El repositorio no aparece en Pages | Está en privado; cámbialo a público en Settings → General → Danger Zone |

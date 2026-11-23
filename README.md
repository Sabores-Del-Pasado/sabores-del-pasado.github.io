# Sabores del Pasado — Recetario de Calkiní

Sitio web del proyecto **“Rescate, documentación y difusión de la gastronomía tradicional del municipio de Calkiní, Campeche”**.
Instituto Tecnológico Superior de Calkiní · Ingeniería Informática · 5.º semestre.

## Qué hay aquí

| Archivo | Para qué sirve |
|---|---|
| `index.html` | Todo el sitio: estructura, estilos y funcionamiento. Es el único archivo necesario para que la página se vea. |
| `README.md` | Esta descripción (GitHub la muestra en la portada del repositorio). |
| `GUIA.md` | Instrucciones para publicar el sitio y para que el equipo lo edite. |
| `.nojekyll` | Evita que GitHub procese el sitio con Jekyll. No borrar. |
| `fotos/` | Fotografías de los platillos (por ahora, de referencia con licencia libre). |
| `CREDITOS.md` | Autor y licencia de cada fotografía. |

## Secciones del sitio

1. **Portada** con fotografía documentada y datos del proyecto.
2. **Franja de datos**: marco legal, enfoque local, documentación en campo y licencias.
3. **Recetario** con buscador, filtros por estado y favoritos.
4. **Metodología**: los cinco pasos con los que se documenta cada receta.
5. **Comunidad**: formulario para aportar recetas.
6. **Proyecto** y **Equipo**.
7. **Ficha de cada platillo**: pestañas de Receta, Variantes y Quién lo cocina.

## Cómo está organizado el contenido

Las recetas viven en una sola lista dentro de `index.html`, en la parte de arriba del bloque `<script>`:

```js
const RECETAS = [ { id:"enchiladas", nombre:"Enchiladas", ... } ];
```

Para agregar un platillo nuevo se copia un objeto completo y se cambian los datos. La página arma sola las tarjetas, el buscador y las fichas.

Campos de cada receta: `nombre`, `emoji`, `foto`, `comunidad`, `region`, `categoria`, `estado` (`vigente` / `riesgo` / `pendiente`), `dificultad` (1 a 4), `tiempo`, `resumen`, `ingredientes`, `preparacion`, `dificultadTexto`, `dificultadResumen`, `variantes`, `cocinera`, `historia`, `fuente`.

El formato completo está explicado en `GUIA.md`, sección 6.

## Estado del contenido

- **4 platillos con fotografía** de referencia (licencias libres, ver `CREDITOS.md`); chamchames y Si’in Tun esperan fotografía de campo.
- **5 fichas** con receta documentada (Canto Sosa, 2001): enchiladas, chamchames, frijol con puerco, tortillas de chaya y dulce de ciruela.
- **1 ficha pendiente**: Si’in Tun (Nunkiní), a la espera de la entrevista.
- **1 ficha de ejemplo** (Chamchames) con datos inventados de cocinera y variantes, marcada con un aviso visible, para mostrar cómo se verá cuando haya entrevistas reales.
- Las secciones “Quién lo cocina”, tiempos, costos y fotografías se completan con el trabajo de campo.

## Créditos y fuentes

- Canto Sosa, S. (2001). *Municipio de Calkiní. Breve descripción.*
- Decreto Número 74 (2013). LXI Legislatura del Congreso del Estado de Campeche.
- Meneses López, R. E. (2025); Meneses López, R. E. y González Gómez, L. (2025).
- Alcaldía de Calkiní (2026). Festival del Si’in Tun.

# Mixtape 4.0 · Inauguración de la cabina

**Ticket MIX-402 · Proyecto de cierre del Módulo 1 · Estación Umbral, Hangar 3**
**Para:** Mecánico de hangar · **De:** Nova · **Tiempo estimado:** 60 minutos · **Puntaje máximo:** 50

## La misión

Cuatro semanas después, Mixtape tiene tarjetas con props, un reproductor con estado, un formulario con validación y una cola de pedidos. Funciona, pero se ve igual en todas las estaciones: es la Mixtape de Nova.

Esta semana se inaugura tu cabina en la Estación Umbral. Nova te entrega las llaves: tú decides el nombre, el logo, los colores y la temática. También le sumas una pieza hecha por ti, un componente de React que no existía. Cuando alguien abra tu Mixtape, tiene que notar que es tuya.

Trabajas sobre tu Mixtape de la clase de hoy (con la cola de pedidos funcionando). No es un proyecto nuevo.

## Ticket 1 · Identidad de tu cabina (15 puntos)

1. **Temática:** elige una (por ejemplo: retro arcade, espacio profundo, bosque, neón, minimalista en blanco y negro). Escríbela en una línea al inicio de tu `README.md`.
2. **Nombre:** crea en `App.jsx` una constante con el nombre de tu cabina y pásala por props a `Encabezado`, que la muestra en el título en lugar de "Mixtape".
3. **Logo:** agrega al encabezado una `img` con la clase `cabina-logo`, un `alt` que describa la imagen y tu propio logo guardado en `public/`.
4. **Paleta:** cambia `--cabina-acento` y `--cabina-fondo` en `src/estilos-l4.css` y ajusta en `index.css` los colores del fondo general y de los títulos para que combinen con tu temática. Puedes cambiar la tipografía si quieres.

**Listo cuando:** puesta al lado de la Mixtape de la clase, tu cabina se reconoce como otra app: nombre, logo, colores y temática propios, y todo el texto se lee bien sobre el fondo.

## Ticket 2 · Tu componente (15 puntos)

Crea un componente nuevo en `src/components/`, con su propio archivo, y úsalo en `App.jsx`. Lo que haga lo decides tú, pero tiene que cumplir esto:

- Recibe al menos una prop.
- Usa `useState` **o** pinta una lista con `.map()` (con su `key`).
- Tiene estilos propios que siguen tu paleta.

Ideas si no se te ocurre nada (puedes inventar otra):

- **Canción del día:** muestra una canción de la playlist y un botón "Otra" que elige otra.
- **Mensaje de bienvenida:** saluda al nombre que recibe por props y cambia el saludo con un botón.
- **Contador de pedidos:** recibe `pedidos` y muestra cuántos hay y quién pidió el último.
- **Ánimo de la cabina:** botones con estados de ánimo; al elegir uno cambia el texto y el color de una tarjeta.

**Listo cuando:** el componente aparece en la app, hace lo que dice tu `README.md` y la consola no muestra errores.

## Ticket 3 · Favoritas de la cabina (10 puntos)

Lo que aprendiste hoy, aplicado a tu playlist.

1. En `App.jsx`, crea un estado `playlist` que empiece con el array `canciones`. Usa `playlist` en lugar de `canciones` en el buscador (`visibles`).
2. Agrega a cada tarjeta un botón con la clase `boton-favorita`. Si la canción es favorita, el `className` es `boton-favorita activa` y el texto dice "Quitar de favoritas"; si no, dice "Marcar favorita".
3. Escribe en `App.jsx` la función `alternarFavorita(id)`: cambia `favorita` al valor contrario solo en la canción con ese `id`, con `map` y un objeto copiado. La tarjeta recibe `id` y `onFavorita` por props.
4. Muestra en el encabezado "N favoritas", calculado de `playlist` en cada pintado, sin otro estado.

**Listo cuando:** al hacer clic, la tarjeta y su botón cambian al instante y el contador sube o baja. Con las canciones originales empieza en "3 favoritas".

## Ticket 4 · Pulido y entrega (10 puntos)

1. Revisa tu cabina como si fueras un usuario nuevo: los botones se ven como botones, el texto se lee, nada se sale de su caja y los mensajes de lista vacía siguen apareciendo.
2. La consola del navegador no muestra errores ni avisos.
3. Despliega el proyecto en Vercel.
4. En tu `README.md`: la temática, una captura de tu cabina, qué hace tu componente y el enlace al despliegue.

**Listo cuando:** el enlace de Vercel abre tu cabina funcionando y el `README.md` tiene las cuatro cosas.

## Extra para curiosos (sin puntos)

- Un botón "Quitar" en cada tarjeta con `filter`, y un botón "Restaurar playlist" cuando queda vacía.
- Una casilla "Solo favoritas" que filtre la playlist junto con el buscador.

No suma puntos: es para quien quiera seguir. Nova lo menciona en la revisión.

## Reglas del hangar

- Prohibido `push`, `splice`, `sort` y asignar una propiedad (`c.favorita = ...`) sobre algo que viene del estado o del array `canciones` importado.
- Lo que se puede calcular del array no necesita otro estado.
- Cada `.map()` lleva su `key`.
- Si te atascas más de 15 minutos en algo, pregunta antes de abrir el Archivo Jedi.

## Rúbrica (máximo 50 puntos)

| Ticket | Criterio | Puntos |
|---|---|---|
| 1 | Nombre por constante y props hacia `Encabezado` | 3 |
| 1 | Logo propio en `public/` con `alt` | 3 |
| 1 | Paleta propia aplicada a toda la app, con buen contraste | 6 |
| 1 | Temática clara y coherente (nombre, logo y colores van juntos) | 3 |
| 2 | Componente nuevo en su propio archivo, importado y usado en `App.jsx` | 4 |
| 2 | Recibe al menos una prop y la usa | 4 |
| 2 | Usa `useState` o `.map()` con `key`, y funciona sin errores | 4 |
| 2 | Estilos propios que siguen la paleta de la cabina | 3 |
| 3 | `playlist` en estado, y `alternarFavorita` con `map` y spread, sin mutar | 5 |
| 3 | Botón de favorita con `onFavorita(id)` y contador calculado | 5 |
| 4 | Interfaz pulida: se lee, se entiende y nada se ve roto | 4 |
| 4 | Consola sin errores ni avisos | 2 |
| 4 | Despliegue en Vercel y `README.md` con temática, captura, componente y enlace | 4 |
| | **Total** | **50** |

**Se descuentan puntos del criterio afectado si:** hay `push`, `splice`, `sort` o asignación directa sobre el estado, o falta la `key` en alguna lista.

**Entrega:** repositorio de GitHub y enlace del despliegue.

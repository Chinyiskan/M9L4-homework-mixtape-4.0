# Mixtape 4.0 · Inauguración de la cabina

**Ticket MIX-402 · Tarea de cierre del Módulo 1 · Estación Umbral, Hangar 3**
**Para:** Mecánico de hangar · **De:** Nova · **Tiempo estimado:** 50 a 60 minutos

## La misión

Cuatro semanas después, Mixtape tiene tarjetas con props, un reproductor con estado, un formulario con validación y una cola de pedidos. La cabina de la Estación Umbral se inaugura esta semana y Nova quiere la versión final: la playlist completa tiene que poder cambiar mientras la app corre.

Esta tarea reúne las cuatro misiones del módulo: props y listas (Misión 35), estado y formularios (Misión 36) y listas que cambian (Misión 37). Trabajas sobre tu Mixtape de la clase de hoy, no sobre un proyecto nuevo.

## Antes de empezar

- Parte del Mixtape que dejaste al terminar la clase (con la cola de pedidos funcionando).
- Los estilos nuevos ya están en `src/estilos-l4.css`: no tienes que escribir CSS. Las clases que vas a usar se nombran en cada ticket.
- Abre `App.jsx` y mira cómo están `pedidos`, `agregar`, `borrar` y `marcar`. La playlist va a funcionar igual.
- El reproductor de abajo sigue usando la lista original de la estación. No lo toques.

## Ticket 1 · Playlist viva (35 puntos)

1. En `App.jsx`, crea un estado `playlist` que empiece con el array `canciones` importado. Usa `playlist` en lugar de `canciones` en el buscador (`visibles`), en la condición de playlist vacía y en el total del encabezado.
2. Agrega a cada tarjeta un botón con la clase `boton-favorita`. Cuando la canción es favorita, el `className` es `boton-favorita activa` y el texto dice "Quitar de favoritas"; si no, dice "Marcar favorita". Pon los botones dentro de un `div` con la clase `tarjeta-acciones` al final de la tarjeta.
3. Escribe en `App.jsx` la función `alternarFavorita(id)`. Cambia `favorita` al valor contrario solo en la canción con ese `id`. La tarjeta recibe `id` y `onFavorita` por props y llama `onFavorita(id)` desde el botón.
4. Muestra en el encabezado cuántas canciones son favoritas, con el texto "N favoritas" y la clase `contador-favoritas`. El número se calcula de `playlist` en cada pintado, sin otro estado.

**Listo cuando:** al hacer clic en el botón, la etiqueta de la tarjeta y su botón cambian al instante, y el contador sube o baja. Con las canciones originales debe empezar en "3 favoritas".

## Ticket 2 · Quitar y agregar (35 puntos)

1. Agrega a cada tarjeta un botón con la clase `boton-quitar` y el texto "Quitar", al lado del de favorita. Escribe `quitarCancion(id)` en `App.jsx`: deja en `playlist` todas las canciones menos la de ese `id`. La tarjeta recibe `onQuitar` por props.
2. Haz que `agregar` (la función del formulario de pedidos) también agregue una canción nueva a `playlist`, además de agregar el pedido a la cola. La canción nueva es un objeto con esta forma (`titulo` es lo que se pidió y `artista` es quien lo pidió):

```jsx
{
    id: nuevo.id,
    titulo,
    artista: quien,
    album: "Pedidos de la cabina",
    duracion: "3:00",
    portada: "/portadas/luces-del-hangar.webp",
    anio: 2026,
    reproducciones: 0,
    favorita: false,
    energia: 50,
}
```

**Listo cuando:** al pedir una canción aparece una tarjeta nueva al final de la playlist y un pedido nuevo en la cola. "Quitar" en una tarjeta la elimina, y el total del encabezado baja. La tarjeta quitada no vuelve al escribir en el buscador.

## Ticket 3 · Tu cabina (30 puntos)

1. **Playlist vacía:** quita todas las canciones. Debe aparecer el mensaje "Aún no hay canciones en la estación" (ya existe en `App.jsx`) y, debajo, un botón con la clase `boton-restaurar` y el texto "Restaurar playlist". El botón deja `playlist` otra vez igual al array `canciones` importado.
2. **Nombre de tu cabina:** crea en `App.jsx` una constante con el nombre de tu cabina y pásala por props a `Encabezado`, que lo muestra en el título en lugar de "Mixtape".
3. **Logo:** agrega al encabezado una `img` con la clase `cabina-logo`, el atributo `alt` con texto y tu propio logo. Puedes usar `/favicon.svg` mientras no tengas uno, pero el logo entregado debe ser uno que elegiste tú. Guárdalo en `public/`.
4. **Colores:** en `src/estilos-l4.css`, cambia los valores de `--cabina-acento` y `--cabina-fondo`.

**Listo cuando:** el botón "Restaurar playlist" devuelve las cinco canciones originales con sus favoritas de origen (aunque antes hayas marcado o quitado otras). La cabina se ve distinta a la de la clase: nombre, logo y los dos colores cambiados.

## Bonus · Solo favoritas (+10 puntos, aparte)

1. Agrega un estado booleano `soloFavoritas` y una casilla (`input type="checkbox"` controlado) con el texto "Solo favoritas", dentro de un `label` con la clase `solo-favoritas`, encima de las tarjetas.
2. `visibles` filtra por la búsqueda y por la casilla al mismo tiempo: con la casilla marcada solo se muestran las favoritas que coinciden con el texto buscado.

**Listo cuando:** con la casilla marcada y el buscador vacío ves solo las favoritas, y escribir en el buscador reduce esa lista sin desmarcar la casilla.

## Reglas del hangar

- Prohibido `push`, `splice`, `sort` y asignar una propiedad (`c.favorita = ...`) sobre algo que viene del estado o del array `canciones` importado.
- Lo que se puede calcular del array no necesita otro estado.
- La consola del navegador no puede mostrar errores ni avisos al entregar.
- Cada `.map()` lleva su `key` con el `id` de la canción.

## Rúbrica

Los puntos de la tabla suman 100 (el bonus va aparte). El calificador los escala al máximo de la entrega.

| Ticket | Criterio | Puntos |
|---|---|---|
| 1 | `playlist` es un estado inicializado con `canciones` y el buscador, el total y la condición de lista vacía lo usan | 10 |
| 1 | `alternarFavorita` usa `map` y copia el objeto con spread, sin mutar | 10 |
| 1 | El botón de favorita avisa al padre con `onFavorita(id)` y cambia texto y clase | 8 |
| 1 | El contador de favoritas se calcula de `playlist`, sin estado extra | 7 |
| 2 | `quitarCancion` usa `filter` con la condición correcta y la tarjeta llama `onQuitar(id)` | 15 |
| 2 | `agregar` suma la canción pedida a `playlist` con un array nuevo (spread) y el pedido sigue entrando a la cola | 15 |
| 2 | La canción nueva tiene todos los campos y su tarjeta se pinta sin errores | 5 |
| 3 | Con la playlist vacía aparece el mensaje y "Restaurar playlist" devuelve las cinco originales | 10 |
| 3 | Nombre de la cabina por una constante y props hacia `Encabezado` | 8 |
| 3 | Logo propio con `alt` y los dos colores cambiados en `estilos-l4.css` | 12 |
| Bonus | Casilla "Solo favoritas" funcionando junto con el buscador | +10 |

**Se descuentan puntos del criterio afectado si:** hay `push`, `splice`, `sort` o asignación directa sobre el estado; hay errores o avisos en la consola; falta la `key` en alguna lista.

**Entrega:** repositorio de GitHub y despliegue del proyecto, como en las tareas anteriores. El bonus se suma aparte y no cubre puntos perdidos en los tickets obligatorios.

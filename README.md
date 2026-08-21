# Torremar: Duc In Altum

Shooter cooperativo en primera persona, estilo DOOM, ambientado en el colegio
Torremar. Todo el juego cabe en un solo archivo: **`index.html`**. No hay
dependencias que instalar ni nada que compilar; se abre en el navegador y ya.

Los gráficos son 100 % procedurales (Canvas 2D), el motor es un raycaster DDA
con z-buffer de una dimensión, y el multijugador va por WebRTC con PeerJS.

## Cómo jugar

Abre `index.html` en un navegador moderno (Chrome, Edge o Firefox). Para el
multijugador en red hace falta conexión, porque PeerJS se carga de una CDN; el
resto funciona sin internet.

## Modos

| Modo | Qué es |
|---|---|
| **50 salas** | La campaña. Salas encadenadas con jefe en la 10, 20, 30 y 50, y botín cada 5. |
| **Horda sin fin** | Una sola arena y oleadas que no paran. Minijefe cada 5, jefe cada 10, mejora cada 3 y arena nueva cada 10. |

Ambos se juegan en solitario, en cooperativo o las dos cosas, y con seis
dificultades: Putita, Fácil, Normal, Difícil, Souls-Like e Imposible. En
Imposible empiezas solo con machete y Glock: el resto del arsenal lo guardan
los jefes.

## Multijugador

- **En red:** hasta 8 jugadores. Se crea una sala con código, se entra con
  código o se busca una partida abierta.
- **En el mismo equipo:** hasta 4 en pantalla dividida estilo Black Ops. El J1
  va con teclado y ratón, y el resto entra pulsando cualquier botón de un mando
  de PlayStation o Xbox. Cada uno tiene sus propias asignaciones (pestañas
  J1–J4) y su propio menú de personaje.
- **Las dos a la vez:** desde la sala del sofá se puede abrir la partida a otras
  PCs. Tres en tu casa, dos en la de un amigo, dos en la de otro y uno solo son
  ocho en la misma partida.

## Controles (por defecto)

| Acción | Teclado | Mando |
|---|---|---|
| Moverse | W A S D | Stick izquierdo |
| Mirar | Ratón | Stick derecho |
| Disparar | Ratón izq. | RT / R2 |
| Fuego alternativo | Ratón der. | LT / L2 |
| Cambiar de arma | 1–5 o rueda | L1/LB y R1/RB |
| Recargar | R | X / □ |
| Esquivar | F | B / ○ |
| Correr | Mayús izq. | R3 |
| Agacharse | C | L3 |
| Saltar | Espacio | A / ✕ |
| Granada rápida | G | Cruceta ↑ |
| Cantimplora | H | Y / △ |
| Furia | Q | Cruceta ↓ |
| Mapa | Tab | Back |
| Pausa | Esc | Start |

Todo se puede reasignar en **⚙ Controles y opciones**, que además tiene ajustes
de confort: sacudida de cámara, destellos, sangre en el visor, grano de imagen,
tamaño del HUD, volumen y mira de alto contraste.

## Mecánicas

- **Esquiva** con fotogramas de invulnerabilidad. La barra llena da tres
  seguidas y se rellena sola muy rápido. Correr no gasta nada.
- **Deslizamiento**: correr y agacharse a la vez.
- **Ejecución**: machete a bocajarro sobre alguien tocado o aturdido lo revienta
  y te cura.
- **Parada**: el tajo pesado del machete abre una ventana en la que las balas
  enemigas salen devueltas al doble de daño.
- **Furia DUC IN ALTUM**: la barra morada se llena al hacer daño. Al soltarla,
  siete segundos de munición infinita, cadencia doble y un aura que quema.
- **Mejoras**: 26 distintas, se acumulan durante la run y se pierden al morir.
- **Modificadores de sala**: apagón, humo denso, horda, guardia de élite, turno
  doble, almacén volátil, hora del recreo, semana de exámenes y huelga de
  profesores.

## Bestiario

Once enemigos rasos (corredor, vigilante, mole, profesor de pizarra, becario,
profesor de física, enfermería, bedel con escudo, delegado de clase, profesor de
química y alumno en patinete), cinco minijefes (Ricky, Miguelito, Josué,
Castells y Ángulo) y cuatro jefes que van de menos a más: Roberto, Arturo, David
y Jorge Coronel.

## Personalización

Apodo, tono de piel, cuatro uniformes, 22 peinados con color libre, 12
expresiones faciales, 15 cosas para la cabeza, 9 gafas y 9 tipos de vello
facial, con color de accesorio propio. Todo se guarda y viaja por la red.

## Marcas

Se guarda la mejor marca por dificultad y por modo, y hay 14 medallas. La
**semilla** de la sala de espera fija la partida: con el mismo código de seis
caracteres salen las mismas salas, en el mismo orden y con los mismos
modificadores.

## Guardado

Todo se guarda en el `localStorage` del navegador:

| Clave | Qué guarda |
|---|---|
| `torremar.char` | Personaje: apodo, piel, uniforme, pelo, rostro y accesorios |
| `torremar.keys` | Teclas del J1 |
| `torremar.pads` | Mandos de J2, J3 y J4 |
| `torremar.best` | Marcas por dificultad, por modo y medallas |
| `torremar.opts` | Ajustes de confort |

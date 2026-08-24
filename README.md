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

### Cómo se comporta la red

- **Nada de tirones.** Con cada aviso del anfitrión se calcula la velocidad de
  cada compañero, enemigo y proyectil, y entre paquete y paquete se sigue su
  rumbo. Hay tope de 0,3 s para que nada se vaya de paseo si se pierde un
  paquete, freno si el destino cae en una pared y salto directo si el anfitrión
  teletransporta algo. Los avatares remotos giran por el arco corto.
- **22 avisos por segundo** de estado de jugador y el doble de instantáneas del
  mundo que antes. Los objetos y los trastos, que ya viajan por evento, solo se
  mandan enteros cuando cambian.
- **Ping real** medido de ida y vuelta: se ve por jugador en la sala de espera y
  en el listado del HUD, con color según lo alto que sea. Si el enlace se queda
  mudo más de dos segundos sale un aviso en pantalla.
- **Reconexión automática:** si se cae el enlace con el anfitrión no te echa al
  menú, reintenta cinco veces con esperas crecientes. Si te expulsan o la sala
  está llena, no reintenta.
- **Entrar a mitad de partida:** quien se conecta con la partida ya empezada
  recibe la sala en curso y una instantánea del mundo, y aparece vivo donde
  toca.
- **Enlace directo:** el botón ENLACE de la sala copia una dirección con
  `#sala=CÓDIGO` que abre el juego en la pantalla de unirse con el código ya
  puesto.
- **Marcas de sitio:** apuntas y pulsas `E` (cruceta → en mando) y todo el
  equipo ve un rombo flotante donde miras, una flecha en el borde de la pantalla
  y una línea en el registro. El tipo sale solo: enemigo, botín, salida o
  genérica. Cada jugador tiene una marca a la vez y duran siete segundos.
- **Errores en cristiano:** «no hay ninguna sala con ese código», «tu red está
  bloqueando la conexión directa»… en vez de los códigos internos de PeerJS.

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
| Marcar sitio | E | Cruceta → |
| Mapa | Tab | Back |
| Pausa | Esc | Start |

Todo se puede reasignar en **⚙ Controles y opciones**, que además tiene ajustes
de confort: calidad gráfica, sacudida de cámara, destellos, sangre en el visor,
grano de imagen, tamaño del HUD, volumen y mira de alto contraste.

La **calidad gráfica** viene en AUTO: el juego mide su propio fotograma y sube o
baja solo la resolución interna, las columnas de pared, el detalle del suelo, el
polvo y los adornos. También se puede clavar en ALTA, MEDIA o BAJA.

El disparo va a donde apunta la mira, también en vertical: la bala sigue la
pendiente de la vista, comprueba a qué altura del enemigo llega y se para en el
techo. El cuarto superior del sprite es disparo a la cabeza. El retroceso sube
el arma y la vista vuelve sola al blanco.

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

Apodo, tono de piel, dos uniformes del colegio, 22 peinados con color libre, 12
expresiones faciales, 15 cosas para la cabeza, 9 gafas y 9 tipos de vello
facial. El gorro y las gafas llevan **cada uno su color**, con rueda de tono,
cuadro de saturación y luminosidad, preajustes y HEX. Todo se guarda y viaja por
la red, y el tono de piel también se ve en la mano que sostiene el arma.

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

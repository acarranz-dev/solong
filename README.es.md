# so_long

**Un pequeño juego 2D en C con vista isométrica y enemigos que patrullan.**

[English](README.md) · [Català](README.ca.md) · **Español**

`Parte del Common Core de 42 Barcelona` · `Rango 2` · `C` · `MLX42`

<p align="center"><img src="demo/demo.gif" alt="Demo" width="640" /></p>

---

## Descripción

El jugador tiene que recoger todos los objetos del mapa y después llegar a la salida. Los mapas son ficheros de texto (`.ber`) y se validan enteros antes de empezar la partida. Además de la parte obligatoria, esta versión dibuja el mapa en **perspectiva isométrica** y añade **enemigos que patrullan** por el mapa.

## Qué enseña

- Un **bucle de juego** con una librería gráfica: ventanas, imágenes y eventos de teclado.
- Leer y validar un mapa: paredes cerradas, una salida, un jugador y al menos un objeto.
- **Flood fill** para comprobar que de verdad se puede llegar a cada objeto y a la salida.
- Convertir coordenadas de la cuadrícula a coordenadas isométricas de pantalla.
- Liberar todos los recursos al cerrar el juego.

## Cómo funciona

El mapa se lee en una cuadrícula 2D y se comprueba. Un flood fill desde el jugador marca cada casilla accesible; si no se puede llegar a un objeto o a la salida, el mapa se rechaza. En cada fotograma la cuadrícula se dibuja casilla a casilla, convirtiendo cada `(x, y)` a coordenadas isométricas. El jugador se mueve con el teclado, se muestra el contador de movimientos y tocar un enemigo termina la partida.

| Tecla | Acción |
|:--:|:--|
| `W` `A` `S` `D` | moverse |
| `ESC` | salir |

| Carácter del mapa | Significado |
|:--:|:--|
| `1` | pared |
| `0` | suelo |
| `P` | jugador |
| `C` | objeto para recoger |
| `E` | salida |
| `e` | enemigo |

## Compilar y ejecutar

```bash
git clone https://github.com/acarranz-dev/solong.git
cd solong

sudo apt install cmake libglfw3-dev   # MLX42 needs CMake and GLFW
make                                  # also builds the MLX42 library
./solong mapas/mapa_01.ber
```

## Estructura del proyecto

```
solong/
├── src/
│   ├── parser.c, check_map.c, visited.c     # read the .ber file and validate the map
│   ├── load_images.c, render*.c, utils.c    # textures and isometric drawing
│   ├── key_hook.c, moving.c, move_jou.c     # keyboard input and player movement
│   ├── enemies_init.c, enemy_move.c, patrol_enemies.c   # enemies
│   └── tomb.c, stop_game.c, init_end.c      # end of game
├── mapas/                                   # example maps
├── MLX42/                                   # graphics library
└── Makefile
```

---

[Más proyectos en mi perfil](https://github.com/acarranz-dev)

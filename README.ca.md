# so_long

**Un petit joc 2D en C amb vista isomètrica i enemics que patrullen.**

[English](README.md) · **Català** · [Español](README.es.md)

`Part del Common Core de 42 Barcelona` · `Rang 2` · `C` · `MLX42`

<p align="center"><img src="demo/demo.gif" alt="Demo" width="640" /></p>

---

## Descripció

El jugador ha de recollir tots els objectes del mapa i després arribar a la sortida. Els mapes són fitxers de text (`.ber`) i es validen sencers abans de començar la partida. A més de la part obligatòria, aquesta versió dibuixa el mapa en **perspectiva isomètrica** i afegeix **enemics que patrullen** pel mapa.

## Què ensenya

- Un **bucle de joc** amb una llibreria gràfica: finestres, imatges i esdeveniments de teclat.
- Llegir i validar un mapa: parets tancades, una sortida, un jugador i almenys un objecte.
- **Flood fill** per comprovar que es pot arribar de veritat a cada objecte i a la sortida.
- Convertir coordenades de la graella a coordenades isomètriques de pantalla.
- Alliberar tots els recursos quan es tanca el joc.

## Com funciona

El mapa es llegeix en una graella 2D i es comprova. Un flood fill des del jugador marca cada casella accessible; si no es pot arribar a un objecte o a la sortida, el mapa es rebutja. A cada fotograma la graella es dibuixa casella a casella, convertint cada `(x, y)` a coordenades isomètriques. El jugador es mou amb el teclat, es mostra el comptador de moviments i tocar un enemic acaba la partida.

| Tecla | Acció |
|:--:|:--|
| `W` `A` `S` `D` | moure's |
| `ESC` | sortir |

| Caràcter del mapa | Significat |
|:--:|:--|
| `1` | paret |
| `0` | terra |
| `P` | jugador |
| `C` | objecte per recollir |
| `E` | sortida |
| `e` | enemic |

## Compilar i executar

```bash
git clone https://github.com/acarranz-dev/solong.git
cd solong

sudo apt install cmake libglfw3-dev   # MLX42 needs CMake and GLFW
make                                  # also builds the MLX42 library
./solong mapas/mapa_01.ber
```

## Estructura del projecte

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

[Més projectes al meu perfil](https://github.com/acarranz-dev)

# so_long

**A small 2D game in C with an isometric view and patrolling enemies.**

**English** · [Català](README.ca.md) · [Español](README.es.md)

`Part of the 42 Barcelona Common Core` · `Rank 2` · `C` · `MLX42`

<p align="center"><img src="demo/demo.gif" alt="Demo" width="640" /></p>

---

## Description

The player has to collect every item on the map and then reach the exit. Maps are plain text files (`.ber`) and are fully validated before the game starts. On top of the mandatory part, this version draws the map in **isometric perspective** and adds **enemies that patrol** the map.

## What it teaches

- A **game loop** with a graphics library: windows, images and keyboard events.
- Reading and validating a map: closed walls, one exit, one player, at least one item.
- **Flood fill** to check that every item and the exit can actually be reached.
- Converting grid coordinates to isometric screen coordinates.
- Freeing every resource when the game closes.

## How it works

The map is read into a 2D grid and checked. A flood fill from the player marks every reachable cell; if an item or the exit is not reachable, the map is rejected. Each frame, the grid is drawn tile by tile, converting each cell `(x, y)` to isometric coordinates. The player moves with the keyboard, the move counter is shown, and touching an enemy ends the game.

| Key | Action |
|:--:|:--|
| `W` `A` `S` `D` | move |
| `ESC` | quit |

| Map character | Meaning |
|:--:|:--|
| `1` | wall |
| `0` | floor |
| `P` | player |
| `C` | item to collect |
| `E` | exit |
| `e` | enemy |

## Build and run

```bash
git clone https://github.com/acarranz-dev/solong.git
cd solong

sudo apt install cmake libglfw3-dev   # MLX42 needs CMake and GLFW
make                                  # also builds the MLX42 library
./solong mapas/mapa_01.ber
```

## Project structure

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

[More projects on my profile](https://github.com/acarranz-dev)

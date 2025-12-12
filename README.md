# Cub3D

Wolfenstein 3D-style 3D engine using the raycasting algorithm for real-time rendering.

## Description

This project implements a real-time 3D renderer from a first-person perspective. The player can explore a maze rendered in 3D with textured walls. The project demonstrates fundamental concepts of 3D graphics, computational geometry, and performance optimization.

## Technologies

- **Algorithm:** Raycasting
- **Graphics library:** MiniLibX
- **Language:** C
- **Standard:** C89/C90

## Features

- Real-time 3D rendering using raycasting
- Texture loading and mapping (North, South, East, West)
- Smooth first-person navigation
- Configurable floor and ceiling colors
- Keyboard (and optional mouse) event handling
- `.cub` configuration file parsing
- Basic collision detection
- Efficient memory management

## Included Files

- `cub3d.c` - Main program
- `Includes/` - Header files
- `Parse/` - `.cub` file parser
- `Execute/` - Rendering engine and main loop
- `Library/` - Utility functions
- `textures/` - Texture files
- `Maps/` - Example maps

## Build

```bash
make              # Build cub3d
make clean        # Remove object files
make fclean       # Remove executables and object files
make re           # Rebuild from scratch
```

## Usage

```bash
./cub3d path/to/map.cub
```

## `.cub` File Format

The configuration file must include texture paths, colors and a map layout. Example:

```
NO ./textures/north.xpm
SO ./textures/south.xpm
WE ./textures/west.xpm
EA ./textures/east.xpm
F 220,100,0
C 225,30,0

111111
100001
1P0001
111111
```

Components:
- `NO/SO/WE/EA` - Texture paths
- `F` - Floor color (RGB)
- `C` - Ceiling color (RGB)
- Map: `0` (floor), `1` (wall), `N/S/E/W` (player starting position and orientation)

## Controls

| Key | Action |
|---|---|
| W | Move forward |
| A | Move left |
| S | Move backward |
| D | Move right |
| Left Arrow | Rotate view left |
| Right Arrow | Rotate view right |
| ESC | Exit |

## Requirements

- C compiler (gcc, clang, etc.)
- Make
- MLX42 (included or provided separately)
- Linux or macOS
- Graphic dependencies on Linux (libX11, libXext, etc.)

## Raycasting Overview

The raycasting pipeline:
1. Cast rays from the player's position for each screen column
2. Detect wall collisions for each ray
3. Compute distance to the nearest wall
4. Render vertical columns with heights proportional to distance
5. Apply textures based on wall orientation and hit position

## Optimizations

- Optimized distance calculations
- Precomputed trig lookup tables where appropriate
- Efficient column rendering and minimal per-pixel overhead
- Preallocated memory for buffers

## Map Validation

The program validates:
- The map is fully enclosed by walls
- Single unique player start position
- Only valid characters in the map
- Texture files are accessible
- Color values are within valid RGB ranges

## Error Handling

The program reports and handles:
- Missing or invalid configuration files
- Corrupt or missing textures
- Incomplete configuration entries
- Memory allocation failures
- Graphics initialization errors

---

Last updated: December 2025

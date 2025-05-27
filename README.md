# cub3D 🐺 - Mi Primer Raycaster 3D (Proyecto en Equipo)

![cub3D GIF](URL_DEL_GIF_AQUI) ## Introducción

`cub3D` es un proyecto de [42 School](https://www.42.fr/) inspirado en el legendario **Wolfenstein 3D**, considerado el primer *First-Person Shooter* (FPS) de la historia. El objetivo es crear una representación gráfica 3D del interior de un laberinto desde una perspectiva en primera persona, utilizando los principios del **Ray-Casting** y la librería gráfica **MiniLibX**.

Este proyecto fue desarrollado en equipo, aprovechando nuestras fortalezas para recrear esta experiencia clásica.

## El Desafío

El reto principal es renderizar una vista 3D dinámica y navegable a partir de un mapa 2D. Esto implica:

1.  **Parsing:** Analizar un archivo de descripción de escena (`.cub`) que contiene la configuración del mapa, las texturas y los colores.
2.  **Ray-Casting:** Implementar el algoritmo de lanzamiento de rayos para calcular qué ven los ojos del jugador y cómo renderizarlo.
3.  **Gráficos 2D/3D:** Usar la `MiniLibX` para dibujar en una ventana, cargar texturas y representar un entorno 3D convincente.
4.  **Interacción:** Manejar eventos del teclado para el movimiento y la rotación del jugador.

## Nuestro Enfoque y Contribuciones 🤝

Siendo un equipo de dos, dividimos el trabajo de la siguiente manera, aunque ambos participamos activamente en todas las fases:

* **[jeandrad1](https://github.com/jeandrad1)** se centró principalmente en la **Ejecución y Renderizado**:
    * Implementación del algoritmo principal de **Ray-Casting**.
    * Interacción con la **MiniLibX** para el dibujado de la ventana, píxeles y texturas.
    * Manejo de los **eventos del teclado** (W, A, S, D, flechas, ESC) para el movimiento y la vista.
    * Cálculo de la perspectiva y el dibujado de las paredes, suelo y techo.

* **[Tu Usuario GitHub]** se centró principalmente en el **Parsing y la Gestión de Datos**:
    * Desarrollo del **parser** para leer y validar los archivos `.cub`.
    * Carga y gestión de las **texturas** (Norte, Sur, Este, Oeste).
    * Procesamiento de los **colores** de suelo y techo.
    * Validación de la estructura del mapa (cerrado, caracteres válidos, etc.).
    * Estructuración de los datos para que el motor de renderizado pudiera usarlos.

Esta colaboración nos permitió abordar tanto la lógica de renderizado como la gestión de datos de manera eficiente.

## Características Implementadas

* **Renderizado Ray-Casting:** Creación de una vista 3D desde una perspectiva en primera persona.
* **MiniLibX:** Uso exclusivo de la `MiniLibX` para toda la gestión gráfica.
* **Mapa `.cub`:** El programa acepta un archivo `.cub` como argumento.
    * El mapa se compone de `0` (espacio), `1` (muro) y `N,S,E,W` (jugador).
    * El mapa debe estar cerrado por muros.
    * Parseo de texturas (`NO`, `SO`, `WE`, `EA`) y colores (`F`, `C`).
    * Gestión de errores para mapas/configuraciones inválidas.
* **Texturas:** Muestra diferentes texturas según la orientación del muro (N, S, E, O).
* **Colores Suelo/Techo:** Colores personalizables para el suelo y el techo.
* **Movimiento:**
    * Teclas W, A, S, D para moverse.
    * Flechas izquierda/derecha para rotar la vista.
* **Gestión de Ventana:**
    * La ventana se gestiona de forma fluida (minimizar, etc.).
    * ESC o la cruz roja cierran el programa limpiamente.

## Parte Bonus (Opcional)

* Colisiones con las paredes.
* Minimapa.
* Puertas que se abren y cierran.
* Sprites animados.
* Rotación de la vista con el ratón.

## Cómo Usar

### Requisitos

* Un compilador C (como `gcc` o `clang`).
* `make`.
* `MiniLibX` instalada o sus fuentes.
* Librerías matemáticas (`-lm`).

### Compilación

1.  **Clona el repositorio:**
    ```bash
    git clone [https://github.com/tu_usuario/cub3d.git](https://github.com/tu_usuario/cub3d.git)
    cd cub3d
    ```
2.  **(Opcional) Si usas `libft`, asegúrate de que esté presente y tu `Makefile` la compile.**
3.  **Compila el proyecto:**
    ```bash
    make
    ```
    Esto creará el ejecutable `cub3D`.

### Ejecución

```bash
./cub3D maps/mapa_valido.cub

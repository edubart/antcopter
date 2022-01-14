# Antcopter - (WASM4 Game Jam 2022)

This is a minimal game using [Nelua](https://github.com/edubart/nelua-lang)
programming language for the [WASM-4 Game Jam](https://itch.io/jam/wasm4).

![Demo](https://cdn.discordapp.com/attachments/890276476883198042/929714960387407923/game-2022-01-09_09.28.02.mp4)

## Why am I participating?

WASM-4 has interesting constraints of being limited to 64KB of memory usage,
64KB cart size and limited API availability, this scenario is very similar
to the ones of embedded devices. It is interesting for me to test the Nelua
programming language in such constraints, so I could potentially make
it perform better in embedded world, by improving Nelua's standard library
plus its garbage collector to use minimal stack space,
minimal memory usage, minimal runtime code size and
be more freestanding (without dependencies in the C runtime).
While developing this game small enhancements were made in the Nelua compiler
in that regard, although the language was already doing great!

## Play it

Play the game at in the browser or in the mobile at
https://edubart.github.io/antcopter/index.html

## Game mechanics

There are 20 levels and 80 fruits,
it should take about 30 minutes for an inexperienced player to finish all of them,
while very skilled players can finish all levels under 5 minutes.

Game controls.
* Press left and right to move horizontally.
* Press down to fall faster.
* Press Z to jump.
* Hold Z while in the air to glide.
* Hold X to lift up (unlocked only after Level 10).
* TIP: After level 10, holding Z and X simultaneously can be easier.

## Tools used

All levels were made with
[Tiled](https://www.mapeditor.org/) map editor,
then exported to `.lua` files and built into the game sources via Nelua's Lua preprocessor.

All sprites sprite sheet and fonts were made with
[Aseprite](https://www.aseprite.org/) pixel art editor,
then exported to `.ppm` files, and built into the game sources
via the Nelua's Lua preprocessor.

The music was composed in [Beepbox](https://www.beepbox.co/) and
then the melody was manually built into the sources.

## Source structure

The game sources is split as the following:

* `src/wasm4.nelua` - WASM4 bindings
* `src/neco.nelua` - Mini game framework on top of SDL2, with auxiliary functions for drawing, playing sound and retrieving input
* `src/w4neco.nelua` - Mini game framework on top of WASM4, with auxiliary functions for drawing, playing sound and retrieving input
* `src/antcopter.nelua` - All the game logic plus auxiliary functions in a single file.
* `assets` - Folder with all sprite sheet, font, map and tileset.

## Design choices

To minimize memory usage and disk size and fit in WASM-4 constraints,
the following design choices were made:

* A custom heap allocator with a fixed static memory buffer was used,
instead of using libc `malloc()` and `free()`.
* Game data and objects use buffers and fields with minimal size, to save memory usage.
* Game data is loaded from `assets` via the preprocessor,
* Nelua's garbage collector was disabled, this saves about 8KB of disk size and uses
less runtime heap memory, although the game works also works fine with
GC enabled!

The complete game fits in 33KB cart size and uses less than 32KB of heap memory.

## Compiling

With WASM4 properly set, just do:
```
make
w4 run build/cart.wasm
```

## Credits

Game play, code and sound was made by myself, edubart.
Sprites were made by Isabella.

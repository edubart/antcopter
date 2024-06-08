# Antcopter

A speedrun platformer game written in [Nelua](https://nelua.io/) for [RIV](https://docs.rives.io) fantasy console.

You can play it in your browser
[here](https://edubart.itch.io/antcopter)

![Screenshot](https://raw.githubusercontent.com/edubart/antcopter/master/antcopter.png)

## Description

There are 20 levels and 80 fruits. How fast can you complete all levels while collecting all blueberry fruits?

Game controls:

- Press left and right to move horizontally.
- Press down to fall faster.
- Press Z to jump.
- Hold Z while in the air to glide.
- Hold X to lift up (unlocked only after Level 10).

*TIP*: After level 10, holding Z and X simultaneously can be easier.

Some levels can be challenging, be warned! It should take about 30 minutes for an inexperienced player to finish all of them,
and less than 5 minutes for a skilled player.

## Compiling

First make sure you have the RIV SDK installed in your environment, then just type `make` to compile.
You can also play it by typing `make run`.

## History

Originally this game was made for [WASM-4 fantasy console](https://wasm4.org/play/antcopter) for its first [game jam](https://itch.io/jam/wasm4) and it was the winner of the jam.

Later it was ported to RIV fantasy console,
so the code has an abstraction layer in the middle, and can look messy,
maybe I will cleanup someday.

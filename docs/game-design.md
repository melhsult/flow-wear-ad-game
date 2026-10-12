# Game Design

## Overview

A side-scrolling arcade shooter. The player controls a Flow Wear balloon on the left side of the screen and defends it against dragons. The game ends when a dragon touches the balloon.

## Controls

| Key | Action |
|---|---|
| `W` / `S` | Accelerate up / down |
| `Space` | Fire a cannonball |
| `V` | Restart after game over |

## Sprites

| Sprite | Role |
|---|---|
| Balloon | Player character. Handles movement physics, collision with dragons and restart |
| Dragon1, Dragon2, Dragon3 | Enemies. Spawn at random positions and fly toward the balloon |
| Cannonball | Projectile. Spawned as a clone each time `Space` is pressed |
| Propeller plane | Flies across the sky with the Flow Wear banner |
| Stage | Holds the backdrops and global variables |

## Game flow

1. The player starts the game with the green flag. The plane and dragons start moving.
2. The balloon moves with `W`/`S`. Vertical velocity changes gradually, which gives a floaty feel.
3. Cannonballs travel across the screen. When one touches a dragon, the dragon is hit (`kill1`-`kill3`) and respawns.
4. If a dragon touches the balloon, the game broadcasts `game lost`, switches to the game-over backdrop and sets `gamelost` to `yes`.
5. Pressing `V` resets the game and restarts the dragons.

## Broadcasts

| Message | Purpose |
|---|---|
| `Begin` | Starts the round |
| `dragon begin`, `dragon1`-`dragon3` | Start or respawn individual dragons |
| `kill1`-`kill3` | Sent when a cannonball hits the corresponding dragon |
| `game lost` | Ends the round |
| `message` | Resets the game |

## Global variables

| Variable | Meaning |
|---|---|
| `gamelost` | `yes` / `no`: whether the game is over |
| `Game status` | Current game state |
| `kills` | Counter for dragons hit |
| `Balloon x`, `Balloon y` | Balloon position, shared with other sprites |
| `spawn` | Used when spawning dragons |
| `Dragon1 health` - `Dragon3 health` | Health values for each dragon |

## Ideas for future work

- Show a visible score and high score
- Add Flow Wear product power-ups (for example a "hydration boost")
- Add difficulty levels that speed up the dragons over time
- Add a call-to-action screen with a link to the Flow Wear website after game over
- Add touch controls for mobile players

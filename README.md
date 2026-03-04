# Dungeon Escape

Dungeon Escape is a terminal-based Roguelike adventure game written in C. Navigate through dark labyrinths, collect essential artifacts, manage your resources, and survive encounters with monsters to find the exit. The game features Fog of War mechanics, enemy artificial intelligence, and a progressive level system.

## 🌟 Features

* **Fog of War (Raycasting):** The game uses Bresenham's line algorithm to calculate a dynamic line of sight. You only see objects that have a direct, unobstructed line of sight to the player.
* **Monster AI:** Enemies have three behavior states:
  * *Chase:* If they see the player and the player is not in a safe zone, they approach.
  * *Flee:* If the player enters a safe zone, the monsters move away.
  * *Patrol:* If they cannot see the player, they move randomly.
* **Combat System:** Features a hitscan shooting mechanic. Hitting a monster will "freeze" it for a limited time.
* **Dynamic UI:** The interface includes a minimap and shifts into a red "danger" mode when monsters are nearby and have a line of sight.
* **Interactive Labyrinths:** Unlock doors with keys, gather ammo and weapons, and collect 3 artifacts per level to unlock the exit.

## 🛠️ Requirements

* **OS:** Linux, macOS, or Windows (via WSL/Cygwin).
* **Compiler:** `gcc` or `clang`.
* **Libraries:** `ncurses` (for graphical terminal rendering) and `math`. 

**Debian/Ubuntu Setup:**
```bash
sudo apt-get install libncurses5-dev
```
## 🚀 Installation & Build

1. Clone the repository to your local machine.
2. Compile the game using `gcc` in your terminal:
   ```bash
   gcc game.c -o game -lncurses -lm

3. Run the game:

Bash
`./game`


(Note: Ensure that the map files map1, map2, map3, and map3next are located in the same directory as the compiled executable ).

# 🎮 Controls

Key	Action

`Arrows (↑↓←→)`	-
Move the player / Aim shooting direction 

`Space`	-
Activate shooting mode (press an arrow key right after to fire) 

`E`	-
Interact (open doors, pick up items and artifacts) 

`Q`	-
Quit the game 

# 🗺️ Map Legend (In-Game)
`[] `: Player  (Note: Represented as an animated UI element based on your code)

`MM` : Monster (Red color) 

`#` : Wall 

`.` : Safe Zone (Monsters avoid this area) 

`П` : Door 

`$$` : Artifact (Collect 3 to activate the level exit) 

`!!` : Key 

`Wp` : Weapon (Provides 3 ammo rounds) 

`::` : Ammo (Refills stock to 3) 

`EX` : Level Exit 


# 🏗️ Architecture & Implementation
The game is built using three primary data structures:

Map: A 2D array of tiles and dimensions.

Player: Stores coordinates (x, y), health, inventory (ammo, keys, artifacts), and weapon state.

Monster: Stores coordinates, active state, and a freeze timer.

Rendering relies on ncurses color pairs (init_pair) and text attributes (like A_BOLD, A_DIM). The user interface is automatically centered on the screen using the system variables LINES and COLS.

# 🖌️ Level Design (Custom Maps)
Maps are stored in simple text files, allowing for easy custom level creation. The game reads the layout dynamically based on row width.

# Use the following characters to build your custom maps:

`1 `: Wall 

`2 `: Exit 

`3 `: Door 

`7 `: Safe Zone 

`8 `: Breakable Wall 

`o `: Player Spawn (Starting position) 

`~ `: Monster Spawn 

`$, %, & `: Artifacts (Place at least 3 for a valid level) 

`!` : Key 

`@ `: Weapon 

`p `: Ammo

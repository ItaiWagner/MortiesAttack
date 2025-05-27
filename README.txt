###############################################################################
                               Morties Attack
###############################################################################

A *Rick‑and‑Morty‑meets‑Space‑Invaders* arcade game written in Jack for the
Nand2Tetris tool‑chain. You steer **Rick** from side to side and blast incoming
hordes of **Morties**; survive as long as you can and wipe out every wave!

-------------------------------------------------------------------------------
Table of Contents
-------------------------------------------------------------------------------
1. Quick Start
2. Controls
3. Project Structure
4. How it Works
5. Authors & Licence

===============================================================================
1  Quick Start
===============================================================================
Prerequisites
-------------
* **Nand2Tetris Software** (version 2.7 +) – includes *JackCompiler*, *VMEmulator*,
  *CPUEmulator*.
* Java 8 or newer.

Running the Game
----------------
1. Place **all `.jack` files** in a folder, e.g. `MortiesAttack/`.
2. In that folder run

       JackCompiler .

   → generates the corresponding `.vm` files.
3. Launch **VMEmulator** (`tools/VMEmulator.sh` or `.bat`)  
   ▸ *File → Load Directory* and select `MortiesAttack/`.
4. Press ► *Run* (or >> *Fast Forward* for full speed).

Tip: use *Zoom ×2* if the screen is small.

===============================================================================
2  Controls
===============================================================================
| Action    | Key      |
|-----------|----------|
| Move left | ← / A    |
| Move right| → / D    |
| Shoot     | Spacebar |

(Modify keys in `Rick.jack` constants if desired.)

===============================================================================
3  Project Structure
===============================================================================
| File / Class            | Purpose (key public methods)                     |
|-------------------------|--------------------------------------------------|
| **Main.jack**           | Game bootstrap; `init()`, `runGame()`            |
| **Rick.jack**           | Player avatar; movement & shooting               |
| **Bullet.jack**         | Single projectile; `move()`, `dispose()`         |
| **BulletSet.jack**      | Manages bullets; `addBullet()`, collisions       |
| **Morty.jack**          | Individual enemy; `move()`, `isHit()`            |
| **MortySet.jack**       | Enemy herd manager; spawn & wave logic           |
| **MortiesAttack.jack**  | Wave coordinator; difficulty progression         |

===============================================================================
4  How it Works (High‑Level)
===============================================================================
* **Game Loop** – `Main.runGame()` repeats:
  1. Poll keyboard.
  2. Update Rick, bullets, Morties.
  3. Detect collisions, remove destroyed objects.
  4. Render frame to screen bitmap.

* **Collision Detection** – axis‑aligned bounding‑box tests in
  `BulletSet.checkCollisions()` and `MortySet.checkStatus()`.

* **Difficulty** – each cleared wave calls
  `MortiesAttack.launchAttack()` with higher spawn rate.

===============================================================================
5  Authors & Licence
===============================================================================
Itai Wagner ‹itai.wagner@post.runi.ac.il›  
Yonatan Abramovich ‹yonatan.abramovich@post.runi.ac.il›

Shared for educational purposes under the MIT licence; Rick & Morty characters
are © Adult Swim / Warner Bros. Fan‑made, non‑commercial, provided “as‑is”.

###############################################################################
                         Enjoy saving the multiverse!
###############################################################################

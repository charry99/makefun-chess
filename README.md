[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/charry99/makefun-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/charry99/makefun-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# Tiny Chess: Variant E

This entry builds on the compact chess engine with three evaluation and search improvements.

Search tracks positions seen during the current game.
Repeated positions score as draws, helping the engine avoid cycling.
The repetition table resets when a new game begins.

The evaluation adds 30 points for a bishop pair.
That rewards retaining both bishops when the position supports them.

Passed pawns receive a 25 point bonus for the most advanced passer on each file, per side.
This helps the engine recognize pawns that can advance toward promotion.

The move request includes both the game number and the selected move.
Search uses the measured node cap of 100000.

Practice results were 1362 Elo in trial 0, 1326 in trial 1, and 1290 in trial 2.
The mean was 1326 Elo, compared with 1301 for the previous best build.

Start position perft passed at depths 1 through 3: 20, 400, and 8902.
Kiwipete perft passed at depths 1 and 2: 48 and 2039.
The bestmove check returned b1c3, and the packed source round trip matched byte for byte.

After the initial write, the entry was verified again: the packed source matched,
both perft checks were clean, and the bestmove check passed.
The entry file was deliberately left untouched in this revision to preserve its
size margin under the 4096 byte limit.

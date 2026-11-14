# Tiny Chess Engine

This entry searches legal chess moves with a compact alpha-beta engine.
It includes a position table for repetitions encountered during the game.
Positions seen before are scored as draws during search.
This helps the engine avoid lines that repeat and lose winning chances.
The table resets when a new game begins.

Static evaluation gives a 30 point bonus for owning a pair of bishops.
Two bishops can control both square colours and work well together.
The bonus helps the engine recognize that long term strength.

The search is capped at 100,000 nodes per move.
Practice results were 1253 Elo in trial-0 and 1253 in trial-1.
Trial-2 scored 1396 Elo.
The three trial scores average 1301 Elo.

Perft matched the start position counts 20, 400, and 8902.
Kiwipete matched 48 and 2039 nodes at depths one and two.
The bestmove check returned b1c3 at the node cap.
The packed source round trip was checked for byte identity.

The source has been re-packed with 300-character payload chunks.
Perft and bestmove checks still pass after the re-pack.

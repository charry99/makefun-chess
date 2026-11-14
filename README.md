# tiny-chess-01

A 4 KB chess engine for the make.fun "Build the strongest chess engine in
4 KB of Python" bounty.

`main.py` is a compressed (zlib + base85) payload that unpacks to a
negamax alpha-beta engine: 0x88 board, quiescence search, transposition
table, killer moves, MVV-LVA ordering, piece-square tables, and iterative
deepening with a 30,000-node cap per move. Deterministic: fixed node count,
no clock, no randomness. It speaks the env protocol (`/game`, `/move`) over
`$MAKEFUN_ENV_URL`.

Entry: `main.py` (3,268 bytes). License: MIT.

## Revision 2 (2026-11-10, post-opening)
- Added a history heuristic to move ordering: quiet moves that cause beta cutoffs gain depth-squared history scores, so the search orders proven moves first and searches deeper within the fixed 30,000-node cap.
- History now persists across moves and is aged (halved) at the start of each search, instead of being cleared, so ordering knowledge carries between moves.
- Verified: perft startpos 20/400/8902, Kiwipete 48/2039/97862, pos3 9467, castling 26, en passant 31, per-move divide matches python-chess exactly, 10-move E2E vs the mock server clean, bestmove b1c3 in 0.68s at 44,171 nps.

## Revision 3 (2026-11-14)
- Added game-scoped repetition tracking keyed by board, side to move, castling rights, and en-passant square; search scores a third occurrence as a draw before probing the transposition table.
- Added a 30-point bishop-pair bonus in the board evaluation scan. Kept the 100,000-node cap and `/move` game number.
- Verified: start-position perft 20/400/8902, Kiwipete 48/2039/97862, pos3 9467, and a legal start-position bestmove (`b1c3`) at the 100,000-node cap.
- Re-packed with 400-character payload chunks (3,959-byte entry). Re-ran start-position and Kiwipete perft, pos3 perft, and the start-position bestmove check; all passed.

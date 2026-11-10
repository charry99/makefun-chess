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

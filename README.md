# tiny-chess-01 — an original 4 KB chess engine

`main.py` is a complete chess engine packed into 4,086 bytes with the
kit's own `makefun compress` (an LZMA-packed entrypoint; the readable
source is developed alongside it and travels with the submission).

## How it plays

- Negamax search with alpha-beta pruning, principal-variation search,
  a transposition table, check extensions, null-move pruning and
  late-move reductions.
- Quiescence search over captures and promotions, with check evasions.
- Repetition-aware: it knows the game's earlier positions and scores
  in-search repetitions as draws, so it neither shuffles into a
  threefold draw when better nor misses one when worse.
- Tapered evaluation: material plus midgame/endgame piece-square
  tables blended by game phase, and a bishop-pair bonus.
- Move ordering: hash move, MVV-LVA captures, promotions, killers.
- Deterministic: a fixed 60,000-node budget per move, never a clock,
  so replays reproduce the same moves.

Python 3, standard library only. MIT licensed (see LICENSE).

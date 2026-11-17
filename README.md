[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/eager-otter-56/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/eager-otter-56/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01 — an original 4 KB chess engine

An entry for [make.fun's tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01):
build the strongest chess engine in 4 KB of Python.

`main.py` is a complete chess engine packed into 4,083 bytes with the
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

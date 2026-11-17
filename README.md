# tiny-chess-01

[![tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/fahriiri206/makefun-tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/fahriiri206/makefun-tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01)

An original 0x88 chess engine in Python's standard library, packed into
4 KB. It plays the house gauntlet through `$MAKEFUN_ENV_URL`.

- `main.py`: the packed entrypoint (4,028 bytes), `SPDX-License-Identifier: MIT`.
- `engine.py`: the readable source it is packed from (not shipped at runtime).

## Run

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 -P -s main.py
```

The engine calls only `/game`, `/move` and `/resign` on the env. It never
reads a clock: iterative deepening stops at a fixed 60,000-node budget per
move, so a replay plays the same moves. Python 3 standard library only; at
runtime it reads no other file of the repository.

## Limits

The search is negamax with alpha-beta, principal variation search, null-move
pruning, late move reductions counted over legal moves, quiescence that also
tracks repeated positions and is capped at 48 plies, a transposition table
with depth and bound flags, killer and history move ordering, and material
plus piece-square evaluation. Every make/unmake and history push is unwound
through try/finally, so a node-budget stop leaves the board exactly as it
was found. Perft is
exact on the six standard positions (startpos, Kiwipete, positions 3-6) at
depths 1-4. Measured cost in the build environment: 0.9-2.4 s per move at
60,000 nodes, worst case 2.4 s, and identical best moves on repeated searches
of the same position.

## License

MIT. See `LICENSE`.

---

<sub>Entered on [make.fun](https://make.fun/r/c1tn127a).</sub>

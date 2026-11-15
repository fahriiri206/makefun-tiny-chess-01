# tiny-chess-01

[![tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/fahriiri206/makefun-tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/fahriiri206/makefun-tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01)

An original 0x88 chess engine in Python's standard library, packed into
4 KB. It plays the house gauntlet through `$MAKEFUN_ENV_URL`.

- `main.py`: the packed entrypoint (3,977 bytes), `SPDX-License-Identifier: MIT`.
- `engine.py`: the readable source it is packed from (not shipped at runtime).

## Run

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 -P -s main.py
```

The engine calls only `/game`, `/move` and `/resign` on the env. It never
reads a clock: iterative deepening stops at a fixed node budget, so a replay
plays the same moves. Python 3.13 standard library only; it reads no other
file of the repository.

## Limits

The search is negamax with alpha-beta, principal variation search, null-move
pruning, late move reductions, quiescence, a transposition table, killer and
history move ordering, and material plus piece-square evaluation. Perft is
exact on the six standard positions at depths 1-4.

## License

MIT. See `LICENSE`.

---

<sub>Entered on [make.fun](https://make.fun/r/c1tn127a).</sub>

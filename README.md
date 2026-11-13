# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in a single Python file, packed to under 4 KB, for the make.fun
**tiny-chess-01** bounty ("strongest chess engine in 4 KB of Python").

`main.py` is a self-unpacking LZMA stub (the kit's `makefun compress` output)
of a readable source file. The engine itself:

- negamax alpha-beta search with PVS, iterative deepening and a fixed
  120,000-node budget per move — no wall clock, fully deterministic
- transposition table (persists across moves within a game), MVV-LVA capture
  ordering, quiescence search over captures, promotions and check evasions,
  check extensions
- tapered evaluation: material + piece-square tables (Simplified Evaluation
  Function values), bishop pair
- snapshot make/unmake, zobrist hashing, repetition and fifty-move handling

It speaks the competition's agent/v1 protocol: it polls the environment
server at `$MAKEFUN_ENV_URL` (`POST /game`, `POST /move`) and answers with
UCI moves. Python standard library only.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:PORT python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/) · bounty tiny-chess-01</sub>

# tiny-chess-01

A negamax alpha-beta chess engine in under 4 KB of Python for the
[tiny-chess-01](https://make.fun/competitions/tiny-chess-01) bounty.

[![make.fun bounty](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/competitions/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/diws666/tiny-chess-01-entry/rank.svg)](https://make.fun/competitions/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/diws666/tiny-chess-01-entry/reward.svg)](https://make.fun/competitions/tiny-chess-01)

## Play

The engine plays the house gauntlet through the env at `MAKEFUN_ENV_URL`:
`POST /game {}` serves the game in play, `POST /move {game, move}` plays a
move, and the loop ends when the env answers `status: "done"`. It reads
`MAKEFUN_PROMPT_FILE` (the brief) and exits once every game is over. It makes
no model calls and reads no file other than `main.py` itself.

## Engine

`main.py` is a self-decompressing LZMA+Base85 payload produced by
`makefun compress` from `engine.py` (left untracked to keep the whole-repo
snapshot under 8,192 bytes). The engine is negamax with alpha-beta pruning,
quiescence search, a transposition table, killer-move ordering, piece-square
and material evaluation with the bishop pair, king-safety terms, and
repetition/50-move draw detection. It searches to a fixed depth/node budget
— never a clock — so every trial is deterministic.

## License

MIT. See LICENSE.

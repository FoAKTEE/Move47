# ref-code provenance

Both versions were handed over by the user in this workspace on 2026-10-05 (no upstream URL or
commit is known). The copies lost their executable bits. They are local mirrors and are not
tracked; this file records what they were.

| version | files | size | manifest digest |
|---|---|---|---|
| `v0.01/` (go-bench without gotree, plus a prebuilt CPU KataGo and two small nets) | 45 | 25 MB | `02e9dcb0089a8ed6094f02093d0a60fd9e6dc15230a60c210c5528db057e005f` |
| `v0.02/` (go-bench with gotree; top-level `PROMPT.md`, `TREE.md`) | 71 | 1.2 MB | `a809c08395429235cf78dae7a68e37abc55d9ca3caf83f07c1cc0bea47b20f9f` |

Manifest digest = `find . -type f ! -path '*__pycache__*' -print0 | sort -z | xargs -0 sha256sum | sha256sum`,
run inside the version directory.

v0.01 engine files (unused; the mission downloads KataGo v1.18.2 CUDA instead, see
`Chandra/move47/scripts/fetch_katago.sh`):

```
e2fd6805588c6f71353650b724527846a881046854cfdc17d861fb8e2c4397b9  engines/katago
f5d32604e3675c480c7c8f6aa579a1ea857135628a0afccc8fa56330fbacd38d  engines/models/g170-b6c96-s175395328-d26788732.bin.gz
1a8e05a4ea3fca20dab79410cbb566c760767fcdd2fa0b701cfe259a84cc8b04  engines/models/g170e-b10c128-s1141046784-d204142634.bin.gz
```

The two nets are byte-identical to the copies in the KataGo repository's `cpp/tests/models/`.

Use in the mission: v0.02 is mirrored verbatim at `Chandra/ref-code/go-bench-v0.02/` (gitignored,
with its own PROVENANCE.md) and imported as the working copy `Chandra/move47/` in Chandra commit
cc6d22e, whose `move47/PROVENANCE.md` holds the per-file sha256 manifest and the deviations.

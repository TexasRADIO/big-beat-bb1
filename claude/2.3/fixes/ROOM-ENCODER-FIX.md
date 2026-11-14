# ROOM block-float encoder fix

**14 November 2026 · Claude (review)**

## Bug

`rm_encode` in `bb_fxbus.c` derived the block exponent `e` from `127.0f / peak`, then computed `fwd = 127.0f / 2^e` — applying the 127 scaling twice. Every stored mantissa clipped to ±127, and `rm_decode` read back a signal about 40 dB down from the correct level with square-edged distortion.

Found during Compás 1.2 listening renders. Fixed there as commit `f3e4ec0` on `claude/compas-1.2`. The same `rm_encode`/`rm_decode` pair shipped in BB1 2.3 (`FM-1_92200203`).

## Fix

1. Derive `e` directly from the peak's IEEE 754 exponent: `e = exponent_bits - 126` so that `peak < 2^e`.
2. Compute `fwd = 127.0f * 2^(-e)` using a new `fx_pow2(int e)` helper that builds the float from the bit pattern.
3. Simplify `rm_decode` to `scale = 2^e * (1/127)` using the same helper.

This is identical to the Compás fix. No other files change.

## Impact

ROOM reverb at any setting now returns at the correct level. RT60 at ROOM 100 is ~311 ms (was a 55 ms burst). The reverb tail decays naturally instead of cutting off.

## Rebuild required

The fix changes one compile unit (`bb_fxbus.c`). Codex rebuilds with `build23.py`, repackages as `.fwsc`, and installs on the FM-1 when approved.

# Changelog

## 2.3 — November 2026

### Effects chain

The echo and spring are replaced by a full effects chain built on the OG Synth X0X fxbus.

**Delay.** Two modes — DIGI (clean digital) and TAPE (analog degradation with wow, flutter and saturation). Tempo-synced divisions from 1/32 to 1/2 dotted. Three read heads at 1/3, 2/3 and full delay with per-head stereo pan. Motion system drifts head positions and pan over 20–60 seconds for echoes that never quite repeat. TAPE mode supports self-oscillation at high feedback. Idle detection skips processing when the line is silent.

**Reverb.** Four-line Hadamard FDN with two allpass diffusers, replacing the 10-stage allpass spring. Per-line one-pole damping, block-float storage and automatic idle detection when the tail has decayed.

**Distortion.** Seven types on a DRIVE knob: Diode (warm symmetric tanh), Clip (asymmetric, gritty), SAT (even-harmonic tube character), BFZ (fuzz with wet/dry), PDIST (polynomial cubic), Fold (three-stage wavefolder) and Crush (bitcrush with decimation).

**Compressor.** One-knob glue compressor with soft knee, 2:1–5:1 ratio, auto makeup gain. Reads the louder channel and applies gain to both so the stereo image holds. Hard bypass at knob zero.

**Volume.** Dedicated master volume after the compressor, fused into a single processing pass.

### Per-song FX recall

Effect settings are saved with each song. Turning ALGO to a new song recalls its effects alongside the pattern. The FX anchor mechanism captures and restores the full effects state.

### Kick-aware Dillo bass

A new generator mode reads the drum pattern's kick positions and writes a bass line that responds to them. Four styles at the density knob. Requires a drum pattern loaded in layer A.

### Retrospective capture

The retro take buffer records continuously. When you like what just happened, the capture is already there.

### Sideman USB TX

BB1 sends a 19-byte summary of its musical state over USB-MIDI SysEx at 10 Hz. A browser page decodes this and shows a live performance guide — what's playing, which voices, transport state.

### Screen companion

The FM-1's display is mirrored live to a browser page over USB-MIDI SysEx. An 88-byte binary snapshot of the UI state is sent at 10 Hz, decoded in JavaScript and rendered on a Canvas matching the firmware's layout and colours. Open `bb1-screen.html` in Chrome with the FM-1 plugged in. Scales to 1×, 2× or 3×. Falls back to a demo mode when disconnected.

### Under the hood

- Reverb idle detection skips processing when the FDN has decayed to silence
- Unrolled four-lane Hadamard with fused scaling replaces the generic loop
- Merged left/right tap accumulation into the lane filter loop (one pass, not two)
- Fused compressor and volume into a single output pass
- Help text is written to flash at install time; the firmware reads it from flash via XIP with a silent fallback when the text block is absent
- UC25HQ80 flash chip support (alongside the original Puya P25Q80)
- 574,100 bytes firmware, 7,464 bytes free

[Back to BB1](../README.md)

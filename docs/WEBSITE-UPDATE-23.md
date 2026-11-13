# BB1 2.3 — Website update for Codex

**What this covers:** Changes needed at thebigbeat.app for the BB1 2.3 release.

## 1. FM-1 product page

Update the feature summary to reflect the new effects chain:

**Old:** "Echo and spring" / "shared effects with instrument sends"
**New:** "Full effects chain — delay (DIGI/TAPE), room reverb, seven distortions, glue compressor"

Add to the feature list:
- Per-song FX recall (effects settings saved and loaded with each song)
- Kick-aware Dillo bass (bass lines that respond to the kick pattern)
- Retrospective capture (always-on recording buffer)
- Screen companion (browser display mirror over USB-MIDI)
- Sideman USB TX (live performance guide over USB-MIDI)

## 2. Screen companion page

Host `bb1-screen.html` at a public URL (suggested: `thebigbeat.app/fm1/screen/` or alongside the emulator). The file is self-contained — single HTML, no dependencies, no build step. It needs WebMIDI with SysEx, so Chrome or Edge only.

The file is on Orange Base at:
- `/Volumes/Orange Base/FM1 Recovery Vault/bb1-screen.html`
- Also on Desktop

## 3. Download / installer

The 2.3 firmware package is:
- `/Volumes/Orange Base/FM1 Recovery Vault/bb1-23-screen.fwsc`

This is the final build: all features, Screen companion cast, soak-tested. 574,100 bytes, 7,464 free.

## 4. What's New section

Use `docs/CHANGELOG.md` from this repo as the source. Key points for the public page:

- Effects chain overhaul: delay with DIGI/TAPE modes, room reverb, seven distortions, glue compressor
- Per-song FX recall
- Kick-aware Dillo bass response
- Screen companion: mirror the FM-1's display live in a browser
- Sideman: live performance guide over USB
- Retrospective capture
- UC25HQ80 flash support

## 5. Emulator

The browser emulator needs an Emscripten rebuild to include the 2.3 changes. Emscripten is currently missing from the Mac toolchain (`emsdk-6.0.13/upstream/bin/clang`). This can be restored separately — the emulator update is not a blocker for the firmware release and website copy.

## 6. No changes needed

- BPM calculator (BB-23) — unchanged
- Studio — unchanged
- Install process — same .fwsc format, same Felucca OTA path

[Back to BB1](../README.md)

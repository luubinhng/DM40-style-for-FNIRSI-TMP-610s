# Artifact Verification

Checks performed while organizing the supplied repository. No firmware was flashed and no hardware behavior was tested.

## Firmware Identity

| Artifact | Recorded SHA-256 |
| --- | --- |
| Distributed `binary/APP_TMP-610S_V1.9.9_260716_dm40.bin` | `353418061f34ead74cc3593816be78f0f05e3571dae84a8289c722b369647f66` |
| `PATCH_MANIFEST.json` output | `040d2d4172ce2f4f99d18734a633bae9a690fb09685d1db0f17dc70c5070dbf6` |
| `PREVIEW_MANIFEST.json` candidate | `1164fadb16ded5286e655ac5406ad144cd23dd65c09e0b81f97d2d9ff7d192bc` |
| Base recorded by both manifests | `cd6a3520d5914e463467675dec580ab1fe7f46fbaa66992fc2f02fb92e51422e` |

The distributed binary contains **946,176 bytes**. Its hash was checked before and after moving it to `binary/`; its bytes were preserved.

The output and candidate hashes also differ from each other. Neither manifest identifies the distributed binary. This does not itself establish a defective binary, but prevents treating these manifests as validation of it. No hashes in the original manifests were rewritten to conceal the mismatch.

## Images

All **13** PNG files named in `PREVIEW_MANIFEST.json` match their recorded SHA-256 hashes. This establishes image-file integrity relative to that manifest only.

Three additional PNGs are not listed in its `image_sha256` mapping: `MINMAX_BEFORE_AFTER.png`, `FONT_SAMPLES_BEFORE_AFTER.png`, and `GLYPHS_AFTER_h122.png`. Their relationship to the distributed binary is not established.

The previews reconstruct selected UI layers. Graph inputs and long reading examples are synthetic. LCD behavior, full-screen appearance, measurement accuracy, bootloader acceptance, and successful hardware operation are not established by these files.

## Reproducibility

The manifest's paths name original development inputs and outputs that are absent here. The original preview-generation instructions refer to tools that are also absent. This package is a binary distribution, not a reproducible build environment.

To establish an exact gallery for this release, regenerate the previews from the distributed binary and record its hash, or supply device photos with the tested binary hash. Device testing should record the model, hardware revision, previous firmware, installation result, and observed behavior.

# UI Reference Gallery

[Project overview](../README.md) | [Artifact verification](../docs/VERIFICATION.md)

These supplied previews are development references. The distributed binary does **not** match the firmware hashes in either manifest. All 13 PNG hashes recorded in `PREVIEW_MANIFEST.json` were verified; the extra `MINMAX_BEFORE_AFTER.png`, `FONT_SAMPLES_BEFORE_AFTER.png`, and `GLYPHS_AFTER_h122.png` are outside that hash list.

The original notes below are retained for provenance. Their regeneration command refers to development tools **not included in this repository**. The "before" base is a development image, not a verified stock-firmware baseline.

---

# Actual-byte reconstruction previews

These are partial UI layers, not device screenshots or a complete TMP framebuffer capture. Run `python3 dm40-refined/make_previews.py` after building `candidate.pending` to regenerate them. The script imports the independent bitmap/layout validator, so it refuses images whose hashes or layout checks fail.

Every product glyph mask is decoded from the exact named base or refined image, using that image's font entry width/height/advance/x/y fields. No host typeface replaces product glyphs. Reviewer captions outside the reconstructed areas use Pillow's default font. Coverage is composited through source-style RGB565 channel interpolation; this is not a verified emulation of TMP's LCD blending ramp or physical panel.

- `HOME_LABELS_BEFORE_AFTER.png`: all8 original Chinese/English home strings, original draw rectangle, oldh40/newh21 selector, actual300x76 descriptor clip. Thin frame is a review annotation, not firmware decoration.
- `METER_READINGS_BEFORE_AFTER.png`: known main/unit layers only, normal-color path; negatives, decimal, narrow/wide digits, long14-character stress, OL/PASS/FAIL. Long cases are synthetic width stress and are not asserted reachable measurement values. Unit placement and actual runtime compact-font selection are reflected.
- `SEMANTIC_GLYPHS_BEFORE_AFTER.png`: independent red exceptional branch plus actual selected `H` and `REL` glyphs. The H box illustrates established extent/colors; the rounded-rectangle helper's exact edge rasterization is not emulated. No invented full-word HOLD label is added.
- `GRAPH_LAYER_BEFORE_AFTER.png`: actual grid/trace color arguments and geometry, clipped to the known graph layer. The ordinate sequence is explicitly synthetic normalized graph input, not an electrical measurement. Original black graph fill is retained.
- `GLYPH_*.png`: actual bitmap/metric samples for large/aux digits, decimal/minus, mixed lowercase and narrow menu glyphs. Both samples use a common review foreground to isolate glyph changes.
- `UNITS_BEFORE_AFTER.png`: all16 tested range/compound units and symbols; common review foreground.
- `SOURCE_F78_VS_REFINED.png`: genuinely decoded DM40 reference F78 masks alongside the actual adapted TMP bank; this shows the uniform face transform, not a host-font substitute.

`PREVIEW_MANIFEST.json` binds source/candidate hashes, each PNG hash, rectangles, sample advances, visible ink counts and limitations. Undrawn layers, acquisition/calibration, hold state transitions, LCD timing, hardware appearance and updater acceptance are not inferred from these previews.

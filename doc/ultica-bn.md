# Bright Nights bindings

The `ultica-bn` branch keeps the approved Bright Nights binding changes in the
normal compositing source format. Build either pack with the repository's composer:

```sh
python tools/compose.py --use-all gfx/UltimateCataclysm build/UltimateCataclysm
python tools/compose.py --use-all gfx/Chibi_Ultica build/Chibi_Ultica
```

Copy `tileset.txt`, `fallback.png`, and `layering.json` from the respective source
pack alongside the generated files. The branch's **Bright Nights UltiCa builds**
workflow performs these steps and publishes both packs as artifacts. It also
publishes versioned prereleases named `ultica-bn-<commit-prefix>` containing
`UltimateCataclysm.zip`, `ChibiUltica.zip`, and `SHA256SUMS`. These archives retain
the directory names expected by the BN packaging workflow. Existing release
assets are not replaced when a workflow is rerun.

BN entries are in each pack's `pngs_bn_bindings_32x32/bindings` directory. They use
sprite names rather than compiled atlas indices. Identical Chibi binding files use
relative links to the UltiCa entries, following the repository's existing sharing
convention. Pack-specific artwork and states keep separate sources. Existing source artwork remains
shared; the earlier source sheets act as fillers behind the BN bindings. This
uses the composer's existing precedence rules and leaves other tilesets' sources
and shared donor files intact. `preserved_source_aliases` explicitly retains the
original automatic aliases whose precedence would otherwise change when moving
those sheets behind the BN entries. Different case-sensitive IDs have distinct source
filenames even on case-insensitive filesystems.

The changes include wall and furniture connections, cabinet orientations, overmap
levels and road connections, vehicle families and their open/broken states, and
previously approved item, clothing and creature aliases. Rotations, weighted
variants, canvas offsets and related entries are retained. Generic black-building
bindings that were deliberately withdrawn stay unbound; unrelated upstream-only
IDs remain available. The old generic-building alias file is excluded only in
these two packs through their sheet metadata; shared donor files are not edited.

Separate PNG sources retain the exact approved pixels for modified vehicle faces,
hatch and door assemblies, roof devices and tint masks. Existing UltiCa and Chibi
artwork retains its upstream authorship and licensing. Masks and opaque exterior
faces are mechanical derivatives of those sprites; no AI-generated replacements
are introduced by this transfer. The approved public-works and parking artwork
already present in the BN package is also retained.

The composer preserves extra `tile_info` metadata and resolves named `fg`/`bg`
mask references, including masks in additional states. Game source code is not
included. Contextual vehicle shapes and layered display still require a Bright
Nights executable with support for those optional metadata fields.

Files under the local art workbench's `!!ultica/!final` directory are outside this
transfer. It neither installs a game nor changes saves or gameplay definitions.

# UltiCa for Bright Nights

The `ultica-bn` branch adapts UltiCa and ChibiUltica to Bright Nights. It fixes
wall and furniture connections, cabinet orientations, overmap and road tiles,
and vehicle graphics, including rotations and open/broken states.

## Building

Build either pack with the repository's composer:

```sh
python tools/compose.py --use-all gfx/UltimateCataclysm build/UltimateCataclysm
python tools/compose.py --use-all gfx/Chibi_Ultica build/Chibi_Ultica
```

Copy `tileset.txt`, `fallback.png`, and `layering.json` from each source pack
into its build directory.

The **Bright Nights UltiCa builds** workflow builds both packs and publishes
versioned releases with `UltimateCataclysm.zip`, `ChibiUltica.zip`, and
`SHA256SUMS`.

## Editing bindings

BN bindings use sprite names and live in `pngs_bn_bindings*/bindings`.
The directories are grouped by display offset: keep each definition in the
sheet with its required offset, even when it references a PNG from another
sheet. Shared Chibi bindings link to the corresponding UltiCa files.

The composer preserves BN metadata and named tint masks. Contextual vehicle
graphics require the matching renderer support in Bright Nights.

## Upstream updates

**Weekly BN upstream sync** runs every Monday at 07:17 UTC (10:17 Moscow time).
It updates `master` from upstream, prepares a merge into `ultica-bn`, and runs
the existing tests and builds for both packs. Only the checked merge is promoted.
Conflicts and failed checks leave a PR open with a link to the logs.

The workflow can also be run manually from Actions. After a successful update,
the normal release build runs to publish new archives.

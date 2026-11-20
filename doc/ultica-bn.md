# UltiCa for Bright Nights

The `ultica-bn` branch adapts UltiCa, ChibiUltica and AltiCa to Bright Nights. It fixes
wall and furniture connections, cabinet orientations, overmap and road tiles,
and vehicle graphics, including rotations and open/broken states.

## Building

Build any pack with the repository's composer:

```sh
python tools/compose.py --use-all gfx/UltimateCataclysm build/UltimateCataclysm
python tools/compose.py --use-all gfx/Chibi_Ultica build/Chibi_Ultica
python tools/compose.py --use-all gfx/Altica build/Altica
```

Copy `tileset.txt`, `fallback.png`, and `layering.json` from each source pack
into its build directory.

The **Bright Nights UltiCa builds** workflow checks and builds all three packs on
source changes. Pushes do not publish releases. To publish a batch, open the workflow
in Actions, choose **Run workflow** on `ultica-bn`, and enable **Publish the checked
batch as a release**. This can be done every few days or weekly, when a batch is ready.
A release contains `UltimateCataclysm.zip`, `ChibiUltica.zip`, `Altica.zip`, and
`SHA256SUMS`.

## Editing bindings

BN bindings use sprite names and live in `pngs_bn_bindings*/bindings`.
The directories are grouped by display offset: keep each definition in the
sheet with its required offset, even when it references a PNG from another
sheet. Shared Chibi bindings link to the corresponding UltiCa files.
AltiCa shares the BN sheets and keeps its own character and clothing artwork.

The composer preserves BN metadata and named tint masks. Contextual vehicle
graphics require the matching renderer support in Bright Nights.

## Upstream updates

**Weekly BN upstream sync** runs every Monday at 07:17 UTC (10:17 Moscow time).
It updates `master` from upstream, prepares a merge into `ultica-bn`, and runs
the existing tests and builds for all three packs. Only the checked merge is promoted.
Conflicts and failed checks leave a PR open with a link to the logs.
If GitHub rejects a push, for example when upstream changes workflow files,
the update is left for manual review in a PR.

The workflow can also be run manually from Actions. Successful updates run the normal checks and builds; publishing remains manual.

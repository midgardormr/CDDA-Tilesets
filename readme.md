# UltiCa for Bright Nights

This fork adapts UltiCa and ChibiUltica to [Cataclysm: Bright Nights](https://github.com/cataclysmbn/Cataclysm-BN). It is based on [I-am-Erk/CDDA-Tilesets](https://github.com/I-am-Erk/CDDA-Tilesets).

BN and CDDA have diverged, and some objects in BN end up with missing or mismatched sprites. This branch fixes those gaps:

- Walls, furniture connections and cabinet orientations.
- Overmap buildings, terrain, roads and map levels.
- Vehicle bodies, doors, wheels and small vehicles, with their rotations and open/broken states.
- Missing item, clothing and creature bindings.

Vehicle graphics use the parts actually installed on the vehicle, so the same rules work for player-built vehicles. These features need the corresponding BN renderer support.

I also plan to add artwork specifically for BN and address things players find hard to read in UltiCa, such as very small item sprites.

## Downloads and building

Get both packs from [this fork's releases](https://github.com/midgardormr/CDDA-Tilesets/releases). Build instructions and notes on editing bindings are in [doc/ultica-bn.md](doc/ultica-bn.md).

## License

Most artwork is licensed under [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/). See the individual tilesets for credits and other license notices.

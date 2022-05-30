# Game File

Files must be between 12811 and 3248327 bytes.

### Format

| Name | Description | Length | Full file only |
|-----|-----|----|:----:|
| File format ID| Identifies this file as a Maikor game file|2| |
| File format version|Version of game file format|1| |
| Min Maikor Version|Minimum supported Maikor version for game|2| |
| Target Maikor Version|Version of Maikor game was compiled for|2| |
|Build|Build number of the game, must be at least 1|4| |
|ID Length|Length in bytes of game ID|1| |
|ID|Game ID text|1 - 255| |
|Name Length|Length in bytes of game name|1| |
|Name|Game name text|1 - 255| |
|Version Length|Length in bytes of game version|1| |
|Version|Game version text|1 - 255| |
|Author Length|Length in bytes of game author|1| |
|Author|Game author text|1 - 255| |
|Code Bank count|Number of code banks, not including main code|1| |
|RAM Bank count|Number of required RAM banks|1| |
|Atlas Bank count|Number of atlas banks|1| |
|Controller graphics bank count|Number of controller graphics banks|1| |
|Main code|Main code data|8700| ✓ |
|Code banks|Up to 255 code banks|0 - 2218500| ✓ |
|Atlas banks|Between 1 and 255 atlas banks|4000 - 1020000| ✓ |
|Controller graphics banks|9 controller graphics banks|88| ✓ |
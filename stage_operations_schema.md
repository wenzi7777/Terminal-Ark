# Stage Operations Schema

Terminal Ark structured TD stage format. Runtime reads `public.stage_operations`; `designFiles/configs/stage_operations.json` is only the manually maintained local copy.

Replaces legacy `stage_maps` (ASCII grid + runtime BFS). Naming is project-original.

## Local source and runtime identity

Local JSON uses an object map: `operationId` → `StageOperation`. The remote table stores one row per `operation_id`; it must be updated only through confirmed, one-time SQL under `designFiles/sql/manual/`.

## StageOperation

| Field | Type | Notes |
|---|---|---|
| `operationId` | string | Same as object key |
| `map` | StageMapGrid | Play grid |
| `routes` | StageRoute[] | Named full paths |
| `waves` | StageWave[] | Spawns must reference `routeId` |
| `rules` | StageRules | Bandwidth, core HP, deploy limit, time |
| `areaSpotId` | string? | City area e.g. `1-1` |
| `roomTypes` | string[]? | `battle` / `elite` / `boss` |
| `displayNameKey` | string? | i18n |
| `ecology` | object? | Faction bonuses |
| `controller` | object? | Hack-controller meta |
| `resourcePackId` | string? | Visual pack; default tech |
| `visualLayers` | (string\|null)[][][]? | Optional voxel override |

## StageMapGrid

- `width`, `height` (integers, recommended 6–40)
- `cells[y][x]`: `{ cellKey: string, special?, params? }`

### cellKey catalog (v1)

| cellKey | passable | deploy | render |
|---|---|---|---|
| `void` | none | none | no mesh |
| `block` | none | none | wall column |
| `floor` | ground | ground | floor |
| `floor_nodeploy` | ground | none | floor |
| `platform` | none | elevated | elevated |
| `entry` | ground | none | floor + entry marker |
| `core` | ground | none | floor + core marker |
| `hazard` | ground | ground | special floor |
| `repair` | ground | ground | special floor |

## StageRoute

| Field | Type |
|---|---|
| `routeId` | string |
| `start` | `{ x, y }` |
| `end` | `{ x, y }` |
| `path` | `{ x, y }[]` full tile sequence including start and end |
| `waitTicksAt` | optional map `"x,y"` → ticks |

Runtime follows `path` only — no pathfinding.

## StageWave / StageWaveSpawn

```json
{
  "startTick": 0,
  "spawns": [
    {
      "enemyId": "wasteland_scrap_hauler",
      "count": 3,
      "intervalTicks": 45,
      "delayTicks": 0,
      "routeId": "lane_main"
    }
  ]
}
```

`routeId` is required.

## Validation (must pass to start)

1. Rectangular cells matching width/height  
2. At least one `entry` and one `core`  
3. Every route: in-bounds path, adjacent steps (4-dir), start/end match fields, tiles passable for ground  
4. Every wave spawn has resolvable `routeId`  
5. Path start should be an `entry` cell; path end a `core` cell  

## Legacy

`stage_maps` (ASCII grid + BFS) is **retired**. Runtime reads **only** `stage_operations`.
Archived snapshot: `designFiles/archive/stage_maps_legacy/stage_maps.json` (rollback only).

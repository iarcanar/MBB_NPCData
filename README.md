# MBB_NPCData

Curated FFXIV character, NPC, and lore database for the **MBB Dalamud** translation overlay.

This repo is consumed automatically by MBB clients via the **Cloud Sync** button in NPC Manager — they fetch `manifest.json` to detect new releases, then download `data/npc.json` to merge into their local database.

## Repo layout

```
manifest.json              ← always-current pointer (sha256 + version + URL)
data/
├── npc.json               ← latest curated database
└── archive/
    └── npc-YYYY.MM.DD.json  ← per-release snapshots (rollback target)
```

## Schema

`manifest.json`:
```json
{
  "schema_version": 1,
  "data_version": "2026.05.15",
  "released_at": "2026-05-15T00:00:00Z",
  "data_url": "https://raw.githubusercontent.com/iarcanar/MBB_NPCData/main/data/npc.json",
  "data_sha256": "sha256 hex of data/npc.json",
  "data_size_bytes": 12345,
  "stats": {"main": 223, "npcs": 65, "lore": 140, "character_roles": 206},
  "min_mbb_version": "1.8.8",
  "release_notes_th": "..."
}
```

## Phase

Currently **Phase A** of the cloud-sync roadmap: public + plaintext, no encryption. Future phases (B: encryption, C: tier gate) tracked in MBB project memory.

## Updates

Releases are published by the maintainer via `scripts/build_npc_release.py` in the [MBB_Dalamud](https://github.com/iarcanar/MBB_Dalamud) repo. Cadence is roughly weekly during active curation.

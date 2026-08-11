# KroModIx.PluginIndex

Offizieller Katalog aller Plugins für den
[KroModIx](https://github.com/KroModIx/KroModIx).

Der Host lädt `plugins.json` beim App-Start (Cache 24 h, Stale-Fallback
bei Netzfehler) und zeigt in der Sidebar bei jedem installierten Steam-
Spiel einen **umrandeten goldenen Stern**, wenn hier ein passendes Plugin
verfügbar ist. Klick → Install-Karte im Content-Bereich → 1-Klick-Install
+ Live-Aktivierung ohne App-Neustart.

## Aktuelle Einträge

| id | Spiel | Steam AppId | Repo |
|---|---|---|---|
| `kroste.ls25` | Landwirtschafts-Simulator 25 | 2300320 | [KroModIx.Plugin.LS25](https://github.com/KroModIx/KroModIx.Plugin.LS25) |
| `kroste.icarus` | Icarus | 1149460 | [KroModIx.Plugin.Icarus](https://github.com/KroModIx/KroModIx.Plugin.Icarus) |
| `kroste.satisfactory` | Satisfactory | 526870 | [KroModIx.Plugin.Satisfactory](https://github.com/KroModIx/KroModIx.Plugin.Satisfactory) |
| `kroste.dummy` | Demo (CS2, TF2, Proton) | 730, 440, 1493710 | [KroModIx.Plugin.Dummy](https://github.com/KroModIx/KroModIx.Plugin.Dummy) |

## Ein Plugin registrieren

Pull-Request mit einem zusätzlichen Eintrag in `plugins.json`:

```jsonc
{
  "id": "kroste.<slug>",              // stabile ID, deckt sich mit plugin.json des Plugin-Repos
  "displayName": "Menschenlesbarer Name",
  "author": "Kroste",
  "description": "Ein bis zwei Sätze zum Plugin.",
  "steamAppIds": [1234567],           // Steam-AppIds die das Plugin bedient
  "updateSource": {
    "kind": "github",
    "repo": "KroModIx/KroModIx.Plugin.<Name>"
  },
  "iconUrl": null                     // optional; PNG-URL für das Plugin-Logo
}
```

Der Host prüft im referenzierten Repo (`Owner/Repo`) den letzten Release
und lädt die aktuellste `*.zip` beim Nutzer-Klick.

**Pflichten für das verlinkte Plugin-Repo:**
- GitHub-Release mit Tag `vX.Y.Z` und Bundle-ZIP-Asset
- Das ZIP enthält `plugin.json` + Plugin-DLL + transitive Deps
- `plugin.json.id` muss mit `id` im Index übereinstimmen

Details für Plugin-Autoren im [KroModIx-Plugin-Skill](https://github.com/KroModIx/KroModIx-Plugin).

## Format

Schema-Version 1. Root-Objekt:

```json
{
  "schema": 1,
  "plugins": [ /* Array */ ]
}
```

## Lizenz

MIT — kein Anspruch aufs Aufnehmen von Third-Party-Plugins, aber gerne PR.

# ModManager.PluginIndex

Offizieller Katalog aller Kroste-Game-Plugins für den [Kroste ModManager](https://github.com/Kroste/Mod-Manager).

Der Host liest `plugins.json` beim App-Start (Cache 24 h) und zeigt in der
Sidebar bei installierten Steam-Spielen einen umrandeten goldenen Stern,
wenn hier ein Plugin verfügbar ist. Klick → Install-Karte im Content-Bereich → 1-Klick-Install.

## Ein Plugin registrieren

Pull-Request mit einem zusätzlichen Eintrag in `plugins.json`:

```jsonc
{
  "id": "kroste.<slug>",              // stabile ID, deckt sich mit plugin.json des Plugin-Repos
  "displayName": "Menschenlesbarer Name",
  "author": "Kroste",
  "description": "Ein Satz.",
  "steamAppIds": [1234567],           // Steam-App-IDs die das Plugin bedient
  "updateSource": { "kind": "github", "repo": "Kroste/ModManager.Plugins.<Name>" },
  "iconUrl": null                     // optional; PNG-URL für das Plugin-Logo
}
```

Der Host prüft dann bei Verfügbarkeit des Update-Assets im referenzierten
Release-Repo (`Owner/Repo`) und lädt die aktuellste `*.zip` beim Nutzer-Klick.

## Lizenz

MIT — kein Anspruch aufs Aufnehmen von Third-Party-Plugins, aber gerne PR.

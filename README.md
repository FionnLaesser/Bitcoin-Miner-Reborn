# Bitcoin Miner: REBORN

**Eigenständiger Roblox-Mining-Simulator** mit sichtbarem Farm-Ausbau, Strom-/Kühlungsoptimierung und kurzen Mining-Aufträgen. **Der Name ist ein vorläufiger Arbeitstitel**, keine offizielle Fortsetzung eines anderen Spiels.

> **Entwicklungsstand:** Konzept-/Dokumentationsphase für **Beta 0.1**. Die nachfolgend beschriebenen Spielfunktionen sind geplant, **nicht als implementiert oder getestet bestätigt**. Eine öffentliche Veröffentlichung ist nicht freigegeben.

## Spielidee

Baue deine eigene GPU-Farm in einem kleinen Mining-District mit bis zu sechs Spielern auf. Eine kostenlose Starter-GPU beginnt automatisch mit der Produktion. Du tauschst **rein virtuelle BTC** gegen **Credits (C)**, kaufst neue GPUs und Racks und optimierst die Strom- und Kühlkapazität deiner Farm.

**Der Kernloop:** GPU installieren → virtuelle BTC minen → BTC zu Credits tauschen → Hardware/Versorgung verbessern → sichtbaren Fortschritt erzielen.

Das Spiel soll mehr bieten als eine reine AFK-Zahlensteigerung: Du erkennst Effizienzengpässe, erfüllst drei freiwillige, wiederholbare Verträge, besuchst andere Farmen und entscheidest später selbst, ob du Prestige für einen kleinen dauerhaften Bonus auslöst.

## Beta 0.1 | Verbindlicher Umfang

**Checkliste: geplant, aktuell nicht als umgesetzt markiert.** Die vollständigen Regeln, Abgrenzungen und Erfolgskriterien stehen in [docs/game-vision.md](docs/game-vision.md).

- [ ] **Eine** kompakte Mining-District-Map mit **sechs** persönlichen Grundstücken und einer Starter-Garage pro Spieler
- [ ] **Sechs fiktive GPU-Modelle** mit sichtbarer Installation und **drei Rack-Grössen** mit festen Slots
- [ ] Virtuelle **BTC**, **Credits (C)**, serverseitige Online-Mining-Produktion, GPU-/Rack-Shop und Exchange mit fixer Rate
- [ ] Strom-/Kühl-Kapazitäten, Effizienzeinbussen und wenige gezielte Upgrades
- [ ] **Eine** kaufbare Garagen-/Grundstückserweiterung
- [ ] Kurzes, überspringbares Tutorial mit kostenloser aktiver Starter-GPU
- [ ] Responsives HUD und vollständige Kernbedienung auf **PC und Smartphone**
- [ ] Zuverlässige Speicherung von Guthaben, Hardware, Upgrades, Aufträgen und Prestige
- [ ] **Drei** wiederholbare Mining-Verträge mit begrenzten Credit-Belohnungen
- [ ] **Ein** freiwilliger Prestige-Lite-Reset mit kleinem permanentem Tech-Bonus
- [ ] Multiplayer-Farmbesichtigungen und **serverlokale** Bestenliste nach effektiver Hashrate
- [ ] Sicherheits-, Geräte-, Mehrspieler- und Playtest-Abnahme vor einer ausdrücklich genehmigten **geschlossenen** Beta

**Nicht in Beta 0.1:** Echtgeld, Blockchain, echte BTC, Wallets, Auszahlungen, Trading, dynamischer Markt, weitere Coins/Maps, Offline-Mining, PvP, Lootboxen, Robux-Shop, globale Rankings oder freie Kabel-/Gebäudephysik.

## Technische Grundlage und Verantwortungen

| Bereich | Geplanter Ansatz |
| --- | --- |
| Engine / Sprache | Roblox Studio / **Luau** |
| Spielentwicklung | **Claude Code direkt in Roblox Studio über MCP**, mit Studio-Playtests |
| Spiellogik | Serverseitig autoritative Transaktionen und pro Spieler aggregiertes Mining; Client sendet Aktionen, keine vertrauenswürdigen Beträge |
| Daten | Roblox DataStore mit Rejoin-, Ladefehler- und Mehrfachsession-Schutz; Details in DOC-03 |
| GitHub | **ChatGPT** bearbeitet Issues, Dokumentation, Planung, Reviews und Abnahmen |
| Grenzen | **Kein Rojo**, keine GitHub-Codeänderungen durch Claude, keine Änderungen am separaten Roblox-Projekt; richtiges Place vor Studio-Zugriff verifizieren |

## Projektplan und Dokumentation

| Dokumentationsschritt | Status / Link |
| --- | --- |
| **DOC-01:** Spielvision und verbindlicher Beta-Scope | [Spielvision](docs/game-vision.md) · [Issue #1](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/1) |
| **DOC-02:** Economy, GPUs, Racks und Balancing | [Issue #2](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/2), noch zu spezifizieren |
| **DOC-03:** Architektur, Persistenz und Sicherheit | [Issue #3](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/3), noch zu spezifizieren |
| **DOC-04:** Map, Artstyle und UX-Flows | [Issue #4](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/4), noch zu spezifizieren |
| **DOC-05:** Beta-Testplan und Freigabe-Gates | [Issue #5](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/5), noch zu spezifizieren |
| **GAME-01–14:** Umsetzung und Beta-Härtung | [Einstieg: #6](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/6) · [Beta-Abnahme: #19](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/19) |

**Reihenfolge:** DOC-01 → DOC-02 → DOC-03/DOC-04 → DOC-05 → Studio-Implementierung nach den Issue-Abhängigkeiten → GAME-14 Beta-Abnahme. Kein automatischer Merge oder öffentlicher Release.

## Hinweis zu Bitcoin und Eigenständigkeit

Alle Coins, Hashrates und Mining-Geräte sind **fiktive Spielelemente**. Im Spiel kann man **keine echten Bitcoins verdienen, überweisen oder auszahlen**; es gibt keine Wallet-Verbindung und keine garantierten Geldwerte. Eigenständige Assets, eigene UI und eigene Weltgestaltung sind Pflicht. **Name und mögliche Rechtekonflikte müssen vor einer öffentlichen Veröffentlichung geprüft werden.**

Die laufende Planung und sämtliche Abnahmen werden über die [GitHub-Issues](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues) nachvollziehbar geführt.

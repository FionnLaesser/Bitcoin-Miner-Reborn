# Bitcoin Miner: REBORN | Spielvision und verbindlicher Beta-0.1-Scope

> **Status:** Produktdefinition für die geplante geschlossene Beta 0.1. Die beschriebenen Funktionen sind **Soll-Anforderungen**, keine Behauptung über bereits implementierte oder getestete Features. **Bitcoin Miner: REBORN ist ein vorläufiger Arbeitstitel.**  
> **Verantwortung:** [DOC-01, Issue #1](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/1) · **Stand:** 29.10.2026 · **Geltung:** Nach Merge Grundlage für alle Beta-Implementierungsissues.

## 1. Produktidentität

### Vision in einem Satz

Spieler bauen in einem kompakten, gemeinsam bewohnten Mining-District eine sichtbare virtuelle GPU-Farm auf, verdienen **ausschliesslich fiktive BTC** und werden nicht nur durch mehr Hardware, sondern durch **kluge Strom-/Kühlungsoptimierung und kurze, aktive Mining-Aufträge** erfolgreicher.

| Bereich | Verbindliche Aussage |
| --- | --- |
| Genre | Zugänglicher Roblox-Aufbau- und Idle-/Management-Simulator mit aktiven Optimierungsentscheidungen |
| Zielgruppe | Roblox-Spieler, die einfache Simulator-Loops, sichtbaren Ausbau und überschaubare Optimierung mögen; spielbar auf PC und Smartphone |
| Spielgefühl | Schnell verständlich, ruhiger stetiger Fortschritt, nachvollziehbare Upgrades, befriedigender Vorher-/Nachher-Vergleich |
| Spielmodus | Bis zu **sechs Spieler pro Server** auf sechs getrennten Grundstücken; gemeinsamer District, persönliche Farm |
| Währungen | **Virtuelle BTC** als Mining-Ertrag und **Credits (C)** als Kauf- und Belohnungswährung |
| Kernversprechen | Jede zusätzliche GPU verändert die sichtbare Farm; gute Effizienz verhindert, dass blosses Sammeln zur einzigen Entscheidung wird |
| Abgrenzung | Eigenständiges Spiel, **keine offizielle Fortsetzung, Neuauflage oder Verbindung** zum früheren Spiel namens «Bitcoin Miner» |

Die Idee «GPU kaufen und Mining-Ertrag vergrössern» ist eine allgemeine Genre-Mechanik, nicht der Anspruch auf eine Kopie. **Eigenständig** sind die Kombination aus verständlichem Kapazitätsmanagement, drei wiederholbaren Spielaufträgen, sichtbaren Rack-/Farm-Veränderungen, freiwilligem Prestige und einer bewusst kleinen sozialen Umgebung. Setting, Modelle, Karte, Interface, Texte, Sounds und Markenauftritt werden unabhängig gestaltet; nichts wird aus einem fremden Roblox-Spiel übernommen.

### Designprinzipien

1. **Erste Handlung sofort:** Ein neues Profil startet am eigenen Plot mit **genau einer kostenlosen, bereits aktiven Starter-GPU**. Kein Pflichtdialog und kein Robux-Kauf blockiert den Einstieg.
2. **Verstehen vor Komplexität:** Zwei Währungen und zwei klare Kapazitätsanzeigen (Strom/Kühlung). Keine Blockchain-Erklärung, Kabelphysik oder Börsensimulation nötig.
3. **Wachstum hat eine Ursache:** Neue GPUs erhöhen die Rohleistung; die effektive Leistung hängt auch von der verfügbaren Versorgung ab. Engpässe sind sichtbar und lösbar.
4. **Aktivität ergänzt Automatik:** Online-Mining läuft automatisch, während Spieler mit Kauf, Verkauf, Umrüstung und Aufträgen Entscheidungen treffen. Keine hektischen Klickzwänge.
5. **Fortschritt ist sichtbar und sozial:** Racks, GPU-Status, Grundstücksausbau und serverlokale Bestenliste zeigen echte Farm-Entwicklung. Besuchende dürfen anschauen, nicht verändern.
6. **Fair, sicher, klein:** Keine Echtgeldversprechen, Zufallsverkäufe oder bezahlten Vorteile in der Beta. Die Autorität für Geld, Inventar und Mining liegt beim Server.

## 2. Kernloop und Motivation

### Von der Starter-GPU zur optimierten Farm

1. **Ankommen:** Der Server weist einem Spieler einen freien Plot zu; die Starter-GPU produziert bereits. Eine kurze UI-Hilfe zeigt die erste Aktion.
2. **Mining beobachten:** Installierte GPUs erzeugen während einer laufenden Spielsitzung automatisch **virtuelle BTC**. Das HUD zeigt BTC, BTC/s und Roh-/Effektiv-Hashrate.
3. **BTC tauschen:** Der Spieler verkauft BTC an der Exchange zur **festen Beta-Rate** gegen Credits. Der Umtausch ist nachvollziehbar und keine echte Finanztransaktion.
4. **Hardware kaufen:** Mit Credits werden eine von sechs fiktiven GPU-Varianten oder passende Racks erworben. Jede Variante hat später dokumentierte Werte und Kosten.
5. **Installieren und vergleichen:** GPUs liegen im Inventar, werden in **feste Rack-Slots** eingesetzt, versetzt oder entfernt. Das sichtbare Gerät und die angezeigte Produktionsrate verändern sich.
6. **Engpass beseitigen:** Strom- und Kühlkapazität werden mit Verbrauch und Wärmelast verglichen. Gezielte Kapazitäts-Upgrades machen vorhandene Hardware produktiver.
7. **Ausbauen und Ziele setzen:** Eine zusätzliche Garagen-/Grundstücksstufe schafft Rack-Fläche; drei wiederholbare Verträge belohnen echtes Spielen. Später ist ein **freiwilliger Prestige-Reset** für einen kleinen dauerhaften Tech-Bonus möglich.

**Warum das motiviert:** Jede Runde enthält eine kurze Erwartung (nächster Verkauf), eine klare Entscheidung (GPU oder Effizienz?), sichtbares Feedback (aktive neue Hardware) und ein grösseres Ziel (Ausbau/Prestige). Aufträge liefern zusätzliche Ziele, ohne die Grundwirtschaft durch unbegrenzte Belohnungen zu ersetzen.

### Festgelegte Systemgrenzen

- **Online-only-Produktion:** BTC entstehen nur während einer gültigen aktiven Serversitzung. Kein Offline-Mining oder Nachvergüten abgelaufener Zeit zwischen zwei Logins.
- **Server als Quelle der Wahrheit:** Client-Aktionen sind Kauf-, Platzierungs-, Verkaufs- und Upgrade-**Anfragen**. Nur der Server berechnet/prüft Guthaben, Besitz, Preis, Slots, Kapazität, Fortschritt und Produktion.
- **Keine Wertschöpfung aus dem Nichts:** Ohne installierte GPU oder ohne Stromkapazität ist die BTC-Produktion null. Kühlengpässe begrenzen die Leistung, zerstören aber in der Beta keine Hardware. Exakte Formel und Grenzfälle folgen in [DOC-02](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/2).
- **Kapazitätsmodell statt Kabelbau:** Strom und Kühlung sind aggregierte Werte pro Farm, keine manuell zu verdrahtenden Geräte. Details zu Berechnung, Rundung und Upgrade-Stufen stehen in DOC-02.
- **Transaktionssicherheit:** Käufe, Exchange, Auftragserfüllung und Prestige dürfen durch Wiederholung, Doppelklick oder ungültige Client-Werte keine Duplikate oder negative Salden erzeugen.

## 3. Beabsichtigtes Spielerlebnis und Progression

Die folgenden Zeitpunkte sind **Design- und Balancing-Ziele, keine Playtest-Ergebnisse**. Sie werden in [DOC-02](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/2) quantifiziert und später in [DOC-05](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/5) anhand echter Tests überprüft.

| Zeitpunkt | Geplantes Erlebnis | Erfolgsindikator im späteren Test |
| --- | --- | --- |
| **0–60 Sekunden** | Spawn am eigenen Plot; eine GPU läuft. Kontexthinweise führen zu BTC-Anzeige, erstem Verkauf und Kauf/Einbau der **zweiten GPU**. | Neue Testperson versteht ohne mündliche Hilfe den Loop; erste zusätzlich gekaufte GPU **nach ungefähr 60 s erreichbar** (Tuning-Ziel). |
| **Bis 5 Minuten** | Spieler erkennt die Wirkung einer weiteren GPU und führt eine sinnvolle Entscheidung zwischen Hardware und Strom-/Kühl-Upgrade aus. | Ein **deutliches, sicht- und messbares Upgrade** ist ungefähr nach 5 min möglich, nicht zwingend exakt zu diesem Zeitpunkt. |
| **20–30 Minuten** | Mehrere unterschiedliche Verbesserungen, erste Vertragsabschlüsse, Engpassoptimierung und ein erkennbares Ziel für die Garagenerweiterung. | Testpersonen können selbst erklären, welcher Ausbau als Nächstes hilft; mehrere Fortschrittsschritte sind erreichbar. |
| **Weitere Sitzungen** | Farm weiterentwickeln, Aufträge erneut bearbeiten, andere Farmen besuchen und sich in der lokalen Hashrate-Tabelle vergleichen. | Rejoin erhält den Fortschritt zuverlässig; keine erfundene Retention- oder Umsatzkennzahl. |
| **Spätes Beta-Ziel** | Nach Erreichen einer klaren Schwelle optional Prestige auslösen und mit einem kleinen dauerhaften Bonus neu starten. | Reset/Fortbestand verständlich, absichtlich ausgelöst und technisch korrekt. |

### Drei kurze, wiederholbare Mining-Verträge

Das Terminal bietet **genau drei Vertragstypen** als aktives Ziel neben der laufenden Produktion:

| Vertragstyp | Beispielhafte Spielerhandlung | Motivation |
| --- | --- | --- |
| **Mining-Ziel** | Eine vorgegebene Menge virtueller BTC durch eigene aktive Produktion erreichen | Fortschritt der Farm spüren |
| **Exchange-Ziel** | Mit regulären BTC-Verkäufen eine vorgegebene Credit-Summe erwirtschaften | Den vollständigen Mining-/Verkaufskreislauf nutzen |
| **Effizienz-Ziel** | Mit der eigenen Farm eine definierte effektive Leistung bzw. Effizienz erreichen | Strom-/Kühl-Optimierung belohnen |

Alle drei Typen sind freiwillig, serverseitig nachgewiesen, wiederholbar **mit eindeutigen Abschluss-/Cooldown-Regeln** und geben begrenzte **Credit-Belohnungen**, keine dritte Währung. Konkrete Schwellen, Belohnungen und Wiederholungsregeln definiert DOC-02. Keine Daily-Streaks, zufälligen Aufgabenpakete oder zeitlich erzwungene Anwesenheit.

### Prestige Lite

Genau **eine einfache Prestige-Mechanik** gehört zur Beta: Nach einer in DOC-02 festzulegenden Freischaltschwelle kann der Spieler freiwillig einen bestätigten Reset ausführen. **Zurückgesetzt** werden virtuelle BTC, Credits, GPUs/Inventar, Racks, Grundstücksstufe sowie Strom-/Kühl-Upgrades; **erhalten** bleiben Prestige-Zähler und ein kleiner permanenter Tech-/Mining-Bonus. Nach dem Reset gibt es wieder das reguläre Starter-Rig mit einer aktiven Starter-GPU. Die vollständigen Regeln für Vertragsstatus, Bonuswert, Schwelle und sichere Wiederholungsabwehr stehen in DOC-02/DOC-03. Kein Forschungsbaum und keine zusätzlichen Prestige-Währungen.

### Multiplayer als Motivation, nicht als Handelsplattform

Bis zu sechs Spieler sehen ihre Nachbarn im District. Fremde Plots dürfen besucht und deren GPU-Aufbau betrachtet werden. Eine **serverlokale** Bestenliste vergleicht die vom Server berechnete **effektive Hashrate** der aktuell anwesenden Spieler und aktualisiert sich nachvollziehbar. Es gibt **kein Trading, keine PvP-Eingriffe, kein globales Ranking** und keinerlei Rechte, fremde Hardware zu verwalten.

## 4. Verbindlicher Beta-Umfang (Version 0.1)

Jede Zeile ist **Pflichtbestandteil** der geschlossenen Beta. Verweise zeigen, welches vorhandene GAME-Issue die Umsetzung konkretisiert. Zahlen, Assetnamen, API- und UX-Details werden in den zuständigen Folge-Dokumenten definiert, ohne den Umfang zu erweitern.

| ID | In Scope: umsetzbarer Funktionsumfang | Nachweis auf Produktebene | Issues |
| --- | --- | --- | --- |
| **B01** | **Ein kompakter Mining-District** mit zentralem GPU-/Rack-Shop, Exchange, Vertragsterminal und Platz für die lokale Bestenliste. Eigener, einfacher Low-Poly-Futurismus; kurze Wege. | Alle Stationen sind erreichbar, erkennbar und nutzbar; **nur eine Map**. | [#7](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/7) |
| **B02** | **Genau sechs getrennte Spielerplots**, je mit Starter-Garage, Rack-Flächen, Spawn und Besitzanzeige. Server weist genau einen freien Plot je Spieler zu und gibt ihn beim Verlassen frei. | Sechs gleichzeitige Spieler erhalten sechs unterschiedliche Plots; fremde Verwaltung scheitert. | [#7](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/7) |
| **B03** | **Genau sechs unterschiedliche, fiktiv benannte GPU-Modelle** mit eigenen Werten und erkennbaren eigenen 3D-Varianten. Ein neues Profil hat genau eine kostenlose, aktive Starter-GPU. | Alle sechs Typen sind kauf-/installierbar; nur installierte aktive GPUs minen. | [#10](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/10), [#15](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/15) |
| **B04** | **Drei Rack-Grössen** mit festen, begrenzten Slots; GPU-Inventar sowie Installieren, Umsetzen und Entfernen über gültige Slot-IDs. Keine freie Bauphysik. | Voller/fremder Slot und doppelte Item-Nutzung werden abgelehnt; Belegung überlebt Rejoin. | [#10](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/10) |
| **B05** | **Genau zwei Spielwerte als Währungen:** geminte **virtuelle BTC** und kaufbare/verdienbare **Credits (C)**. Beide getrennt und klar angezeigt. | Kein Echtgeld-/Wallet-Bezug, kein negativer Saldo, keine dritte Währung. | [#8](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/8), [#11](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/11) |
| **B06** | **Automatisches serverseitiges Mining während des Online-Spiels** mit pro Spieler aggregierter GPU-Leistung und reproduzierbarer BTC-Rate. | Produktionsänderungen nach Ein-/Ausbau sowie null bei fehlender GPU/Strom; Client kann Ertrag nicht setzen. | [#9](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/9) |
| **B07** | **GPU-/Rack-Shop** mit fest definierten Preisen und sicheren Credit-Käufen. | Erfolgreicher Kauf erzeugt genau ein Inventarobjekt; ungenügende Credits/Spam/ungültige IDs werden abgelehnt. | [#11](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/11) |
| **B08** | **Exchange** für virtuelle BTC → Credits mit **fester** Beta-Umtauschrate, ohne dynamischen Kurs oder Rücktausch. | BTC sinken und Credits steigen atomar um den konfigurierten Betrag; ungültige Verkäufe verändern nichts. | [#11](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/11) |
| **B09** | **Strom und Kühlung** als Farm-Kapazitäts-/Effizienzsystem inkl. weniger kaufbarer Upgradestufen und verständlicher Engpassanzeige. Keine Schäden, Einzelkabel oder Energiekostenabrechnung. | Leistungseinbusse bzw. Verbesserung stimmt mit DOC-02 überein; Kapazitätswechsel und Grenzfälle sind testbar. | [#12](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/12) |
| **B10** | **Genau eine kaufbare Grundstücks-/Garagenerweiterung** für zusätzliche feste Rack-Flächen, sichtbar anders als die Starter-Garage. | Einmaliger, gespeicherter Ausbau nach geprüftem Kauf; keine zweite Map/Gebäudestufe. | [#13](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/13) |
| **B11** | **Kurzes, überspringbares Einstiegstutorial:** Mining beobachten → erste BTC verkaufen → zweite GPU kaufen/installieren; später erneut aufrufbare Hilfe. | Ein Neuling schafft den Loop ohne mündliche Hilfe; bei Rejoin keine erzwungene Wiederholung. | [#15](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/15) |
| **B12** | **Responsive PC-/Touch-UI** mit HUD (Credits, BTC, BTC/s, Hashrate, Strom/Kühlung), Shop, Exchange, Inventar, Upgrades, Verträgen, Prestige und verständlichen Fehlerzuständen. | Gesamter Pflichtloop auf Desktop und Smartphone ohne Entwicklerkonsole und ohne verdeckte kritische Schaltflächen bedienbar. | [#14](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/14) |
| **B13** | **Zuverlässiges Speichern** von Geld, Inventar, Rack-Slots, Upgrades, Grundstück, Verträgen, Tutorial und Prestige; Session-Schutz, Wiederherstellung und Fehlerbehandlung. | Rejoin/Serverwechsel korrekt; bei Ladefehler kein neues Leerprofil mit Überschreiben bestehender Daten. | [#8](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/8) |
| **B14** | **Multiplayer mit Farmbesichtigung** und **serverlokaler Bestenliste** nach effektiver Hashrate; Besitzanzeige und bereinigter Join-/Leave-Zustand. | Sechs Spieler können zeitgleich spielen; Besuchende sehen, dürfen aber nicht manipulieren; kein globales Ranking. | [#18](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/18) |
| **B15** | **Genau drei wiederholbare Verträge** (Mining, Exchange, Effizienz) mit kleinen, serverseitig einmalig vergebenen Credit-Belohnungen und Cooldown. | Alle drei mit normalen Aktionen abschliessbar; bei Wiederholungsversuch kein Doppelreward; Fortschritt wird gespeichert. | [#16](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/16) |
| **B16** | **Ein freiwilliges Prestige Lite** mit bestätigtem Reset, dauerhaftem Prestige-Zähler und kleinem Tech-Bonus; nachvollziehbare Regeln und neuer Starter-Status. | Kein unfreiwilliger/doppelter Reset; Bonus und Reset nach Rejoin korrekt. | [#17](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/17) |

**Umfangsregel:** Die Formulierungen «genau» und «ein» setzen für Beta 0.1 eine harte Obergrenze für Inhalte (nicht für einzelne GPU-Exemplare, Rack-Käufe oder erneute Vertragsdurchläufe). Änderungen am Pflichtumfang erfordern eine bewusste Entscheidung im Projekt, nicht eine stillschweigende Erweiterung durch GAME-Issues.

### Qualität, die für sämtliche B01–B16 gilt

- **Eindeutiges Feedback:** Kauf, Verkauf, Installation, Engpass und Freischaltung haben lesbare Bestätigungs- und Fehlerzustände; keine wichtige Aktion hängt von einem nicht dokumentierten Tastendruck ab.
- **Eigentum und Werte:** Der Server validiert Berechtigung, Wertebereiche, Guthaben, Besitz, Limits und doppelte Aufträge; fremde Plots sind lesbar, aber nicht veränderbar.
- **Leistungsbudget:** Maximal sechs aktive Spieler sind mit mehreren Racks flüssig bedienbar. Mining läuft aggregiert pro Spieler, **keine eigene Dauerschleife pro GPU und kein DataStore-Schreibzugriff pro Tick**.
- **Barrierearme Bedienung:** Touch-Ziele, Kontrast, kurze Texte, klare Zahlenlabels und Eingabealternativen für Maus/Tastatur werden in DOC-04 konkretisiert.

## 5. Ausdrücklich ausserhalb der Beta

| Nicht Bestandteil von 0.1 | Warum / Grenze |
| --- | --- |
| Echte Kryptowährungen, Blockchain, Mining auf echten Geräten, Wallets, Auszahlungen, Echtgeldpreise | Das Spiel simuliert vollständig **fiktive** Währungen und Leistung. |
| Dynamischer BTC-Kurs, mehrere Coins, Krypto-Trading, spielerübergreifender Handel, globaler Marktplatz | Die Beta benötigt nur **BTC → Credits zu fixer Rate**. |
| Weitere Maps/Rechenzentren, Grundstücksstufen, freies Bauen, physische Kabel, komplexe Gebäudemechanik | Eine Map, Starter-Garage und **eine** Erweiterung reichen. |
| Offline-Mining, AFK-Rewards für abwesende Spieler, Daily-Streak-/Login-Zwang | Ertrag nur während einer aktiven Serversitzung; kurze freiwillige Ziele statt Druck. |
| PvP, Sabotage, globales Ranking, globale Freundes-/Clanfunktionen, Mining-Pools | Soziale Interaktion beschränkt sich auf Besuche und serverlokale Tabelle. |
| Forschungssystem/Skilltree, zusätzliche Prestige-Währungen oder mehrere Prestige-Zweige | In Beta nur Prestige Lite mit einem dauerhaften Bonus. |
| Lootboxen, bezahlte Zufallsmechaniken, Robux-Shop, verpflichtende Käufe, Pay-to-win | Beta ist ohne Monetarisierung vollständig spielbar. |
| Zusätzliche GPUs, zeitlich begrenzte Events, saisonale Battle-Pässe, komplexe Live-Ops | Kein Feature Creep vor stabiler geschlossener Beta. |

**Optionen für die Zukunft, nicht für 0.1:** zusätzliche fiktive Coins und ein kontrollierter dynamischer Markt, neue Rechenzentren, weitere GPU-Serien, kooperative Mining-Pools, Forschung, zusätzliche Prestige-Stufen und kosmetische Farm-Individualisierung. Jede Option erfordert später ein separates Konzept und eine ausdrückliche Scope-Entscheidung. Ihre Erwähnung hier begründet **keine** Implementierungspflicht.

## 6. Eigenständigkeit, Rechte und Fairness

- Spielname **«Bitcoin Miner: REBORN» ist nur ein Arbeitstitel**. Vor einer **öffentlichen** Veröffentlichung mögliche Marken-, Titel- und sonstige Rechtekonflikte prüfen und bei Bedarf umbenennen. Der Begriff «REBORN» bedeutet **keine** offizielle Fortsetzung.
- Keine fremden Original-Assets, Karten, Skripte, Sounds, Texte, UI-Layouts, Logos oder erkennbar geschützten Gestaltungen übernehmen. Eigene Inhalte verwenden oder Lizenzen eindeutig prüfen und dokumentieren.
- «BTC» und «Credits» sind **rein fiktive Zahlen innerhalb des Spiels**, ohne Verbindung zu echtem Bitcoin, realen Kursen, Wallets oder realem Gegenwert. Beschreibung und UI dürfen kein echtes Einkommen versprechen.
- Beta ohne verpflichtende Robux-Käufe, ohne bezahlte Zufallsmechaniken, ohne Trading/Glücksspielsysteme. Fortschritt beruht auf verständlicher Simulation und bewussten Entscheidungen.
- Roblox-relevante Inhalts-/Altersangaben, Berechtigungen sowie private Testfreigabe vor der geschlossenen Beta prüfen. **Keine öffentliche Veröffentlichung ohne ausdrückliche Zustimmung des Projektbesitzers.**

## 7. Definition of Done: gute geschlossene Beta

**Die Spielvision ist durch DOC-01 dokumentiert. Die Beta ist dadurch noch nicht implementiert oder freigegeben.** «Geschlossene Beta bereit» kann erst nach nachgewiesener Erfüllung der folgenden Punkte beansprucht werden; die konkreten Testfall-IDs, Severity-Stufen und Release-Gates entstehen in [DOC-05](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/5).

| Gate | Messbarer Nachweis | Beta-Blocker |
| --- | --- | --- |
| **Funktionsvollständigkeit** | Jede Pflichtzeile **B01–B16** im verifizierten eigenen Studio-Place erfüllt, mit mindestens einem Erfolgs- und Fehlertest pro Funktion. | Kernloop oder Pflichtfunktion nicht spielbar. |
| **Onboarding/Progression** | Moderierter bzw. beobachteter Test mit **5–10 Personen**; erste neue GPU nach ungefähr 60 s und bedeutender Fortschritt nach ungefähr 5 min sind **Zielwerte**, nicht schon belegte Ergebnisse. Erkenntnisse fliessen in DOC-02-Tuning ein. | Neulinge scheitern systematisch am Loop; kein realistischer Fortschritt. |
| **Datenintegrität** | Rejoin, Serverwechsel, Shutdown, paralleler Join, Ladefehler und Datenmigration getestet; Spielstand bleibt konsistent, Ladefehler überschreibt keine gespeicherten Profile. | Datenverlust, Item-/Belohnungsduplikation oder stille Profilüberschreibung. |
| **Sicherheit** | Fremde Plot-/Slot-Manipulation, manipulierte Remotes und negative/NaN/unendliche/extreme Werte zurückgewiesen; Kauf/Quest/Prestige gegen wiederholte Ausführung geschützt. | Ausnutzbare kostenlose Käufe, fremder Besitz, Dupes oder Währungsmanipulation. |
| **Multiplayer/Performance** | **Sechs parallele Spieler**, mehrere Racks, korrekte Plot-Zuteilung/Leaveroutine und lokale Bestenliste geprüft; keine auffälligen stabilitätskritischen Engpässe. | Servercrashes, Blockaden, massive Performanceprobleme oder Ownership-Lecks. |
| **Geräte/Usability** | Vollständiger Loop mit Maus/Tastatur und auf Smartphone/Touch getestet; lesbare HUD-/Fehlerzustände, keine verdeckten Kernaktionen. | Kernaktion auf einem Zielgerät unbedienbar. |
| **Rechte/Freigabe** | PlaceId/UniverseId des **richtigen Spiels** dokumentiert; eigene/lizenzierte Inhalte, fiktive BTC-Kommunikation, Testerzugang, Backup/Rollback und bekannte Restfehler geprüft. | Ungeklärte gravierende Rechteprobleme, fehlender Rückfallplan oder fehlende Besitzerfreigabe. |

**Abnahmeentscheidung:** [GAME-14, Issue #19](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/19) führt die Testmatrix durch und protokolliert Ergebnisse, Restfehler und offene Risiken. Ein Gate ist **nicht erfüllt**, solange ein Blocker besteht oder sein Testnachweis fehlt. Auch ein technisch bestandener Testplan bedeutet **keine automatische öffentliche Freigabe**: Der Besitzer genehmigt höchstens die geschlossene Testphase ausdrücklich. Es liegen für diese Vision **keine Playtest-Daten und keine verifizierten Studio-Ergebnisse** vor.

## 8. Verantwortlichkeiten, Folgeentscheidungen und Reihenfolge

### Arbeitsweise

| Zuständigkeit | Erlaubte Arbeit | Nicht erlaubt / nicht vorgesehen |
| --- | --- | --- |
| **ChatGPT** | GitHub-Issues, Planung, Markdown-Dokumente, Review, Quality Gates und Nachbereitung | Roblox-Studio-Inhalte ungefragt verändern |
| **Claude Code** | **Ausschliesslich** das neue Bitcoin-Miner-Spiel direkt in Roblox Studio via **MCP** umsetzen, Studio-Playtests ausführen, kurze Pfad-/Testergebnisberichte geben | GitHub-Code schreiben, GitHub-Issues/PRs pflegen, **Rojo** oder GitHub-Studio-Synchronisation voraussetzen |

Vor jedem Studio-Eingriff **UniverseId, PlaceId und Spielname des Bitcoin-Miner-Projekts explizit verifizieren**. Die PlaceId des anderen Roblox-Projekts darf **niemals** als Ersatz dienen; bei Nichtübereinstimmung keine Änderung. GitHub enthält Planung/Dokumentation/Abnahme, nicht einen durch Claude gepflegten Script-Mirror.

### Noch offen: bewusst an die Folge-Dokumente delegiert

| Folgeauftrag | Verbindlich zu entscheiden, **nicht** in DOC-01 zu erfinden |
| --- | --- |
| [DOC-02 #2](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/2) | Sechs GPU-Namen und Werte, drei Rack-Grössen/Slotzahlen, Preise/Start-Credits, feste Exchange-Rate, Mining-Formel samt Null-/Kühl-Grenzfällen, Auftragsziele/Belohnungen/Cooldowns, Upgrade-Stufen, Prestige-Schwelle/Bonus/Vertragsreset und realistische Zielkurve. |
| [DOC-03 #3](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/3) | Luau-Serviceverantwortung, Remote-Vertrag, Profilschema/Item-IDs, DataStore-Sperre/Migration/Fehlerbehandlung, aggregierte Ticks, korrekter Studio-MCP-Workflow. |
| [DOC-04 #4](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/4) | Konkrete Map-/Garagen-Skizze, visuelle Sprache, UI-Flows/Wireframes, Touch-Ziele, eigene Assetliste und Zustands-/Fehlermeldungen. |
| [DOC-05 #5](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/5) | Reproduzierbare Testfälle mit IDs, Failure-Severity, Geräte-/Mehrspielermatrix, Testprotokoll, Closed-Beta-Entscheid und Rollback-Gates. |

### Rückverfolgbarkeit zu den bereits angelegten GAME-Issues

| Reihenfolge nach fachlichen Abhängigkeiten | Implementierungs-Issue | Beta-Verantwortung |
| --- | --- | --- |
| 1 | [GAME-01 #6](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/6) | Korrekte Studio-Basis, Konfiguration und Playtest-Voraussetzung für **alle B-IDs** |
| 2 | [GAME-02 #7](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/7) | **B01–B02** Map, Plots, Ownership |
| 3 | [GAME-03 #8](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/8) | **B05, B13** Profile, sichere Persistenz |
| 4 | [GAME-04 #9](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/9) | **B06** Mining-Engine |
| 5 | [GAME-05 #10](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/10) | **B03–B04** GPU-Inventar, Racks |
| 6 | [GAME-06 #11](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/11) | **B05, B07–B08** Shop und Exchange |
| 7 | [GAME-07 #12](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/12) | **B09** Strom/Kühlung |
| 8 | [GAME-08 #13](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/13) | **B10** Garage-Ausbau |
| 9 | [GAME-09 #14](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/14) | **B12** UI/Touch |
| 10 | [GAME-10 #15](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/15) | **B03, B11** Starter-GPU und Onboarding |
| 11 | [GAME-11 #16](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/16) | **B15** Verträge |
| 12 | [GAME-12 #17](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/17) | **B16** Prestige Lite |
| 13 | [GAME-13 #18](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/18) | **B14** Farmbesichtigung/Bestenliste |
| 14 | [GAME-14 #19](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/19) | **B01–B16** Integration, Härtung, Abnahme und Freigabevorbereitung |

**Dokumentations-Gates:** DOC-01 → DOC-02 → DOC-03 und DOC-04 (nach DOC-02) → DOC-05 → GAME-01 und abhängige GAME-Issues → GAME-14. Die Tabelle ist eine **empfohlene grobe Bearbeitungsreihenfolge**, keine Aufhebung der in den Issues genannten Einzelabhängigkeiten. Bestehende GAME-Issues dürfen ihre fachlichen Dokumentations-Abhängigkeiten nicht überspringen.

---

**Entscheidungsregel:** Bei Widerspruch zwischen einer späteren Detailimplementierung und dieser Produktvision zuerst das betroffene Issue und die Dokumentation prüfen. Beta-Umfang, Eigenständigkeit, Sicherheitsgrundsätze oder technische Zuständigkeitsgrenzen dürfen nur per bewusster, dokumentierter Scope-Entscheidung geändert werden.

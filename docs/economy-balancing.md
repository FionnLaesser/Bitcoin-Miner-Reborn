# Bitcoin Miner: REBORN | Economy- und Balancing-Spezifikation (Beta 0.1)

> **Status:** verbindlicher Zahlen- und Regelentwurf für DOC-02 / [Issue #2](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/issues/2), Stand 29.10.2026. **Abhängigkeit:** [DOC-01 / PR #20](https://github.com/FionnLaesser/Bitcoin-Miner-Reborn/pull/20) ist bei Erstellung noch **nicht in main gemergt**. Die Spezifikation basiert auf dessen `docs/game-vision.md` und darf erst nach dessen Merge und Abgleich als endgültig freigegeben gelten. **Keine Spielimplementierung und keine Playtest-Ergebnisse.**
>
> Alle BTC sind **rein fiktive Spielwerte**. Kein echter Bitcoin, kein Wallet, kein Handel mit Echtgeld. PC- und Touch-Bedienung sowie Serverautorität gemäss DOC-01 bleiben bindend.

## 1. Ziel, Grundsätze und Grenzen

Kernloop: **aktive GPU im Rack → serverseitiges Online-Mining → BTC gegen Credits (C) verkaufen → GPUs/Racks und Versorgung kaufen → optimieren → Ausbau → optional Prestige**. Die ersten Sekunden müssen belohnen; ab der dritten GPU ist Kapazitätsmanagement spürbar. Keine Robux-Notwendigkeit, kein Offline-Mining, keine Strom-Rechnungen, keine Defekte, keine weiteren Währungen, Maps oder Forschung.

**Eine Zeitangabe ist ein Designziel, kein gemessener Spielerwert.** Preise sind absichtlich fix. Eine GPU darf trotz bezahltem Kauf unprofitabel sein, wenn Versorgung fehlt; Shop/Preview müssen deshalb die *voraussichtliche effektive* Hashrate nach Einbau zeigen und vor Rückschritten warnen.

## 2. Einheiten, Währungen und Starterzustand

| Kennzahl | Verbindlicher Wert / Einheit |
| --- | --- |
| Währungen | `BTC` (fiktive Mining-Währung) und ganzzahlige `Credits` (`C`) |
| Start `credits` / `btcMicro` | `0 C` / `0 µBTC`, keine Start-Auszahlung |
| Feste Exchange-Rate | **1,000000 BTC = 1'000 C**; nur **BTC → C**; keine Gebühren |
| BTC-Speicher | Ganzzahlige **µBTC**; `1 BTC = 1'000'000 µBTC`; Anzeige mit exakt 6 Nachkommastellen |
| Verkaufseinheit | `1 C` kostet genau `1'000 µBTC` (= 0,001000 BTC); kleinere BTC-Reste bleiben erhalten |
| Hashrate | `H` = fiktive Hashrate-Einheit, Anzeige `H/s`; Roh-/Effektivwert |
| Mining-Konstante | `100 µBTC / (H · s)` = `0,000100 BTC` je `H` und Sekunde |
| Daraus folgt | Ohne Engpass/Prestige: `1 H = 0,1 C/s` als *Verkaufsäquivalent* |
| Strom / Wärme / Kühlung | `P` = aggregierte Leistungs-Einheit; `T` = aggregierte Wärme-Einheit; beide dimensionslose Spielgrössen |
| Neu angelegtes Profil | Ein kostenloses `r2_bench`-Rack mit **2 Slots**, genau **eine** kostenlos erhaltene, bereits installierte und aktive `s1_sparrow`-GPU, `powerLevel=0`, `coolingLevel=0`, zwei Garagen-Rackflächen (eine belegt) |
| Starterkapazität | `40 P` Strom und `32 T` Kühlgrenze |
| Dauerkosten | **0 C/s**: Strom/Kühlung sind einmalig kaufbare Kapazitätsstufen, keine laufenden Gebühren |

**Rundung:** `credits` und `btcMicro` sind nichtnegative ganze Zahlen. Die Exchange fragt eine **ganze Anzahl Credits** `sellCredits` an; atomar `btcMicro -= 1'000 * sellCredits` und `credits += sellCredits`. Die Schaltfläche «Max.» wählt das kleinere von `floor(btcMicro / 1'000)`, dem Transaktionslimit und dem freien Credit-Balance-Spielraum. Es gibt keine BTC-Rückkäufe und **keine GPU-/Rack-Rückerstattung oder Hardware-Verkaufsfunktion** in der Beta. Alle Hardwarepreise werden exakt in ganzen C abgezogen.

## 3. Vollständiger GPU-Katalog: genau sechs Modelle

Alle Modelle sind eigens erfundene Spielhardware, jederzeit im Shop sichtbar und durch ihren Preis zugänglich. **Jede GPU belegt genau einen Slot**, unabhängig von Modell. `P` und `T` fallen ausschliesslich bei installierten aktiven Karten an. Ausgebaute Karten produzieren nichts.

| ID / Anzeigename | Preis C | Roh H | Strom P | Wärme T | H/P | H/T | H/C | Wirtschaftliche Rolle |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | --- |
| `s1_sparrow` / Sparrow S1 | **55** | 10 | 10 | 8 | 1,00 | 1,25 | 0,182 | Günstigster Einstieg; schnellster zweiter Kauf |
| `f2_flux` / Flux F2 | **185** | 32 | 28 | 26 | 1,14 | 1,23 | 0,173 | Preiswerter Allrounder mit moderatem Verbrauch |
| `e3_eco` / Eco E3 | **390** | 52 | 17 | 15 | 3,06 | 3,47 | 0,133 | Bestes frühes Verhältnis Leistung zu Strom/Wärme |
| `b4_burst` / Burst B4 | **730** | 122 | 105 | 118 | 1,16 | 1,03 | 0,167 | Viel Hashrate pro Kauf-C, dafür heiss |
| `v5_vector` / Vector V5 | **1'650** | 210 | 70 | 60 | 3,00 | 3,50 | 0,127 | Hohe Slot-Dichte und sehr gute Versorgungseffizienz |
| `t6_titan` / Titan T6 | **3'900** | 510 | 400 | 440 | 1,28 | 1,16 | 0,131 | Höchste Rohleistung pro Slot, hoher Infrastrukturbedarf |

H/P, H/T und H/C in der Tabelle sind **nur Vergleichswerte vor Versorgungskürzungen und Prestige** (auf 2–3 Dezimalstellen gerundet); die Integer in den vier mittleren Spalten sind die alleinige Berechnungsquelle. Beispiel: B4 hat mit `122/730 = 0,1671 H/C` eine attraktivere rohe Kaufleistung als E3 (`52/390 = 0,1333`), kann aber bei ungenügender Kühlung schlechter abschneiden. V5 übertrifft T6 bei `H/P` und `H/T`, T6 bei `H/Slot`. Es gibt keine versteckten GPU-Level oder Zufallswerte.

## 4. Rack-Katalog, Slots und Platzgrenzen

| ID / Name | Preis C | Slots | Freischaltung | Nutzen |
| --- | ---: | ---: | --- | --- |
| `r2_bench` / Bench Rack | **90** | 2 | Sofort; **erstes Exemplar gratis installiert** | Günstig, wenn nur wenige Karten nötig sind |
| `r4_frame` / Frame Rack | **160** | 4 | Sofort | Mehr Slots pro Rackfläche, frühe Ausbauentscheidung |
| `r8_vault` / Vault Rack | **640** | 8 | **Erweiterte Garage**, Strom- und Kühl-Level jeweils mindestens 2 | Hohe Dichte im späteren Spiel |

Starter-Garage: **2 feste Rackflächen** (maximal zwei installierte Racks). Einmaliger Garagenausbau: **4 Rackflächen insgesamt**. Maximal **4 gleichzeitig installierte Racks** und bei Starter-Rack plus drei Vault-Racks **26 GPU-Slots**. Weitere Rackkäufe können auf freie Flächen gesetzt oder im Inventar aufbewahrt werden; **maximal 8 besessene Racks** und **40 besessene GPU-Exemplare** pro Profil. Diese Inventarlimits schliessen installierte Objekte ein.

Jedes Rack und jede GPU erhält eine eindeutige persistente Item-ID. Ein Rack belegt genau eine Fläche, eine GPU genau einen validen Slot (`rackItemId, slotIndex`). GPUs zwischen Racks umsetzen und unbenutzte Racks entfernen ist kostenlos. Ein Rack darf nur eingelagert werden, wenn alle seine Slots leer sind. Kein Tausch, keine physikalische Verkabelung, kein Verlust/Verkauf beim Umsetzen. Installation in bereits belegte Slots oder fremde Plots scheitert atomar. GPU im Inventar ist nicht aktiv; es gibt keine zusätzliche manuelle GPU-Ein-/Ausschaltmechanik.

## 5. Strom und Kühlung: feste Kapazitätsstufen

Die Upgradepreise sind **inkrementell** (Preis für genau die nächste Stufe, nicht kumuliert). Kein Überspringen, kein Downgrade und keine Erstattung.

| Stufe `powerLevel` | Gesamt-Stromkapazität P | Preis zum Erreichen C |
| ---: | ---: | ---: |
| 0 (Start) | 40 | gratis |
| 1 | 120 | **240** |
| 2 | 350 | **1'000** |
| 3 (Maximum) | 1'200 | **5'000** |

| Stufe `coolingLevel` | Gesamt-Kühlgrenze T | Preis zum Erreichen C |
| ---: | ---: | ---: |
| 0 (Start) | 32 | gratis |
| 1 | 100 | **190** |
| 2 | 290 | **820** |
| 3 (Maximum) | 1'000 | **4'250** |

**Gesamtkosten ab Start:** Strom bis Maximum `6'240 C`, Kühlung `5'260 C`. Keine GPU verbraucht Strom im Inventar. Kauf eines Upgrades ist auch ohne gegenwärtigen Engpass erlaubt; die UI zeigt «Aktuell keine zusätzliche Produktion». Ein weiteres Upgrade nach Level 3 wird abgelehnt. Beim Rejoin sind gekaufte Stufen wiederherzustellen.

## 6. Verbindliche Mining- und Exchange-Berechnung

Die folgende Berechnung findet **ausschliesslich auf dem Server** anhand der aktiven installierten GPUs statt.

1. `rawH = sum(gpu.rawH)`, `requiredP = sum(gpu.powerP)`, `heatT = sum(gpu.heatT)`.
2. Falls **keine GPU**, `rawH <= 0` oder `requiredP <= 0`: `effectiveH = 0`. Falls `availableP <= 0`: ebenfalls `effectiveH = 0`. Ungültige Konfigurationswerte dürfen die Formel nie erreichen.
3. Sonst `powerFactor = min(1, availableP / requiredP)` und `coolFactor = max(0.5, min(1, coolingT / heatT))`, wobei `heatT` für alle definierten GPU-Modelle positiv ist.
4. **Verbindliche Formel aus Issue #2:** `effectiveHBeforePrestige = rawH * powerFactor * coolFactor`.
5. `prestigeFactor = 1 + 0.04 * prestigeCount` (maximal 5). `effectiveH = effectiveHBeforePrestige * prestigeFactor`. **Die GPU-P-/T-Werte ändern sich durch Prestige nicht**; Bonus einmalig *nach* den beiden Faktoren anwenden.
6. `rateMicroPerSec = effectiveH * 100`. Für einen servergemessenen Online-Zeitschritt `deltaSeconds` gilt `generatedMicro = floor(rateMicroPerSec * deltaSeconds + miningCarry)`. Der Bruchrest kommt in `miningCarry` (Bereich `[0,1) µBTC`), nicht in `credits`. Nur `generatedMicro` wird dem `btcMicro`-Saldo und dem Produktions-/Vertragszähler gutgeschrieben.
7. Beim Exchange-Request `sellCredits`: exakt `1'000 * sellCredits` µBTC gegen `sellCredits` C tauschen. Kein sofortiger automatischer Coin-Verkauf im echten Spiel.

**Keine Rundung von `effectiveH` vor Schritt 6.** Anzeige: H und H/s mit zwei Nachkommastellen; BTC/s mit sechs Nachkommastellen (nur UI); Cash nur ganze Credits. Der Server hält µBTC und C immer als Integer. `miningCarry` ist ein kleiner flüchtiger Bruchrest; bei Speicherung/Rejoin kann weniger als **1 µBTC** Rest verfallen. Keine Nachzahlung für Offline-Zeit.

**Zeitbehandlung:** Ein aggregierter Mining-Tick je Spieler, `deltaSeconds = clamp(serverElapsed, 0, 5)`. Keine clientseitigen Uhren und keine nachträgliche Zeitgutschrift über fünf Sekunden nach einem Hänger; bei Rejoin beginnt der Takt neu. Änderungen von Rack-/Versorgungszustand gelten ab dem nächsten Tick. Für reproduzierbare Referenzrechnungen gilt `deltaSeconds=1` exakt. Kein DataStore-Write pro Tick.

### Bewusst definierte Grenzfälle

| Fall | Hashrate / Folge |
| --- | --- |
| Null installierte GPUs | `rawH=0`, `effectiveH=0`, `0 µBTC/s`; **keine Division durch null** |
| Kein Strom (`availableP=0`) | `powerFactor=0` und **Mining 0**, auch bei Kühllast 0 |
| Keine Kühlung (`coolingT=0`), aber aktive GPU und Strom | **`coolFactor=0,5`**; weiterhin 50 % der strombereinigten Leistung (explizite Folge der vorgegebenen Formel) |
| Strom zu knapp | Proportionale Minderung mit `availableP / requiredP` |
| Kühlung zu knapp | Faktor `max(0,5, coolingT/heatT)`, **höchstens 50 % Kühl-Malus** |
| Beides ausreichend | `effectiveH = rawH * prestigeFactor` |
| Konfigurations-/Profil-NaN, Infinity, negativer oder nicht-ganzzahliger Wert | Nicht rechnen; Aktion ablehnen bzw. Profil in sicheren Fehlerzustand versetzen; **nie durch frei erfundene Null-/Positivwerte «reparieren»** |
| Tick-Lag, Delta ausser `[0,5]` | Negativ/NaN/Infinity verwerfen, positiver Wert über 5 auf 5 begrenzen; keine Offline-Zeit anrechnen |
| Bilanzmaximum erreicht | Wert nicht über Grenze schreiben; überschüssige Produktion für diesen Tick **nicht gutschreiben**, Warnanzeige; keine Überläufe |

Das Kühlminimum 0,5 gilt **nur** für die Kühlkomponente, nicht für den Stromfaktor. Ohne Strom gibt es auch mit einem Kühlfaktor von 0,5 exakt **keine Produktion**.

## 7. Grundstück: genau ein Ausbau

| Merkmal | Beta-Wert |
| --- | --- |
| Ausbau | `garageLevel`: 0 → 1, danach Maximum |
| Kaufpreis | **3'000 C**, einmalig |
| Freischaltung | Im aktuellen Prestige-Zyklus mindestens **5,000000 BTC produziert** (`cycleMinedMicro >= 5'000'000`), Strom/Kühl-Level jeweils ≥ 1 und insgesamt ≥ 2 installierte Racks |
| Kapazität | Von **2 auf 4 Rackflächen**; keine zusätzliche Map |
| Nutzwert | Bis zu 2 zusätzliche Racks; später je maximal 8 GPU-Slots; sichtbare grössere Garagenfläche und zwei markierte Pads |
| Rejoin | `garageLevel=1` bleibt samt gespeicherten Rack-Belegungen |
| Prestige | Rückkehr zu `garageLevel=0` und gratis Starter-Rack; alle alten gekauften Racks/GPU-Objekte werden gemäss Reset verworfen |

Ein neu gekauftes Rack wird *nicht* durch Ausbau gratis erzeugt. Platzbelegung vor der Erweiterung bleibt gültig. Die Voraussetzung zählt produzierte BTC, nicht die aktuell gehaltene BTC-Menge, damit häufiges Verkaufen keinen Nachteil erzeugt.

## 8. Drei automatische, wiederholbare Verträge

Das Terminal zeigt **genau diese drei Vertragstypen**. Sie sind beim Start aktiv, solange sie nicht im Cooldown sind; kein Zufalls-Reroll und keine Annahmekosten. Fortschritt zählt nur nach aktueller Aktivierung und nie während des Cooldowns. Nach Ende des Cooldowns beginnt ein neuer Durchlauf ab 0 **erst bei der nächsten gültigen Online-Aktion bzw. dem nächsten Mining-Tick**.

| Vertrag / ID | Exakte Zielbedingung | Credit-Reward | Cooldown **ab Abschluss** |
| --- | --- | ---: | ---: |
| Mining / `mine` | **300'000 µBTC = 0,300000 BTC** aus eigener Online-Produktion seit Start des Durchlaufs | **35 C** | **120 s** |
| Exchange / `exchange` | **600 C** kumulativ durch bestätigte BTC→Credits-Exchange-Transaktionen seit Start des Durchlaufs (ohne Questbelohnungen) | **60 C** | **180 s** |
| Effizienz / `efficiency` | **45 aufsummierte aktive Online-Sekunden** mit `effectiveH >= 100` **und** `powerFactor >= 0.95` **und** `coolFactor >= 0.95` | **80 C** | **300 s** |

Für die Effizienz-Aufgabe zählen nur reale, begrenzte Server-Tick-Dauern. Bei unzureichender Leistung pausiert der Zähler statt auf 0 zu fallen; so ist Fortschritt über Rejoins speicherbar. Negative oder unplausible Zeiten werden nie angerechnet. Prestige-Bonus zählt zur effektiven H-Anzeige, darf aber die Faktoren-/Zeitbedingungen nicht umgehen.

**Automatische Einmalbelohnung:** Bei Zielerreichung führt der Server innerhalb derselben gesperrten Profiltransaktion `reward Credits`, `completedOrdinal += 1`, `progress=0` und `cooldownUntil = serverUnixNow + cooldownSeconds` aus. Kein frei wiederholbarer Client-«Claim». Gleichzeitige Mining-, Verkaufs- und Cooldown-Ereignisse werden pro Spieler serialisiert. Ein bereits abgeschlossener `completedOrdinal` darf nie erneut entlohnt werden. Vor erneutem Aktivieren prüfen, ob der vorherige Abschluss gespeichert wurde; DOC-03 definiert DataStore-Commit/Retry und atomare Wiederaufnahme.

**Persistenz:** Pro Typ `progress`, `completedOrdinal` und `cooldownUntil` speichern. Online-Zeit wird bei Rejoin nicht nachgerechnet; abgelaufene Cooldowns dürfen bei Rejoin sofort enden. **Prestige:** Durchlauf-Fortschritt und Cooldowns werden zurückgesetzt, historische Abschlusszähler dürfen zu Anzeige-/Diagnosezwecken erhalten bleiben, sie geben aber keine neue Belohnung. Keine Abkürzung durch mehrfaches Abmelden.

**Economy-Grenze:** Mining-Reward entspricht 11,67 % seines Mindest-BTC-Äquivalents (`300 C`); Exchange-Reward 10 % der umgetauschten C; Effizienz bei minimal `100 H` über 45 s entspricht `450 C` Grundproduktion und damit 17,78 % Bonus. Unabhängige Cooldowns begrenzen die maximale Questbelohnung langfristig auf höchstens ungefähr `35/120 + 60/180 + 80/300 = 0,892 C/s` (theoretisches Überoptimierungs-Limit, keine garantierte Rate). Kein Quest-Reward zählt für den Exchange-Vertrag.

## 9. Prestige Lite (freiwillig, maximal fünf Durchläufe)

**Freischaltung je aktuellem Zyklus:** `prestigeCount < 5`, `cycleMinedMicro >= 300'000'000` (**300,000000 BTC** selbst produziert, nicht nur gehalten), `garageLevel=1`, Strom- und Kühl-Level jeweils **3**, mindestens eine **installierte T6**, sowie **60 aufsummierte qualifizierende Online-Sekunden** mit `effectiveH >= 1'000` seit Erfüllung der übrigen Bedingungen. Dieser Zeitnachweis wird persistiert, bei fallenden Anforderungen pausiert und beim nächsten Prestige auf 0 gesetzt; Offline-Zeit zählt nicht. Prestige benötigt keinen zusätzlichen Credit-Abzug, verbraucht aber den gesamten Zyklusfortschritt.

**Bonus:** Pro erfolgreichem Reset **+4 %** auf Rohleistung *nach* den Kapazitätsfaktoren (Formel Abschnitt 6), insgesamt höchstens **+20 %** bei `prestigeCount=5`. Keine dritte Währung, kein Bonus auf Vertragsbelohnung oder Preise und keine weiteren Prestige-Käufe. Ab Zähler 5 kein sechster Reset.

**Atomarer Reset nach expliziter Doppelbestätigung:**

| Wird zurückgesetzt | Bleibt erhalten |
| --- | --- |
| `credits=0`, `btcMicro=0`, `miningCarry=0` | `prestigeCount` (um exakt 1 erhöht, maximal 5) |
| Alle bisherigen GPUs und Racks, Rack-Slot-Referenzen und Inventare | Der daraus deterministisch berechnete permanente `prestigeFactor` |
| Neues gratis `r2_bench` mit **einer installierten `s1_sparrow`** | `tutorialCompleted` und erneut aufrufbare Hilfe |
| `powerLevel=0`, `coolingLevel=0`, `garageLevel=0` | Unverfängliche Lebenszeitstatistiken, sofern integer- und cap-sicher |
| `cycleMinedMicro=0`, Prestige-Zeitnachweis=0, Vertragsfortschritt und -Cooldowns=0 | Vertrags-Abschlusszähler nur als Historie, **ohne** erneuten Reward |

Prestige-Abbruch ändert nichts. Bestätigung ist an serverseitigen Profilstand und einmalige Request-ID gebunden; parallele Requests müssen auf exakt denselben Abschluss führen, nie auf zwei Bonusstufen. Nach absturzbedingtem Rejoin darf es weder ein halbes Inventar noch eine zweite Starter-GPU geben. Das erste Prestige ist ausdrücklich **kein Beta-Pflichtziel in den ersten 30 Minuten**.

## 10. Balancing- und Progressionsberechnung (Simulation, keine Playtests)

### Rechenprüfungen für den Anfang

- **Start:** `rawH=10, P=10, T=8`, Versorgung `40/32` → `effectiveH=10` → `1'000 µBTC/s = 0,001000 BTC/s = 1 C/s` Verkaufswert.
- **Zweite S1:** `55 C / 1 C/s = 55 s` bis zum finanzierbaren Kauf bei lückenlosem Mining, sofortigem manuellem BTC-Verkauf und ohne Bedienzeit. Zwei S1 liefern danach `20 H = 2 C/s`. Ein Spieler muss tatsächlich noch Exchange und Kauf/Einbau bedienen.
- **S1 + F2:** `rawH=42, P=38, T=34`, Startversorgung `40/32` → `powerFactor=1`, `coolFactor=32/34` → `effectiveH=39,52941176` → `3'952,941176 µBTC/s` vor µBTC-Abrundung. Die Kühlung bremst.
- **S1 + F2 + S1:** `rawH=52, P=48, T=42`, Startversorgung → `52 × (40/48) × (32/42) = 33,01587302 H`; **langsamer** als die S1+F2-Farm. Bei Strom-Level 1 + Kühl-Level 1 dagegen **52 H**. Damit sind Versorgungs-Upgrades wirtschaftlich relevant.
- **Null-Kühlung:** Eine S1 bei Strom `40 P` und Kühlung `0 T` liefert `10 × 1 × 0,5 = 5 H` bzw. `500 µBTC/s`. Bei Strom 0 liefert sie **0**.

### Zwei reproduzierbare Kauf-/Spiel-Szenarien

**A: sehr zügiges, optimistisches Modell.** Mining tickt genau jede Sekunde. Die Simulation verkauft BTC **modellhaft jede Sekunde** gebührenfrei, sobald ≥ 1 C umtauschbar ist; das ist *keine* automatische Exchange-Funktion des Spiels. Ein geplanter Kauf/Einbau erfolgt frühestmöglich auf dem nächsten vollen Sekunden-Tick. Keine Wege, Klick- oder Denkzeiten, Verträge, Boni, Offline-Erträge oder Robux. Kaufreihenfolge in der untenstehenden Tabelle.

**B: getaktete Bedienung.** Sonst identische Preise und Regeln, aber BTC-Verkauf und höchstens **eine** Kauf-/Einbau-Aktion je **15 Sekunden**; eine Installation benötigt damit den nächsten Handlungsslot. Keine Vertragsbelohnungen. Die 15 Sekunden sind nur eine Modellannahme für langsamere Interaktionen, kein vorgeschriebenes UI-Cooldown.

| Zeit | A: effektive H; C-Saldo; kumulativ BTC produziert | B: effektive H; C-Saldo; kumulativ BTC produziert |
| --- | --- | --- |
| **1 min** | **20 H; 9 C; 0,064000 BTC**, zweite S1 installiert | **10 H; 60 C; 0,060000 BTC**, zweite S1 ab Sekunde 60 kaufbar, Einbau bei Sekunde 75 |
| **5 min** | **52 H; 10 C; 0,840388 BTC**, zwei Versorgungsschritte, Rack, F2 und drei aktive GPUs | **39,53 H; 119 C; 0,759352 BTC**, Rack, F2 und Strom-Level 1 |
| **10 min** | **104 H; 530 C; 3,570388 BTC**, Strom/Kühlung auf Level 2, E3 aktiv | **104 H; 162 C; 3,202941 BTC**, Strom/Kühlung auf Level 2, E3 aktiv |
| **20 min** | **1'546,38 H; 18'905 C; 49,965080 BTC**, Garage ausgebaut, Max-Versorgung und 11 GPUs | **1'519,03 H; 7'727 C; 37,137405 BTC**, Garage ausgebaut, Max-Versorgung und 10 GPUs |
| **30 min** | **1'546,38 H; 111'687 C; 142,747782 BTC**, keine Käufe mehr nach ~18 min | **1'546,38 H; 98'819 C; 129,879083 BTC**, keine Käufe mehr nach ~21 min |

**Vorgegebene Kauf-/Einbaureihenfolge für A und B:** zweite S1 kaufen/installieren → F2 kaufen und eine S1 im Starter-Rack ersetzen (freie S1 im Inventar) → R4 kaufen/installieren → Strom 1 → Kühlung 1 → freie S1 installieren → E3 kaufen/installieren → Kühlung 2 → Strom 2 → B4 kaufen/installieren → V5 kaufen/installieren → Garage erweitern → R8 kaufen/installieren → V5 kaufen/installieren → Kühlung 3 → Strom 3 → T6 zweimal kaufen/installieren → V5 zweimal kaufen/installieren. Bei nicht ausreichendem Guthaben wird weiter gemint; gesperrte Ausbauten warten auf ihre Bedingungen. **Keine Vertrags-Credits** verwendet. Pro erfolgreich ausgeführtem Kauf/Einbau verstreicht in A ein Sekunden-Tick, in B ein 15-Sekunden-Handlungsslot. Alle angegebenen Saldi sind *nach Käufen*, BTC-Mikroreste unterhalb einer Credit-Verkaufseinheit sind nicht als C dargestellt.

**A-Kontrollpunkte:** Kauf S1 ~55 s; F2 ~148 s; R4 ~189 s; Strom 1 ~250 s; Kühlung 1 ~298 s; E3 ~374 s; Garage ~763 s; erste T6 ~1'021 s. In A wurden bis 30 min exakt **31'060 C** ausgegeben; `142,747782 BTC × 1'000 C/BTC = 142'747,782 C` umtauschbarer Gegenwert, davon `111'687 C` als ganzzahliger Credit-Saldo und `782 µBTC` Rest. Die Formeln erklären die Tabellenwerte; individuelle Bedienung und spätere Playtests werden davon abweichen.

**Kontrast ohne Reinvestition:** Nur eine S1 liefert nach 5 Minuten `0,300000 BTC` = **300 C** und nach 30 Minuten `1,800000 BTC` = **1'800 C**; Credits entstehen erst beim tatsächlichen Verkauf. Der Vergleich verdeutlicht, wie sich manuelles Investieren auswirkt, und ist keine Retention-Prognose.

**Designziele:** 0–60 s zweite GPU *finanzierbar*, 1–5 min bessere Farm, 5–10 min Strom/Kühlung/Rack-Entscheidungen, 10–20 min unterschiedliche GPU-Kombinationen, 20–30 min sichtbarer Ausbau; später Prestige. A zeigt technische Obergrenzen einer sehr effizient spielenden Person, nicht typische Geschwindigkeit. Bei echten 5–10-Personen-Playtests gemäss DOC-05 Kaufzeiten, Friktion und Versorgungsverständnis messen und **danach** Werte bei Bedarf dokumentiert nachstellen.

## 11. Deterministische Tests und Sicherheit

| Test-ID | Eingang / Aktion | Erwartung |
| --- | --- | --- |
| E01 | Ein Starter-GPU, Level 0/0, `delta=1`, Prestige 0 | `effectiveH=10`; `1'000 µBTC` Produktion |
| E02 | Zwei S1, Level 0/0, `delta=1` | `20 H`; `2'000 µBTC` |
| E03 | S1+F2, Level 0/0 | `39,52941176 H`; ca. `3'952,941176 µBTC/s`; bei frischem `miningCarry=0` nach 1 s **3'952 µBTC** und Rest `0,941176…` |
| E04 | S1+F2+S1, Level 0/0 | `33,01587302 H`; niedrigere Produktion als E03 |
| E05 | Dieselben 3 GPUs, Level 1/1 | `52 H`; `5'200 µBTC/s` |
| E06 | Keine GPU / 0 P / 0 T | 0 GPU → 0; 0 P → 0; nur 0 T → halbe strombereinigte H |
| E07 | `btcMicro=55'999`, `sellCredits=55` | Danach `999 µBTC` und `credits +=55` |
| E08 | `btcMicro=999`, Verkauf 1 C / Verkauf 0 / negativer Betrag / `NaN` | Sämtliche Anfragen **abgelehnt**, Saldo unverändert |
| E09 | Doppelter Kauf/Slot-/Exchange-Remote | Ein autorisierter Zustandswechsel; kein doppeltes Item / kein negativer Wert |
| E10 | 0,300000 BTC aktiver Mining-Vertragsfortschritt | Genau **35 C** einmal, `cooldownUntil=now+120` |
| E11 | Exchange aus Quest-Reward oder ausserhalb aktiven Durchlaufs | Kein Exchange-Quest-Fortschritt |
| E12 | `effectiveH=100`, Faktoren je 1, 44 zulässige Online-Sekunden | Noch kein Effizienz-Reward; nach Sekunde 45 genau **80 C** |
| E13 | Prestige bei `count=0`, 300 BTC Zyklus und allen Nachweisen | `count=1`, `prestigeFactor=1,04`, null Währungen, **ein** aktiver S1 auf Starter-Rack |
| E14 | Wiederholte identische Prestige-/Reward-Request-ID | Keine doppelte Erhöhung, keine doppelten C, keine weiteren Starter-Items |
| E15 | Überschreiten Geld-/Inventar-/Rack-/Tiergrenze | Kein Überlauf, keine Teilbuchung; definierter Fehler |
| E16 | Rejoin mit gespeicherten positiven Saldi/Slots/Quest/Cooldown | Exakt wiederherstellen, **keine** BTC-Nachvergütung; Offline-Cooldown darf ablaufen |
| E17 | Unbekanntes GPU-/Rack-Modell oder falsche Item-ID / fremder Plot | Keine Änderung des autoritativen Zustands |
| E18 | `prestigeCount=5` | Bonus `1,20`; weiterer Reset abgelehnt |

### Feste Grenzen und Transaktionsinvarianten

- **Serverkonfiguration:** Exakt sechs GPU-IDs, drei Rack-IDs, Preise und Leistungswerte als endliche positive Integer; Slot-Zahlen positive Integer; Tier-Arrays strikt aufsteigend, Tierpreise positiv. Ungültige Serverkonfiguration **verhindert Start des Economy-Service**.
- **Profil-/Geldgrenzen:** `0 <= credits <= 2'000'000'000`, `0 <= btcMicro <= 1'000'000'000'000`, `0 <= cycleMinedMicro <= 1'000'000'000'000'000`; `prestigeCount` ganzzahlig `0..5`; `powerLevel`/`coolingLevel` ganzzahlig `0..3`; `garageLevel` `0..1`. Zähler bei Höchstgrenzen nicht überlaufen lassen. Alle Ganzzahlen bleiben unter JavaScript-/Luau-Double-Integergrenze `2^53-1`.
- **Exchange:** Pro Request `1 <= sellCredits <= 10'000'000`; Produkt `sellCredits * 1'000` auf Überlauf und BTC-Deckung prüfen, Credit-Maximum vor Addition prüfen. Menge **nie** dem Client glauben; nur die gewünschte ganzzahlige Anzahl C annehmen, Preise/Raten serverseitig berechnen.
- **Inventar:** Höchstens 40 GPU-Items, 8 Rack-Items, vier belegte Rackflächen und 26 aktive GPU-Slots; Rack/GPU-Item-IDs pro Spieler eindeutig; Item in höchstens einem Slot. Lager/Einbau/Erweiterung vor Geldabzug validieren, bei Fehlschlag keine Teilbuchung.
- **Kauf-/Upgrade-Transaktionen:** Server prüft gültige ID, Eigentümer, Version, Freischaltung, freien Bestand/Limits und gesamten Saldo; serieller Mutations-Lock pro Profil. Ein Kauf führt **genau einen** Credit-Abzug und **genau ein** Item oder Tier-Update aus. Bei Speicherausfall kein erfolgreiches Ergebnis vortäuschen; genaue Recovery-Semantik in DOC-03.
- **Mining:** Nur gültiger geladener Profilzustand, aktive Serversitzung und gemessene Tickdauer; keine vom Client gesendeten BTC-/H-Werte. Ertragsaddition und Zähleraddition gegen Höchstgrenzen prüfen, auch bei Prestige und Verträgen. UX zeigt «Limit erreicht» statt Wraparound.
- **Datenqualität:** `NaN`, ±Infinity, negative, gebrochene, fehlende oder sonst ungültige Eingaben verwerfen. Defekte persistierte Profile dürfen nicht unbemerkt in einen «neuen» Account überschrieben werden; sichere Behandlung/Recovery/Migration in DOC-03.
- **Cooldown- und Prestige-Replay:** Zustandsänderung plus Reward bzw. Reset als eine idempotente Profiloperation; Zeitstempel vom Server; jede Request-ID je Aktion nur einmal wirksam. Auftrags-/Prestige-Werte nie aus Client-Behauptungen übernehmen.
- **Rundungsinvariante:** Erzeugte µBTC nie aus angezeigten, gerundeten H-Werten ableiten. Ein validierter tickbasierter Rechentest darf wegen Floating-Point-Rest höchstens **1 µBTC** vom mathematisch ungerundeten Referenzwert abweichen, nicht systematisch mehr. Credits bleiben **exakt**.

## 12. Zentrale Konfigurationsfelder und Übergaben

Diese Namen sind der **fachliche Konfigurationsvertrag**, keine fertig implementierten Luau-Dateien.

| Gruppe | Felder |
| --- | --- |
| `GPUConfig` | `models[id]={displayName, priceCredits, rawHash, powerUnits, heatUnits}` |
| `RackConfig` | `models[id]={displayName, priceCredits, slotCount, minGarageLevel, minPowerLevel, minCoolingLevel}`; `starterRackId` |
| `EconomyConfig` | `microBtcPerBtc=1000000`, `creditsPerBtc=1000`, `microBtcPerCredit=1000`, `microBtcPerHashSecond=100`, `maxCredits`, `maxBtcMicro`, `maxCounterMicro`, `maxExchangeCredits`, `maxOwnedGpus=40`, `maxOwnedRacks=8`, `maxInstalledRacks=4`, `maxTickSeconds=5` |
| `UpgradeConfig` | `powerCapacityByLevel=[40,120,350,1200]`, `powerNextCost=[240,1000,5000]`, `coolingCapacityByLevel=[32,100,290,1000]`, `coolingNextCost=[190,820,4250]` |
| `PlotConfig` | `rackPadsByGarageLevel=[2,4]`, `garageExpandPrice=3000`, `garageMinCycleMinedMicro=5000000`, `garageMinPowerLevel=1`, `garageMinCoolingLevel=1`, `garageMinInstalledRacks=2` |
| `ContractConfig` | `mine={targetMicro:300000,rewardCredits:35,cooldownSeconds:120}`; `exchange={targetCredits:600,rewardCredits:60,cooldownSeconds:180}`; `efficiency={minEffectiveHash:100,minPowerFactor:0.95,minCoolFactor:0.95,targetOnlineSeconds:45,rewardCredits:80,cooldownSeconds:300}` |
| `PrestigeConfig` | `maxCount=5`, `bonusPerCount=0.04`, `minCycleMinedMicro=300000000`, `minGarageLevel=1`, `minPowerLevel=3`, `minCoolingLevel=3`, `requiredInstalledGpuId="t6_titan"`, `minEffectiveHash=1000`, `targetEligibleOnlineSeconds=60` |
| `StarterConfig` | `credits=0`, `btcMicro=0`, `gpuId="s1_sparrow"`, `rackId="r2_bench"`, `gpuSlot=1`, `powerLevel=0`, `coolingLevel=0`, `garageLevel=0` |

**DOC-03 / Issue #3:** Schema der Item-/Request-IDs, Tick-Accumulator-Persistenz, Profile-Session-Locks, Recovery nach nicht bestätigtem Save, idempotente Quest-/Prestige-Buchung, integerbasierte Guards und sichere Remote-Verträge technisch festlegen. Keine Architekturentscheidung darf die hier dokumentierte Rechenfolge ändern.

**DOC-04 / Issue #4:** Visualisierung der zwei Starter-Rackflächen und zwei zusätzlichen Pads, eindeutige Kapazitäts- und prognostizierte Hashrate-Anzeigen, BTC-Verkauf in ganzen C/«Max», Preis-/Saldo-Fehler, Rack-Slot-Interaktion, Prestige-Doppelbestätigung und reine Spielwährungskennzeichnung.

**DOC-05 / Issue #5:** E01–E18 als Testfälle übernehmen; Playtests für die tatsächlich gemessene Zeit bis zur zweiten GPU, 5-/30-Minuten-Fortschritt, Rejoin, gleichzeitige Interaktionen, 6 Spieler, Mobilgerät und Prestige. Balancing-Werte erst anhand protokollierter Befunde bewusst ändern.

**Studio-Arbeit:** Spätere Luau-Umsetzung ausschliesslich durch Claude Code direkt im **korrekt verifizierten Roblox-Studio-Place über MCP**. Kein Rojo, keine GitHub-Code-Synchronisation durch Claude. Dieses Dokument und Issues/PRs liegen bei ChatGPT. **Nächster fachlicher Schritt nach DOC-02: DOC-03 (#3), nach Merge von DOC-01 und DOC-02.**

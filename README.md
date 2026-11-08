# PluginPrism ABA-Prüfer

**Rückführungen in Logikplänen des ABB KNX Logik Controller ABA/S 1.2.1 finden**
· *Find feedback loops in logic plans of the ABB KNX Logic Controller ABA/S 1.2.1* ([English below](#english))

**[⬇ Download – neueste Version / latest version](../../releases/latest)** · Windows 10/11, 64 Bit, eine einzelne Datei, keine Installation

---

## Deutsch

Der Logik-Controller ABA/S 1.2.1 berechnet die Logik zyklisch von den Eingängen zu den Ausgängen und kennt keine
Schleifen (ABB-Produkthandbuch ABA/S 1.2.1, Abschnitt 7.8). Eine **Rückführung** – ein Ausgang, der über einen oder
mehrere Bausteine wieder auf einen eigenen Eingang wirkt – kann im Editor und in der Simulation funktionieren, in der
Praxis aber unzuverlässig sein.

Der ABA-Prüfer liest einen Logikplan-Export (`.xml`) oder einen exportierten Funktionsblock (`.fbxml`) und zeigt

- wie viele Rückführungen es gibt,
- welche Bausteine daran beteiligt sind (mit Name, bei KNX IN/OUT mit Objektnummer),
- wo sie liegen: Arbeitsblatt, Bereich des Blatts (z. B. „unten Mitte“), der nächste Baustein mit eigenem Namen und
  die Position (X/Y) im Logik-Editor,
- auch Rückführungen im Inhalt von Funktionsblöcken – mit den Arbeitsblättern, auf denen der Funktionsblock steht.

Der Prüfer **liest nur**; die geprüfte Datei wird nicht verändert.

### Bedienung

1. `ABA-Pruefer-<Version>.zip` aus den [Releases](../../releases/latest) laden und entpacken.
2. Die Logikplan-Datei (Export aus dem Logik-Editor des ABA/S 1.2.1) oder einen exportierten Funktionsblock auf
   `ABA-Pruefer.exe` ziehen – oder das Programm starten, die Datei ins Fenster ziehen und Enter drücken.
3. Ergebnis: **KEINE RÜCKFÜHRUNG** (grün) oder je Rückführung ein Steckbrief (rot). `[S]` speichert den Bericht als
   `<Name>_Rueckfuehrungen.txt` neben der Datei. `[L]` wechselt die Sprache (Deutsch/Englisch).

Abhilfe bei einer Rückführung: Speicher und Selbsthaltung mit einem RS-FF bauen, statt einen Ausgang zurückzuführen.

**Konsole und Skripte:** `ABA-Pruefer.exe [--de | --en] <Datei> [<Datei> ...]` – Rückgabewert 0 = keine Rückführung,
1 = mindestens eine Rückführung, 2 = Datei nicht lesbar bzw. kein Logikplan/Funktionsblock des ABA/S 1.2.1 (bei
mehreren Dateien der höchste Wert).

**Grenzen:** Geprüft werden nur Rückführungen, keine anderen Planungsfehler; nur Logikpläne und Funktionsblöcke des
ABA/S 1.2.1, geprüft mit dem Dateiformat Version 2.

Die ausführliche Anleitung liegt dem Download bei (`LIESMICH.txt`).

**Windows SmartScreen:** Die exe ist nicht signiert. Beim ersten Start kann Windows warnen („Weitere Informationen“ →
„Trotzdem ausführen“). Die Prüfsumme (SHA-256) jeder Datei steht beim jeweiligen Release.

---

## English

The ABA/S 1.2.1 logic controller calculates the logic cyclically from the inputs to the outputs and has no loop
capability (ABB product manual ABA/S 1.2.1, section 7.8). A **feedback loop** – an output that acts on one of its own
inputs through one or more elements – may work in the editor and in the simulation, but behave unreliably in practice.

The ABA Checker reads a logic plan export (`.xml`) or an exported function block (`.fbxml`) and shows how many
feedback loops there are, which elements are involved (with name; KNX IN/OUT with object number), and where they are
(worksheet, area of the sheet, nearest named element, X/Y position in the logic editor) – including loops inside
function blocks. It only reads; the file is not modified.

**Usage:** download `ABA-Pruefer-<version>.zip` from the [releases](../../releases/latest), unzip, drag the logic plan
or function block file onto `ABA-Pruefer.exe` (or start it and drag the file into the window). `[S]` saves the report,
`[L]` switches the language. Command line: `ABA-Pruefer.exe [--de | --en] <file> ...`, exit code 0 = no loop,
1 = loop found, 2 = file not readable. Full manual: `README.txt` in the download.

**Windows SmartScreen:** the exe is not signed; Windows may warn on first start („More info“ → „Run anyway“). The
SHA-256 checksum of each file is listed with its release.

---

## Lizenz / License

© 2026 Jan Tenbrock – Freeware. Kostenlos nutzbar, auch gewerblich; Weitergabe nur unverändert und unentgeltlich;
ohne Gewähr. *Free to use, including commercial use; redistribution only unmodified and free of charge; provided
“as is”.* Details: [LICENSE.txt](LICENSE.txt).

ABB ist eine Marke der ABB. Dieses Programm ist kein Produkt der ABB. · *ABB is a trademark of ABB. This program is
not a product of ABB.*

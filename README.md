# Omni Spotlight Cockpit

KI-Cockpit mit orchestrierten Agenten für die **Omni Spotlight GmbH**.
Zwei Geschäftslinien werden langfristig unterstützt: DOOH-Spot-Kampagnen (Produkt A) und Active Sourcing für akademisches Recruiting (Produkt B).

**Aktueller Fokus:** Agent 1 (Anonymisierungs- und Ranking-Agent) und Agent 3 (Stellenprofil- und Filter-Agent) — beide aus Produkt B.

## Workspace-Struktur

| Pfad | Zweck |
|---|---|
| `README.md` | Dieses Dokument — Einstieg |
| `CLAUDE.md` | Persistente Anweisungen für Claude in jeder Session |
| `PROJECT_STATE.md` | **Lebende Datei.** Wo stehen wir gerade? |
| `DECISIONS.md` | Append-only Log architektonischer Entscheidungen |
| `OPEN_QUESTIONS.md` | Offene Fragen an Kunden und intern |
| `docs/` | Vom Kunden gelieferte Dokumente (PDF-Briefing, Excel-Plan) |
| `customer-data/` | Echte Daten vom Kunden, gegliedert pro Agent |
| `agents/` | Pro Agent: Spec, Prompts (versioniert), Examples, Eval-Suite |
| `code/` | Tatsächlicher Code (initial leer) |
| `session-log/` | Eine Datei pro Arbeits-Session |

## Session-Start

1. In den Projektordner wechseln: `cd ~/Desktop/omni-spotlight-cockpit`
2. Claude startet automatisch und liest `CLAUDE.md`
3. Erste Frage an Claude: *"Lies PROJECT_STATE.md und sag mir wo wir stehen."*

## Session-Ende

1. `PROJECT_STATE.md` aktualisieren
2. Neue Entscheidungen in `DECISIONS.md` ergänzen
3. Neue offene/beantwortete Fragen in `OPEN_QUESTIONS.md` pflegen
4. `session-log/YYYY-MM-DD-session-NN.md` mit 5–10 Zeilen Zusammenfassung anlegen
5. `git add -A && git commit -m "..."` mit aussagekräftiger Message

## Drei-Schichten-Gedächtnis

| Schicht | Was darin steht |
|---|---|
| **Repo-Dateien** (hier) | Quelle der Wahrheit. Vom User kuratiert. |
| **Auto-Memory** (`~/.claude/projects/.../memory/`) | User-Präferenzen, Feedback-Regeln, Projekt-Fakten |
| **claude-mem** (lokal, http://localhost:37701) | Passive Beobachtungen aus jeder Session |

**Konfliktregel:** Bei Widersprüchen gilt das Repo > Auto-Memory > claude-mem.

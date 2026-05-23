# Projekt-Stand

> Diese Datei wird **am Ende jeder Session** aktualisiert. Sie ist der Anker für die nächste Session.

**Letztes Update:** 2026-05-23

---

## Aktueller Stand (Zusammenfassung)

Projekt-Workspace ist eingerichtet. Kunde Omni Spotlight ist gewonnen. Wir konzentrieren uns auf den Bau von **Agent 1 (Anonymisierung & Ranking)** und **Agent 3 (Stellenprofil & Filter)** — beide aus Produkt B. Beide Agenten sind in **Phase 0 — Discovery**: wir warten auf Daten und Inputs vom Kunden.

## Letzte Aktion

**2026-05-23:** Workspace `~/Projects/omni-spotlight-cockpit/` angelegt mit vollständiger Folder-Struktur, Status-Dateien (`README`, `CLAUDE`, `PROJECT_STATE`, `DECISIONS`, `OPEN_QUESTIONS`), Initial-Git-Commit, **Push auf GitHub (privates Repo: maximiliankauffmann-cpu/omni-spotlight-cockpit)**. claude-mem installiert und als LaunchAgent dauerhaft laufend. **Setup-Phase abgeschlossen.**

## Nächste konkrete Aktion

1. **Excel-Tabelle "Daten Agent 1 und 3"** aus `docs/00_Projektplan.xlsx` als Bring-Liste an den Kunden senden (per Mail mit Begleittext).
2. Sobald die ersten kritischen Inputs eintreffen (siehe `OPEN_QUESTIONS.md`): `customer-data/agent-1-anonymisierung/` und `customer-data/agent-3-stellenprofil/` befüllen.

## Blocker

- **API-Zugang zur Kandidaten-DB** muss vom externen IT-Freelancer bereitgestellt werden (kritisch für beide Agenten)
- **Beispiel-Outputs aus heutiger manueller Praxis** muss der Auftraggeber selbst zusammenstellen (kritisch für Agent 1)
- **5–10 echte Stellenprofile** muss Operations zusammenstellen (kritisch für Agent 3)

## Status pro Agent

| Agent | Phase | Notiz |
|---|---|---|
| **Agent 1 — Anonymisierung & Ranking** | 0 — Discovery | Heute schon manuell mit Claude gemacht. Beispiel-Outputs aus dieser Praxis sind die wichtigste Trainingsquelle. |
| **Agent 3 — Stellenprofil & Filter** | 0 — Discovery | API-Schema der Kandidaten-DB ist die Schlüsselabhängigkeit. |

**Phasen-Definition:** 0 Discovery → 1 Spec → 2 Build → 3 Eval → 4 Pilot → 5 Done (für Standalone-Stufe).

## Wo zu finden, wenn du dich wieder einarbeiten musst

- **Was ist das Projekt überhaupt?** → `docs/01_PROJECT_BRIEFING_v3.pdf`
- **Was wurde bisher entschieden?** → `DECISIONS.md`
- **Was fehlt mir noch vom Kunden?** → `OPEN_QUESTIONS.md`
- **Was ist in der letzten Session passiert?** → neuester Eintrag in `session-log/`

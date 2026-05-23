# Agent 1 — Anonymisierungs- und Ranking-Agent

> **Status:** Phase 0 — Discovery. Diese Spec ist ein Stub; wird in Phase 1 vervollständigt, sobald Kundeninputs vorliegen.

## Zweck

Wandelt Roh-Kandidatendaten aus der externen Kandidaten-DB in eine **anonymisierte, gerankte Vorauswahl** um, die der Endkunde erhält.

Wird heute manuell mit Claude erledigt. Diese Spec produktionisiert die existierende Praxis.

## Input (vorläufig — präzisieren wenn API-Schema da ist)

- Roh-Datensatz: JSON-Array von Kandidatenprofilen aus der Kandidaten-DB
- Stellenprofil-Kontext (vom Agent 3 oder direkt)
- Bewertungsraster (statisch oder pro Mandat überschrieben)

## Output (vorläufig)

Strukturiertes Dokument (Format-Vorgabe siehe `OPEN_QUESTIONS.md`):

- Pro Kandidat: Match-Score, anonymisierter Lebenslauf, kurze Begründung
- Sortiert nach Match-Score absteigend
- Reproduzierbar (gleicher Input → gleicher Output, idealerweise)

## Verhalten

- **Anonymisieren:** Namen, exakte Adressen, frühere Arbeitgebernamen entfernen oder abstrahieren (Regeln siehe `customer-data/agent-1-anonymisierung/`)
- **Ranken:** nach Bewertungsraster (siehe `customer-data/agent-1-anonymisierung/`)
- **Begründen:** pro Kandidat 1–2 Sätze, warum dieser Score
- **Niemals halluzinieren:** wenn ein Feld fehlt, ehrlich als "unbekannt" markieren statt zu raten

## Akzeptanzkriterien (für Phase 3 Eval)

- Output für identischen Input ist deterministisch reproduzierbar (innerhalb der LLM-Toleranz)
- Anonymisierung ist vollständig (manueller Review der Eval-Outputs zeigt kein PII)
- Match-Score-Verteilung ist plausibel (nicht alle Kandidaten 90+, nicht alle 30-)
- Format entspricht der vom Kunden gewünschten Vorlage

## Abhängigkeiten

- Kandidaten-DB-API (für Input-Format)
- Anonymisierungs- und Ranking-Regeln (vom Kunden)
- Beispiel-Outputs aus heutiger manueller Praxis (vom Kunden)

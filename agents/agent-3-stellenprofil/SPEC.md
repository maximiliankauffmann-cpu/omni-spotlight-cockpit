# Agent 3 — Stellenprofil- und Filter-Agent

> **Status:** Phase 0 — Discovery. Diese Spec ist ein Stub; wird in Phase 1 vervollständigt, sobald Kundeninputs vorliegen.

## Zweck

Wandelt ein rohes **Stellenprofil** (vom Kunden geliefert oder im Cockpit erfasst) in einen **strukturierten Filtersatz** um, der gegen die externe Kandidaten-DB-API ausgeführt werden kann.

Bildet die manuelle Faustregel ab, die heute schon im Team gelebt wird: aktuelle, jobverwandte Titel + Regionalfilter (PLZ + Umkreis) liefern eine brauchbare Grobeinschätzung.

## Input (vorläufig)

- Rohes Stellenprofil (Freitext, ggf. PDF-Auszug, ggf. vom Kunden formuliert)
- Standortangabe (Stadt, Region oder Adresse)
- Senioritäts-Hinweis (optional, oft im Profiltext)

## Output (vorläufig)

JSON-Objekt mit Filter-Kriterien, kompatibel zum API-Schema der Kandidaten-DB:

```json
{
  "job_titles": ["Senior Data Scientist", "Lead Data Scientist", "Principal Data Scientist"],
  "location": { "plz": "80331", "radius_km": 30 },
  "seniority_years_min": 5,
  "must_have_skills": ["Python", "Machine Learning"],
  "reasoning": "Kurze Begründung der Ableitung für den menschlichen Reviewer"
}
```

## Verhalten

- **Titel-Erweiterung:** Aus einem Titel verwandte ableiten (z.B. "Senior X" → "Lead X", "Principal X")
- **PLZ-Logik:** Standortbeschreibung in PLZ + Umkreis übersetzen (Regeln siehe `customer-data/agent-3-stellenprofil/`)
- **Seniority-Mapping:** Junior/Senior/Lead/... in Berufsjahre und Filter-Werte übersetzen
- **Reasoning mitliefern:** Jeder Filter-Wert ist nachvollziehbar
- **Human-in-the-Loop:** Output ist ein Vorschlag, Mensch gibt frei, bevor API-Call läuft

## Akzeptanzkriterien (für Phase 3 Eval)

- Für 5–10 echte Stellenprofile (Eval-Set) erzeugt der Agent Filter, die ein erfahrener Mitarbeiter so oder sehr ähnlich abgeleitet hätte
- Edge-Cases werden sauber behandelt: vager Standort, ungewöhnlicher Titel, fehlende Seniority
- Filter sind **vollständig** im Sinne des API-Schemas (kein Feld vergessen, das die API verlangt)

## Abhängigkeiten

- API-Schema der Kandidaten-DB (definiert das Output-JSON)
- Regionalregeln (vom Kunden)
- Seniority- und Titel-Mapping (vom Kunden)
- 5–10 echte Stellenprofile als Eval-Set (vom Kunden)

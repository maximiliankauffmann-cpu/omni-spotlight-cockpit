# Anweisungen für Claude in diesem Projekt

Diese Datei wird in **jeder** Claude-Code-Session in diesem Ordner automatisch geladen. Sie ist der dauerhafte Kontext.

## Projekt-Kontext (statisch)

- **Kunde:** Omni Spotlight GmbH
- **Auftrag:** KI-Cockpit + orchestrierte Agenten als operative Produktionsschicht über bestehenden Workflows
- **Zwei Geschäftslinien:**
  - **Produkt A:** DOOH-Spot-Kampagnen für Arbeitgeber an Hochschulen
  - **Produkt B:** Active Sourcing für akademische Recruiting-Mandate
- **Aktueller Fokus:** Agent 1 und Agent 3 (beide Produkt B). Cockpit-Bau erst später.

## Tech-Stack (festgelegt)

- **Frontend:** Next.js, gehostet auf Vercel
- **Datenbank + Auth + Storage:** Supabase (EU-Region, DSGVO-konform)
- **KI-Modell:** Claude API (Anthropic) für alle Text-Agenten, Claude Vision für Bildanalyse
- **E-Mail-Versand:** Resend
- **LLM-Monitoring:** Helicone
- **Fehler-Monitoring:** Sentry
- **Bestehende Systeme (bleiben):** Close (CRM, Source of Truth Vertrieb), n8n (Workflow-Glue), externe Kandidaten-DB (vom IT-Freelancer betreut)

## Sprach- und Kommunikationsregeln

- **Kommunikation mit User:** Deutsch (User bevorzugt Deutsch im gesamten Projekt)
- **Code, Variablen, Commits:** Englisch (Standardkonvention)
- **Tabellen und Dokumente intern:** Deutsch
- **Tonalität:** sachlich, präzise, ohne Floskeln. Keine Emojis ungefragt.

## Code- und Commit-Konventionen

- Commits auf Englisch, im Conventional-Commits-Stil (z.B. `feat: add filter agent prompt v2`)
- Pro Agent eine versionierte Prompt-Datei (`prompts/v1.md`, `prompts/v2.md`, ...) — alte Versionen behalten
- Eval-Outputs nicht in Git committen, wenn sie personenbezogene Daten enthalten

## Workflow-Erwartungen

1. **Bei jedem Session-Start:** Lies `PROJECT_STATE.md` und fasse den Stand in 3 Sätzen zusammen.
2. **Bei Entscheidungen mit Tragweite:** Schreibe sie unaufgefordert in `DECISIONS.md`.
3. **Bei Fragen an den Kunden:** Trage sie in `OPEN_QUESTIONS.md` ein, statt sie nur mündlich zu äußern.
4. **Bei jedem Session-Ende:** Aktualisiere `PROJECT_STATE.md` und erzeuge `session-log/YYYY-MM-DD-session-NN.md`.

## User-Profil

- User ist Geschäftsführer von Omni Spotlight GmbH (Auftraggeber, nicht externer Entwickler)
- Hat begrenzte Entwicklungserfahrung — erkläre technische Konzepte ohne Fachjargon
- Code wird im Pair-Programming-Modus User + Claude geschrieben
- Validierte Faustregel aus heutiger Praxis: aktuelle Jobtitel + Regionalfilter (PLZ + Umkreis) liefern brauchbare Sourcing-Vorauswahlen
- User produziert Agent-1-Outputs heute schon manuell mit Claude — Agent 1 ist also bereits validiert, nur nicht produktionisiert

## Verweise

- Quelldokument für alle Anforderungen: `docs/01_PROJECT_BRIEFING_v3.pdf`
- Aktueller Projektplan (5 Sheets): `docs/00_Projektplan.xlsx`
- Aktueller Stand der Arbeit: `PROJECT_STATE.md`

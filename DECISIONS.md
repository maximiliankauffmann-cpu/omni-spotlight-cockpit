# Entscheidungs-Log

Append-only. Pro Eintrag: Datum, Entscheidung, Begründung, verworfene Alternativen.
Neueste Einträge oben.

---

## 2026-05-24 — Workspace auf den Schreibtisch verschoben

**Entscheidung:** Projekt-Workspace von `~/Projects/omni-spotlight-cockpit/` nach `~/Desktop/omni-spotlight-cockpit/` verschoben. Git-Historie und GitHub-Remote bleiben unverändert.

**Begründung:** Bessere Zugänglichkeit im Alltag — der User hat den Schreibtisch ohnehin geöffnet und greift schneller darauf zu. Der ursprüngliche Grund für `~/Projects/` (saubere Trennung vom unstrukturierten alten Desktop-Ordner) gilt weiter, weil der neue Workspace einen eigenen, eindeutigen Namen hat und nicht in Konflikt mit dem alten Archiv-Ordner steht.

**Verworfen:** Im `~/Projects/`-Pfad belassen (weniger zugänglich); Symlink zum Desktop legen (zusätzliche Komplexität ohne klaren Vorteil).

---

## 2026-05-23 — Multi-Session-Projektstruktur eingeführt

**Entscheidung:** Eigener Workspace unter `~/Projects/omni-spotlight-cockpit/` mit Status-Dateien (PROJECT_STATE, DECISIONS, OPEN_QUESTIONS, CLAUDE.md), per-Agent-Ordnern und Session-Logs. Lokales Git + privates GitHub-Repo.

**Begründung:** Projekt zieht sich über Wochen bis Monate. Ohne strukturierten Workspace würde Claude in jeder Session denselben Kontext neu aufbauen müssen — was zu Halluzinationen und Inkonsistenzen führt. Drei-Schichten-Gedächtnis (Repo > Auto-Memory > claude-mem) stellt sicher, dass nichts verlorengeht.

**Verworfen:** Im bestehenden Desktop-Ordner weiterarbeiten (zu unstrukturiert); reines claude-mem (zu passiv, keine explizite User-Kuratierung).

---

## 2026-05-23 — claude-mem installiert und als LaunchAgent dauerhaft aktiv

**Entscheidung:** claude-mem v13.3.0 als Community-Plugin via `npx claude-mem install`. macOS-LaunchAgent (`com.claude-mem.worker.plist`) gestartet mit RunAtLoad + KeepAlive bei Crash. Logs in `~/Library/Logs/claude-mem/`.

**Begründung:** Passive Cross-Session-Erinnerung ohne User-Aufwand. Worker läuft dauerhaft, startet bei Login.

**Verworfen:** Manueller Start vor jeder Session (Reibung); cloud-basierte Memory-Lösung (Datenschutz, Abhängigkeit).

---

## 2026-05-22 — Fokus auf Agent 1 und Agent 3 als Erstes

**Entscheidung:** Nach Kundengespräch wird zuerst nur Agent 1 (Anonymisierungs- und Ranking-Agent) und Agent 3 (Stellenprofil- und Filter-Agent) gebaut. Beide aus Produkt B.

**Begründung:** Agent 1 wird heute schon manuell mit Claude durchgeführt — produktionsreif zu validieren ist also schnell. Agent 3 schließt mit Agent 1 den ersten Halb-Funnel für Active Sourcing (Stellenprofil → Filter → DB-Query → Anonymisierung). Sofortiger Mehrwert beim Kunden, geringes Risiko.

**Verworfen:** Mit dem Cockpit zu beginnen (würde Wochen ohne Mehrwert bedeuten); alle 10 Agenten parallel zu spec'en (zu viel Aufwand vor erster Validierung).

---

## 2026-05 — Tech-Stack festgelegt

**Entscheidung:**
- Frontend/App: **Next.js** auf **Vercel**
- Datenbank + Auth + Storage: **Supabase** (EU-Region)
- KI-Modelle: **Claude API** für Text, **Claude Vision** für Bildanalyse
- Mail-Versand: **Resend**
- LLM-Monitoring: **Helicone**
- Fehler-Monitoring: **Sentry**
- Bestehende Systeme bleiben unverändert: **Close** (CRM), **n8n**, externe **Kandidaten-DB**

**Begründung:**
- Next.js + Vercel: Standardstack, schnelles Deployment, keine Eigenentwicklung der Infrastruktur sinnvoll
- Supabase: vereint DB/Auth/Storage, DSGVO-konformes EU-Hosting
- Claude API: bereits Teil der manuellen Praxis (Agent 1 wird heute mit Claude erledigt) — Konsistenz und Modellqualität
- Bestehende Systeme erhalten: explizite Vorgabe aus dem Briefing-Dokument

**Verworfen:**
- OpenAI als Hauptmodell (User arbeitet bereits produktiv mit Claude; Wechsel würde Re-Validierung erfordern)
- Eigener Server-Stack (würde monatelange Infrastruktur-Arbeit ohne Geschäftswert bedeuten)
- Ablösung von Close-CRM (Anti-Scope laut Briefing)

---

## 2026-05 — Workspace-Strategie: kompletter Neustart statt Erweiterung

**Entscheidung:** Neuer, sauberer Projektordner unter `~/Projects/omni-spotlight-cockpit/` statt Weiterarbeit im Desktop-Ordner.

**Begründung:** Der Desktop-Ordner enthält veraltete Drafts (z.B. zwei Versionen der Excel-Datei, Lock-Dateien). Ein sauberer Workspace mit nur den relevanten Artefakten reduziert kognitive Last und Fehlerquellen.

**Verworfen:** Im bestehenden Desktop-Ordner bleiben (zu viel Rauschen).

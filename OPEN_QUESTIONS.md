# Offene Fragen und ausstehende Inputs

Live-Liste. Wenn beantwortet: Status auf "beantwortet" setzen und Antwort kurz festhalten. Bei Erledigung später nach `archive` verschieben.

**Konvention:**
- 🔴 **Kritisch** — ohne dies können wir den Agenten nicht starten
- 🟡 **Wichtig** — verzögert den Build, aber nicht blockierend
- ⚪ **Klärung** — interne Klärung, Kunde nicht zwingend nötig

---

## Für Agent 1 — Anonymisierungs- und Ranking-Agent

### 🔴 1. API-Zugang und Doku der Kandidaten-DB
- **Was genau:** API-Key, Endpoint-URL, Authentifizierungsmethode, Rate-Limits, Schema-Dokumentation (welche Felder, welche Filter, welches Antwortformat)
- **Wer beim Kunden:** externer IT-Freelancer
- **Gestellt am:** —
- **Status:** offen
- **Antwort:** —

### 🔴 2. Beispiel-Outputs aus heutiger manueller Praxis
- **Was genau:** 5–10 anonymisierte Vorauswahlen, die heute schon mit Claude produziert wurden — als Trainingsmaterial
- **Wer beim Kunden:** Auftraggeber selbst
- **Gestellt am:** —
- **Status:** offen
- **Antwort:** —

### 🔴 3. Anonymisierungsregeln
- **Was genau:** Was wird entfernt (Namen, exakte Adressen, frühere Arbeitgeber)? Was bleibt (Berufserfahrung, Skills, PLZ-Region)?
- **Wer beim Kunden:** Auftraggeber / Operations
- **Gestellt am:** —
- **Status:** offen
- **Antwort:** —

### 🔴 4. Bewertungsraster für Ranking
- **Was genau:** Match-Score-Kriterien, Gewichtung, Match-Begründung pro Kandidat
- **Wer beim Kunden:** Auftraggeber / Operations
- **Gestellt am:** —
- **Status:** offen
- **Antwort:** —

### 🟡 5. Format-Vorgabe für das Ergebnisdokument
- **Was genau:** Wie sieht die finale Vorauswahl an den Endkunden aus (PDF, Tabelle, Struktur pro Kandidat)?
- **Wer beim Kunden:** Auftraggeber / Operations
- **Gestellt am:** —
- **Status:** offen
- **Antwort:** —

---

## Für Agent 3 — Stellenprofil- und Filter-Agent

### 🔴 1. API-Zugang und Doku der Kandidaten-DB
- *Siehe Agent 1 Punkt 1 — derselbe Input, zählt für beide.*

### 🔴 2. 5–10 echte Stellenprofile aus vergangenen Mandaten
- **Was genau:** Verschiedene Branchen und Senioritäten als Trainings- und Testmaterial
- **Wer beim Kunden:** Operations / Vertrieb
- **Gestellt am:** —
- **Status:** offen
- **Antwort:** —

### 🔴 3. Regionalregeln (PLZ-Logik)
- **Was genau:** Wie wird "Standort München" zu PLZ-Bereich + Umkreis übersetzt; übliche Umkreis-Werte je Senioritäts-Stufe
- **Wer beim Kunden:** Operations
- **Gestellt am:** —
- **Status:** offen
- **Antwort:** —

### 🟡 4. Seniority- und Titel-Mapping
- **Was genau:** Junior/Senior/Lead/Principal zu Berufsjahren und Filter-Werten; Faustregeln zur Titel-Erweiterung
- **Wer beim Kunden:** Operations
- **Gestellt am:** —
- **Status:** offen
- **Antwort:** —

---

## Übergreifende Fragen / interne Klärung

### ⚪ Versende-Mail an Kunden mit Bring-Liste
- **Was:** Wer schreibt die initiale Mail an den Kunden mit der Excel-Bring-Liste? Welcher Ansprechpartner beim Kunden bekommt sie?
- **Status:** offen

### ⚪ DSGVO-Bewertung Trainingsmaterial
- **Was:** Sind die "Beispiel-Outputs aus heutiger manueller Praxis" personenbezogen? Falls ja: müssen sie vor Speicherung in `customer-data/` zusätzlich pseudonymisiert werden?
- **Status:** offen

# Report Finanziamenti su Supabase

La versione del Report Finanziamenti da aprire fuori da claude.ai, con un link. La pagina su GitHub Pages contiene solo il codice: i mesi stanno su Supabase e si vedono solo dopo l'accesso con email e password (create da Luca su Supabase). Luca inserisce i mesi nuovi direttamente da questa pagina.

## Come è fatto
- `index.html` – la pagina pubblicata. Si genera con `python costruisci.py` dalla pagina su claude.ai (`../2026-10-26_bozza_mensile-finanziamenti.html`), che resta l'unica fonte del codice.
- `sql/01_schema.sql` – tabelle e regole di accesso: chi non è collegato non vede niente, chi è in `accessi` come `lettore` legge, come `editore` legge e scrive.
- `dati-locali/` – **esclusa da git**: lo storico con i dati reali (`02_storico.sql`) e l'elenco delle email autorizzate (`03_accessi.sql`). Non va mai pubblicata.

## Stato
- **3/11/2026:** `index.html` rigenerato con il nuovo design del report (guscio alla Google, pagine a colori). `costruisci.py` ora riconosce il contenitore `<div class="wrap g-app">`. Pubblicato su GitHub Pages il 3/11 con il via di Luca, dopo i controlli: nessun dato nella pagina e, senza accesso, Supabase nega la lettura di `mesi` e `accessi` (HTTP 401).

- **3/11/2026, novità validate da Luca una per una e pubblicate:** confronto con lo stesso periodo dell'anno prima nei numeri chiave (mese e trimestre); penetrazione separata fra nuovo e km 0; "Da inizio anno" (numero in evidenza, tre cifre e grafico progressivo) in fondo alla Panoramica; mix delle finanziarie mese per mese e loyalty per modello nella pagina Credito; colori dei marchi legati al colore del brand. **Scartate:** il grafico del portafoglio (contratti meno immatricolazioni) e gli avvisi "Da guardare" con soglie fisse. Il pulsante "Report PDF" resta solo ai lettori. Sorgente della versione precedente: `4-archivio/2026-11-03_report-finanziamenti-senza-novita.html`.

## Regole
- I numeri non entrano mai nel repository: né nella pagina né nella storia dei commit.
- Prima di pubblicare, chiedere conferma a Luca e verificare che senza accesso il database non restituisca niente.
- Per dare o togliere l'accesso a una persona: riga in `accessi` e utente in Authentication > Users.

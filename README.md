# Report Finanziamenti su Supabase

La versione del Report Finanziamenti da aprire fuori da claude.ai, con un link. La pagina su GitHub Pages contiene solo il codice: i mesi stanno su Supabase e si vedono solo dopo l'accesso con email e password (create da Luca su Supabase). Luca inserisce i mesi nuovi direttamente da questa pagina.

## Come è fatto
- `index.html` – la pagina pubblicata. Si genera con `python costruisci.py` dalla pagina su claude.ai (`../2026-10-26_bozza_mensile-finanziamenti.html`), che resta l'unica fonte del codice.
- `sql/01_schema.sql` – tabelle e regole di accesso: chi non è collegato non vede niente, chi è in `accessi` come `lettore` legge, come `editore` legge e scrive.
- `dati-locali/` – **esclusa da git**: lo storico con i dati reali (`02_storico.sql`) e l'elenco delle email autorizzate (`03_accessi.sql`). Non va mai pubblicata.

## Stato
- **4/11/2026, novità validate da Luca e pubblicate:** nomi dei marchi sempre visibili nel grafico delle quote (se non stanno nella fetta, vanno nella riga sotto); nella tabella Marchi il gruppo Liquidazioni con totale, liquidazioni su immatricolazioni totali e su immatricolazioni del nuovo (tolta la vecchia "% immatric."); nella Panoramica, sotto la penetrazione, il grafico delle liquidazioni con le due misure, asse fisso 0-120% (triangolo per i mesi oltre) e distacco colorato. Pubblicate da una sorgente pulita senza gli avvisi ancora in prova: `4-archivio/2026-11-04_report-finanziamenti-senza-avvisi.html`, con `python costruisci.py ../../../4-archivio/2026-11-04_report-finanziamenti-senza-avvisi.html` (dal 4/11 lo script accetta il percorso della sorgente).
- **3/11/2026, prova in corso solo sull'artefatto:** avvisi morbidi in "Inserisci un mese" (quattro vincoli logici, da validare). Finché non sono validati non rilanciare `costruisci.py`: il sorgente senza avvisi, uguale a GitHub `4563d26`, è in `4-archivio/2026-11-03_report-finanziamenti-prima-degli-avvisi.html`.
- **Dove si usa il report (Luca, 3/11/2026):** il report in uso è questa versione (GitHub Pages con i dati su Supabase); i mesi si inseriscono solo qui. L'artefatto su claude.ai serve solo per le prove: il suo archivio interno è separato e può restare indietro.
- **3/11/2026:** `index.html` rigenerato con il nuovo design del report (guscio alla Google, pagine a colori). `costruisci.py` ora riconosce il contenitore `<div class="wrap g-app">`. Pubblicato su GitHub Pages il 3/11 con il via di Luca, dopo i controlli: nessun dato nella pagina e, senza accesso, Supabase nega la lettura di `mesi` e `accessi` (HTTP 401).

- **3/11/2026, novità validate da Luca una per una e pubblicate:** confronto con lo stesso periodo dell'anno prima nei numeri chiave (mese e trimestre); penetrazione separata fra nuovo e km 0; "Da inizio anno" (numero in evidenza, tre cifre e grafico progressivo) in fondo alla Panoramica; mix delle finanziarie mese per mese e loyalty per modello nella pagina Credito; colori dei marchi legati al colore del brand. **Scartate:** il grafico del portafoglio (contratti meno immatricolazioni) e gli avvisi "Da guardare" con soglie fisse. Il pulsante "Report PDF" resta solo ai lettori. Sorgente della versione precedente: `4-archivio/2026-11-03_report-finanziamenti-senza-novita.html`.

## Regole
- I numeri non entrano mai nel repository: né nella pagina né nella storia dei commit.
- Prima di pubblicare, chiedere conferma a Luca e verificare che senza accesso il database non restituisca niente.
- Per dare o togliere l'accesso a una persona: riga in `accessi` e utente in Authentication > Users.

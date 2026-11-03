# Report Finanziamenti su Supabase

La versione del Report Finanziamenti da aprire fuori da claude.ai, con un link. La pagina su GitHub Pages contiene solo il codice: i mesi stanno su Supabase e si vedono solo dopo l'accesso con email e password (create da Luca su Supabase). Luca inserisce i mesi nuovi direttamente da questa pagina.

## Come è fatto
- `index.html` – la pagina pubblicata. Si genera con `python costruisci.py` dalla pagina su claude.ai (`../2026-10-26_bozza_mensile-finanziamenti.html`), che resta l'unica fonte del codice.
- `sql/01_schema.sql` – tabelle e regole di accesso: chi non è collegato non vede niente, chi è in `accessi` come `lettore` legge, come `editore` legge e scrive.
- `dati-locali/` – **esclusa da git**: lo storico con i dati reali (`02_storico.sql`) e l'elenco delle email autorizzate (`03_accessi.sql`). Non va mai pubblicata.

## Stato
- **3/11/2026:** `index.html` rigenerato con il nuovo design del report (guscio alla Google, pagine a colori). `costruisci.py` ora riconosce il contenitore `<div class="wrap g-app">`. Pubblicato su GitHub Pages il 3/11 con il via di Luca, dopo i controlli: nessun dato nella pagina e, senza accesso, Supabase nega la lettura di `mesi` e `accessi` (HTTP 401).

- **3/11/2026, prova solo sull'artefatto:** la pagina su claude.ai contiene sei novità visive in prova (confronto con l'anno prima, avvisi "Da guardare" con soglie non validate, grafico da inizio anno, penetrazione nuovo e km 0 separate, portafoglio, mix delle finanziarie e loyalty per modello). **Su GitHub non ci sono:** finché Luca non le valida, non rilanciare `costruisci.py`, altrimenti finiscono anche qui. Versione pubblicata senza le novità: commit `f8aefdc` (senza il pulsante "Report PDF" per l'editore, che crea il PDF dalla pagina "Crea il report"); il suo sorgente è in `4-archivio/2026-11-03_report-finanziamenti-senza-novita.html`.

## Regole
- I numeri non entrano mai nel repository: né nella pagina né nella storia dei commit.
- Prima di pubblicare, chiedere conferma a Luca e verificare che senza accesso il database non restituisca niente.
- Per dare o togliere l'accesso a una persona: riga in `accessi` e utente in Authentication > Users.

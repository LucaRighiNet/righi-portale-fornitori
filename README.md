# Portale Fornitori Righi Solutions

Portale che mette in comunicazione **Righi** e i suoi **fornitori terzisti** sui
lavori di subappalto di manodopera: **cablaggio e costruzione di quadri
elettrici** (automazione, distribuzione, potenza).

Non è un portale di qualifica fornitori né di approvvigionamento materiali: è un
portale di **delega di commesse a progetto** brevi (3–5 settimane), con due
obiettivi — **ridurre il testo scritto** e **accelerare l'assegnazione**.

PWA statica **offline-first**, senza dipendenze: i dati restano sul dispositivo.

## Avvio

- **Subito**: apri `index.html` in un browser. Al primo accesso scegli un utente
  (lato Righi o lato Fornitore); gli accessi sono già predisposti per la demo.
- **Come sito** (consigliato per la PWA):
  ```bash
  python3 -m http.server 8080   # poi apri http://localhost:8080
  ```

Vedi [`LEGGIMI.md`](LEGGIMI.md) per la guida d'uso completa.

## Struttura

| Percorso | Contenuto |
|---|---|
| `index.html` | L'app (PWA) — CSS e JS inline, nessun asset esterno |
| `manifest.json`, `sw.js`, `logo.svg` | PWA: installazione, offline, icona |
| `LEGGIMI.md` | Guida d'uso |
| `PIANO_PRODOTTO.md` | Piano di prodotto, sintesi ricerca, roadmap |
| `BACKEND.md` | Contratto backend: accessi (auth), RLS, sync, ruoli, import/export |
| `tests/` | Suite native Node (`node tests/run_all.js`) |

## Test

```bash
node tests/run_all.js
```

Verifica la sintassi dell'app (`node --check`) e la logica pura di dominio
(ruoli, visibilità delle commesse, ritardi, ore/carico, filtro/ordinamento,
round-trip CSV import/export, contratto sync). Nessuna dipendenza esterna.

## Note

- Repository **privato**: il deploy automatico su GitHub Pages non è attivo (le
  Pages non pubblicano da repo privati su piano gratuito). L'app resta apribile
  in locale o pubblicabile dove preferite.
- Prototipo offline-first: i dati restano sul dispositivo finché non si aggancia
  il backend cloud descritto in [`BACKEND.md`](BACKEND.md) (il client ha già il
  *seam* di sync pronto e testato).

# Diario lattosio e flatulenza

Web app per il telefono che registra il lattosio consumato e gli episodi di flatulenza (orario e intensità da 1 a 5), per capire quanto lattosio tolleri.

- **Si installa come un'app.** Dopo averla pubblicata, la aggiungi alla schermata Home e si apre a schermo intero, con la sua icona.
- **Funziona anche offline.**
- **I dati restano sul tuo telefono.** Non ci sono server, account o tracciamenti.
- **Stima del lattosio.** Inserisci alimento e peso: il lattosio viene calcolato da una tabella di oltre 120 alimenti e piatti italiani. Per quelli che non sono in tabella scrivi tu i grammi di lattosio per 100 g, e l'app li ricorda per le volte successive.
- **Grafici.** Uno mostra l'andamento della giornata, con cibi ed episodi sulla stessa linea del tempo. Altri due coprono gli ultimi 14 giorni.
- **Esportazione e backup.** Puoi esportare i dati in CSV, salvare un backup e ripristinarlo.

È un solo file HTML, senza dipendenze e senza passaggi di compilazione.

## Pubblicarla con GitHub Pages (gratis)

1. Crea un account su [github.com](https://github.com) se non ce l'hai.
2. Crea un nuovo repository con il pulsante **New**, per esempio `diario-lattosio`. Può essere pubblico. Se è privato, GitHub Pages richiede un piano a pagamento.
3. Nella pagina del repository tocca **Add file → Upload files** e trascina **tutto il contenuto** di questa cartella: `index.html`, `manifest.webmanifest`, `sw.js`, `README.md` e la cartella `icons`. Poi tocca **Commit changes**.
4. Vai su **Settings → Pages**. In *Build and deployment* scegli **Source: Deploy from a branch**, poi branch `main` e cartella `/ (root)`, e tocca **Save**.
5. Dopo uno o due minuti l'app è online all'indirizzo
   `https://TUO-NOME-UTENTE.github.io/diario-lattosio/`

Se usi git da terminale:

```bash
cd diario-lattosio
git init && git add . && git commit -m "Prima versione"
git branch -M main
git remote add origin https://github.com/TUO-NOME-UTENTE/diario-lattosio.git
git push -u origin main
```

Poi attiva Pages come al punto 4.

## Installarla sul telefono

- **iPhone (Safari):** apri l'indirizzo, tocca **Condividi** e scegli **Aggiungi alla schermata Home**.
- **Android (Chrome):** apri l'indirizzo, tocca il menu **⋮** e scegli **Installa app** (oppure *Aggiungi a schermata Home*).

## Uso

- **Episodio:** controlla l'orario (è già impostato su adesso) e tocca l'intensità da 1 a 5. L'episodio è salvato subito.
- **Alimento:** scrivi il nome e il peso in grammi e controlla la stima, poi tocca **Salva alimento**. Prima di salvare puoi correggere il valore per 100 g.
- **Altri giorni:** le frecce ‹ › in alto aprono i giorni passati. Ciò che registri finisce nel giorno che stai guardando.
- **Cancellare una voce:** tocca **Elimina** e poi **Conferma**.

## I tuoi dati

I dati sono salvati nella memoria del browser del telefono (`localStorage`). Li perdi se:
- cancelli i dati di navigazione o del sito;
- disinstalli l'app o cambi telefono;
- su iPhone, non apri l'app per molte settimane: Safari può cancellare i dati dei siti inutilizzati.

Per questo conviene usare **Salva backup** ogni tanto. Il backup è un file `.json` da tenere, per esempio, su iCloud o Google Drive. Con **Ripristina backup** lo ricarichi: le voci vengono unite a quelle presenti, senza duplicati.

## Aggiornare l'app

Se modifichi un file, cambia anche `VERSION` in `sw.js` (per esempio da `"v1"` a `"v2"`). Così i telefoni scaricano la nuova versione invece di usare quella in memoria. Spesso servono due aperture dell'app perché l'aggiornamento compaia.

Per aggiungere alimenti alla tabella, modifica l'elenco `FOODS` in `index.html`. Il formato è `["nome", grammi_lattosio_per_100g, ["sinonimo", ...]]`.

## Nota

I valori di lattosio sono medie indicative e variano con marca e ricetta. L'app aiuta a osservare un andamento, ma non sostituisce il parere di un medico o di un nutrizionista.

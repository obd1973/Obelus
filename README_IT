🇬🇧 [Read in English](README.md)

# Obelus Toolkit
### Strumenti per la fatturazione Amazon nel sistema SDI italiano

---

Fatturare correttamente per Amazon in Italia è più difficile di quanto sembri.

L'Agenzia delle Entrate ha le sue regole. Amazon ne ha di proprie, in aggiunta. Si sovrappongono, ma non coincidono — e nel mezzo c'è lo spazio in cui le fatture si bloccano: rifiutate, parcheggiate, o sospese senza una spiegazione chiara. Quando il fornitore se ne accorge, sono già passate settimane.

Obelus è stato costruito per chiudere quella lacuna prima che si apra.

È un insieme di tre strumenti locali — nessuna installazione, nessun cloud, nessun dato che lascia il tuo computer — che accompagnano il fornitore attraverso la struttura corretta di una fattura XML compatibile con Amazon, spiegano cosa significa ogni campo e perché esiste, e validano il risultato finale prima che un solo file venga inviato.

---

## I Tre Strumenti

### 1. Obelus Mentor
`ObelusMentor.html`

Una guida interattiva che spiega in modo chiaro i concetti dietro i campi della fattura XML. Si apre nel browser. Nessuna installazione necessaria.

Mentor copre gli otto campi responsabili della maggior parte dei rifiuti delle fatture Amazon: il codice destinatario SDI, i codici prodotto (EAN/ASIN), il numero dell'ordine di acquisto, il numero fattura, la corrispondenza degli importi totali, l'aliquota IVA, i dati acquirente Amazon e l'identità fiscale del venditore. Ogni campo è spiegato con tre domande — cos'è, perché esiste, e perché si sbaglia — più il valore o il formato esatto richiesto.

Disponibile in italiano e inglese tramite un selettore nell'interfaccia.

**Usa Mentor per primo**, prima di aprire qualsiasi template, per capire cosa stai compilando e perché.

---

### 2. Template XML
`templates/`

File XML precompilati, uno per tipo di documento, con le costanti Amazon già inserite e commenti inline che spiegano ogni campo che il fornitore deve completare. Rimuovi i commenti prima di inviare allo SDI.

| File | Tipo documento |
|------|---------------|
| `TD01_template.xml` | Fattura |
| `TD04_template.xml` | Nota di credito |
| `TD05_template.xml` | Nota di debito |

Ogni template include:
- Dati Amazon precompilati (ragione sociale, P.IVA, indirizzo, PEC) — non modificarli
- Istruzioni inline per ogni campo che il fornitore deve compilare
- Una checklist finale con le cause di rifiuto più comuni
- Note su fatture con più ordini, riferimenti DDT, codici di addebito e spese di trasporto

**Usa i template dopo Mentor**, quando hai capito cosa ti viene chiesto in ogni sezione.

---

### 3. Obelus
`Obelus1.0.html`

Un motore di validazione locale. Trascina uno o più file XML completati e li controlla rispetto ai requisiti di formato e routing Amazon — immediatamente, prima dell'invio.

**Cosa controlla automaticamente:**
- Presenza del numero fattura e unicità nel batch
- Codice destinatario SDI rispetto ai codici Amazon (Retail, Dropship, Advantage)
- Indirizzo PEC
- Ragione sociale Amazon (corrispondenza esatta)
- Partita IVA Amazon
- Validità del tipo documento
- Importo totale
- Conformità OFA per note di credito e debito (riferimento documento collegato, codice Causale)
- Corrispondenza importi tra note di credito/debito e fatture originali in modalità batch

**Cosa estrae per la verifica manuale:**
- Numero/i dell'ordine di acquisto (PO) trovati nell'XML — da confermare in Vendor Central
- Codici prodotto ASIN/EAN trovati nell'XML — da confrontare con il catalogo attivo

**Cosa non controlla:**
La validazione dello schema SDI (conformità XSD, firme digitali, busta di trasmissione) — queste verifiche sono gestite dal tuo software di fatturazione e dal sistema SDI.

**Storico ed esportazione:**
Ogni validazione viene registrata localmente con data, numero fattura, esito e dati PO/ASIN estratti. L'esportazione produce un file CSV strutturato — una colonna di stato e una di dettaglio per ogni controllo, più una colonna di risoluzione per ogni anomalia — pensato per essere condiviso direttamente con un referente Amazon o il reparto IT come report autonomo.

**Usa Obelus per ultimo**, quando la fattura è completa, prima di inviarla allo SDI.

---

## Flusso di Lavoro Consigliato

```
1. Apri Mentor → capisci i campi
2. Apri il template corretto → compila i tuoi dati
3. Trascina l'XML completato in Obelus → leggi i risultati
4. Correggi gli errori → esegui Obelus di nuovo
5. Invia allo SDI
```

Se stai correggendo una fattura già rifiutata:

```
1. Identifica l'errore (Obelus ti mostra cosa è fallito e perché)
2. Emetti una nota di credito (TD04) con riferimento al numero fattura originale
3. Usa il template TD04 + Obelus per validare la nota di credito
4. Riemetti la fattura corretta (TD01)
5. Validala di nuovo con Obelus prima di inviarla
```

---

## Codici SDI Amazon — Riferimento Rapido

| Campo | Valore |
|-------|--------|
| Ragione sociale | `AMAZON EU SARL, SUCCURSALE ITALIANA` |
| Partita IVA | `IT08973230967` |
| PEC | `amazoneu@legalmail.it` |
| Codice SDI — Retail | `XR6XN0E` |
| Codice SDI — Dropship | `ERI9GSW` |
| Codice SDI — Advantage | `ZDHP2W8` |

---

## Privacy

Tutti e tre gli strumenti funzionano interamente nel tuo browser o come file locali. Nessun dato della fattura viene trasmesso, caricato o salvato al di fuori del tuo computer. Nessuno strumento richiede una connessione internet dopo il download.

---

## Requisiti

Un browser moderno (Chrome, Firefox, Edge, Safari). Nient'altro.

---

## Segnalazioni e Contributi

Se trovi un errore, un caso non gestito o hai un suggerimento, apri una segnalazione in questo repository. Se sei un fornitore Amazon italiano e hai usato questi strumenti, il tuo feedback su cosa ha aiutato e cosa era ancora poco chiaro è particolarmente prezioso — è quello che orienta la versione successiva.

---

## Autore

Creato da **Oscar Bares**
[LinkedIn](https://www.linkedin.com/in/oscar-b-43572422/) · [GitHub](https://github.com/obd1973/Obelus)

Questo toolkit è stato creato per risolvere un problema reale e ricorrente osservato nelle operazioni dei fornitori Amazon in Italia. È gratuito, open-source e fornito senza garanzie. Non è affiliato né approvato da Amazon.

---

*Il nome Obelus (÷) si riferisce al simbolo della divisione — e all'atto di separare ciò che è corretto da ciò che non lo è.*

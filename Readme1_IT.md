# Toolkit Obelus

In Italia, la fatturazione è spesso il lavoro di una sola persona.

Non un dipartimento. Una sola persona. Spesso autodidatta, che lavora a memoria e impara per tentativi ed errori. Quando se ne va, chi prende il suo posto ricomincia da zero. I webinar esistono. La documentazione esiste. Ma nessuno la consegna al nuovo arrivato il primo giorno.

Il risultato è un problema silenzioso e costoso. Fatture che sono perfettamente conformi allo SDI — che soddisfano ogni requisito governativo — rimangono comunque bloccate nel sistema di Amazon. Questo perché la conformità allo SDI e la conformità al formato Amazon sono due cose diverse, e nessuno lo spiega in modo chiaro.

Quando un fornitore si rende conto che qualcosa non va, sono passate settimane. A volte mesi. La fattura viene corretta, inviata di nuovo, e viene scartata per una regola diversa. Nel frattempo, una piccola azienda aspetta un pagamento che ha già maturato.

Non riuscivo a trovare una soluzione che colmasse il divario tra le rigide regole dei sistemi Amazon e il lavoro quotidiano dei fornitori. Così l'ho costruita.

Obelus non è più solo un validatore. È un ecosistema completo in quattro parti, progettato in modalità self-service per diagnosticare gli errori, insegnare le regole e fornire esempi impeccabili — tutto localmente, nel tuo browser.

---

## Il Toolkit

L'ecosistema Obelus si basa su quattro componenti che lavorano in sinergia:

### 1. Validatore Obelus (`Obelusv1.8XL.html`)
Il motore diagnostico principale. Lo apri in un browser e ci trascini dentro i tuoi file XML. Esegue una serie rigorosa di controlli di conformità specifici per Amazon (Codici destinatario, Ragione sociale, Partita IVA, Tipo di documento e corrispondenza degli importi per le Note di Credito/Debito). Ti dice esattamente cosa c'è di sbagliato, quale riga nell'XML ha generato l'errore e come risolverlo prima di inviare il documento allo SDI.

### 2. Obelus Mentor (`ObelusMentor1.2.html`)
La "Stele di Rosetta". Quando il Validatore segnala un errore, fornisce un link diretto a Mentor. Mentor spiega *perché* esiste quella regola in un linguaggio semplice (in inglese e italiano). Soprattutto, include un **Localizzatore Software** (Software Locator) che traduce i tag XML grezzi nei nomi dei campi effettivi utilizzati dai più diffusi software di fatturazione italiani (es. "Cerca *Codice Univoco* nella tua *Anagrafica Clienti*"). Fornisce persino dei messaggi precompilati che i venditori possono copiare e incollare per chiedere aiuto all'assistenza del proprio software.

### 3. Template XML Annotati
Bozze strutturali. Sono file XML perfettamente formattati contenenti istruzioni esplicite, avvisi e checklist. Esistono per essere letti e studiati, e mostrano esattamente dove devono essere inserite le costanti richieste da Amazon.

### 4. Il "Golden Dummy" (`Golden_Example_100_Percent_Pass.xml`)
Un prototipo funzionale. È un file XML immacolato, compilato con dati aziendali fittizi, che ha la garanzia di superare il Validatore Obelus con il 100% di controlli verdi (PASS). I venditori possono usarlo per testare l'affidabilità del Validatore e confrontarlo fianco a fianco con i propri file scartati, così da individuare visivamente le differenze.

---

## Perché Funziona

* **Zero Dipendenze:** Nessuna installazione. Nessun server. Nessun account. Scarica i file HTML e aprili. Funzionano istantaneamente su qualsiasi computer.
* **Privacy Totale:** Tutto viene elaborato localmente utilizzando JavaScript e il `localStorage` del tuo browser. I tuoi dati finanziari non lasciano mai il tuo dispositivo.
* **Report di Correzione:** Il Validatore esporta un report CSV altamente operativo. Funziona come un report di anomalia autonomo con istruzioni di risoluzione chiare, perfetto da consegnare a un reparto IT o al fornitore del software gestionale.
* **Elaborazione Massiva (Batch):** Trascina 50 fatture in un colpo solo. Obelus le incrocia per segnalare numeri di fattura duplicati e verifica che gli importi delle note di credito/debito corrispondano esattamente a quelli delle fatture originali collegate.

---

## Cosa NON Può Fare

Obelus non ha accesso a Vendor Central. Pertanto, ci sono due cose che richiedono sempre un controllo umano:
1.  **Ordini di Acquisto (PO):** I numeri di PO sono aperti e corretti?
2.  **Codici Prodotto:** I codici ASIN/EAN corrispondono al tuo catalogo attivo?

Dopo ogni convalida, lo strumento mette in evidenza questi elementi in un pannello dedicato. Non sono nascosti. Sono in primo piano. Vengono estratti in modo che tu possa confermarli facilmente.

---

## Cosa NON Sostituisce

Obelus convalida i requisiti di formattazione e instradamento specifici di Amazon. Non esegue una convalida profonda dello schema SDI (conformità XSD, verifica della firma digitale o controlli della busta di trasmissione). Questo viene gestito a monte dal tuo software di fatturazione e dal sistema SDI stesso.

---

## Come Usarlo

1.  Scarica la cartella completa di Obelus.
2.  Apri `Obelusv1.8XL.html` in qualsiasi browser moderno.
3.  Trascina e rilascia i tuoi file di fattura `.xml` generati.
4.  Rivedi i risultati. Se viene segnalato un errore, clicca sul link **"📖 Learn more in Mentor"** (Scopri di più in Mentor) per capire come risolverlo nel tuo gestionale.
5.  Esporta il report CSV se ti serve un registro.

Tutto qui.

---

## Tipi di Documento Supportati

| Codice | Tipo |
|------|------|
| TD01 | Fattura standard |
| TD04 | Nota di credito |
| TD05 | Nota di debito |
| TD24 | Fattura differita |
| TD25 | Fattura differita (ex art. 73) |

---

## Codici Destinatario SDI

| Codice | Canale |
|------|---------|
| XR6XN0E | Retail (Vendor Central) |
| ERI9GSW | Dropship |
| ZDHP2W8 | Advantage |

---

*Fornito "così com'è" per uso interno dei fornitori. Non affiliato o approvato da Amazon.*
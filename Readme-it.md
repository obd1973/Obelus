Here is the updated Italian version of your `README-it.md` file, translating all the new features and updates from version 2.3aXL:

## [Leggi in Inglese 🇬🇧](README.md)

# Obelus Toolkit

In Italia, la fatturazione è spesso il lavoro di una sola persona.

Non un dipartimento. Una persona sola. Spesso autodidatta, che lavora a memoria, imparando per tentativi ed errori. Quando se ne va, un'altra persona ricomincia da zero. I webinar esistono. La documentazione esiste. Ma nessuno li consegna al nuovo arrivato il primo giorno.

Il risultato è un problema silenzioso e costoso. Fatture perfettamente conformi allo SDI — che rispettano ogni requisito governativo — rimangono bloccate nel sistema di Amazon. Perché la conformità SDI e la conformità al formato Amazon sono due cose diverse, e nessuno evidenzia chiaramente questo divario.

Quando un fornitore si rende conto che qualcosa non va, sono già passate settimane. A volte mesi. La fattura viene corretta, inviata nuovamente e respinta di nuovo per una regola diversa. Nel frattempo, una piccola azienda aspetta un pagamento che si è già guadagnata.

Non sono riuscito a trovare una soluzione che colmasse il divario tra le regole robotiche di Amazon e il flusso di lavoro umano del fornitore. Così ne ho costruita una.

Obelus non è più solo un validatore. È un ecosistema self-service completo, diviso in quattro parti, progettato per diagnosticare errori, insegnare le regole e fornire esempi impeccabili — tutto localmente, nel tuo browser.

---

## Il Toolkit

L'ecosistema Obelus si basa su quattro componenti che lavorano insieme:

### 1. Validatore Obelus (`Obelus2.3aXL.html`)

Il motore diagnostico principale. Lo apri in un browser e ci trascini i tuoi file XML. Esegue una rigorosa serie di controlli di conformità specifici per Amazon (Codici destinatario, Denominazioni, Partite IVA, Tipi di documento e corrispondenza Note di Credito/Debito). Ora presenta un pannello laterale dinamico "Fix Plan" (Piano di Correzione) che fornisce piani di risoluzione personalizzati e passo-passo. Inoltre, categorizza i documenti in sottotipi specifici (come RETAIL, COOP, RETURN e PQV) per applicare regole di validazione esatte. Ti dice esattamente cosa è sbagliato, quale riga nell'XML ha generato l'errore e come risolverlo prima dell'invio allo SDI.

### 2. Obelus Mentor (`ObelusMentor1.2.html`)

La "Stele di Rosetta". Quando il Validatore segnala un errore, il nuovo pannello Fix Plan rimanda direttamente a Mentor. Mentor spiega *perché* esiste la regola in un linguaggio semplice (sia in inglese che in italiano). L'aspetto fondamentale è che include un **Localizzatore Software** che traduce i tag XML grezzi nei nomi effettivi dei campi utilizzati dai più diffusi software di fatturazione italiani (ad es., "Cerca il *Codice Univoco* nella tua *Anagrafica Clienti*"). Fornisce persino messaggi da copiare e incollare che i fornitori possono inviare all'assistenza clienti del proprio gestionale.

### 3. Modelli XML Annotati

Piani di riferimento formativi. Si tratta di file XML perfettamente strutturati contenenti istruzioni esplicite, avvisi e liste di controllo. Esistono per essere letti e studiati, mostrando esattamente dove devono essere inserite le costanti richieste da Amazon.

### 4. Il Fantoccio d'Oro (`Golden_Example_100_Percent_Pass.xml`)

Un prototipo funzionale. Questo è un file XML immacolato, compilato con dati aziendali fittizi, che ha la garanzia di superare Obelus con il 100% di spunte verdi. I fornitori possono utilizzarlo per familiarizzare con il Validatore e confrontarlo fianco a fianco con i propri file errati per individuare visivamente le differenze.

---

## Perché Funziona

* **Zero Dipendenze:** Nessuna installazione. Nessun server. Nessun account. Basta scaricare i file HTML e aprirli. Funzionano istantaneamente su qualsiasi macchina.
* **Privacy Totale:** Tutto viene eseguito localmente utilizzando JavaScript e il `localStorage` del tuo browser. I tuoi dati finanziari non lasciano mai il tuo dispositivo.
* **Report di Correzione:** Il Validatore ora esporta report PDF altamente formattati per le validazioni di singole fatture e riepiloghi in formato nativo Excel (`.xlsx`) per elaborazioni massive. Questi fungono da report di errore autonomi con chiare istruzioni di risoluzione, perfetti per essere consegnati a un reparto IT o al fornitore del software.
* **Elaborazione Massiva:** Carica 50 fatture in una volta sola. Obelus le incrocia per segnalare numeri di fattura duplicati e verifica che gli importi delle note di credito/debito corrispondano esattamente a quelli delle fatture originali collegate.

---

## Cosa Non Può Fare

Obelus non ha accesso a Vendor Central. Di conseguenza, due cose richiedono sempre un controllo umano:

1. **Ordini di Acquisto (PO):** I numeri degli ordini sono aperti e corretti?
2. **Codici Prodotto:** I codici ASIN/EAN corrispondono a quelli del tuo catalogo attivo?

Dopo ogni validazione, lo strumento mette in risalto questi elementi in un pannello dedicato. Non nascosti. In primo piano. Li estrae per permetterti di confermarli.

---

## Cosa Non Sostituisce

Obelus convalida i requisiti specifici di formattazione e instradamento di Amazon. Non esegue una validazione profonda dello schema SDI (conformità XSD, verifica della firma digitale o controlli della busta di trasmissione). Questo viene gestito a monte dal tuo software di fatturazione e dal sistema SDI stesso.

---

## Come Usarlo

1. Scarica la cartella completa di Obelus.
2. Apri `Obelus2.3aXL.html` in un qualsiasi browser moderno.
3. Trascina e rilascia i file delle fatture `.xml` generati.
4. Esamina i risultati. Se viene segnalato un errore, apri il pannello fluttuante "Fix Plan" per visualizzare una risoluzione passo-passo o fai clic sui link Mentor per capire come risolverlo nel tuo gestionale.
5. Esporta il report in PDF o Excel se ti serve un archivio.

Tutto qui.

---

## Tipi di Documento Supportati

| Codice | Tipo |
| --- | --- |
| TD01 | Fattura standard |
| TD04 | Nota di credito |
| TD05 | Nota di debito |
| TD24 | Fattura differita |
| TD25 | Nota di credito differita |

---

## Codici Destinatario SDI

| Codice | Canale |
| --- | --- |
| XR6XN0E | Retail |
| ERI9GSW | Dropshipping |
| ZDHP2W8 | Advantage |

---

*Fornito "così com'è" per uso interno dei fornitori. Non affiliato o approvato da Amazon.*[Leggi in Inglese 🇬🇧](README.md)
---

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

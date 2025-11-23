# prompt iniziale
crea una sezione documentazione che legga dei diagrammi mermaid e dei file markdown dalla cartella /documentation.

# Piano di Documentazione

Genera un **piano completo di documentazione** per il progetto, organizzando tutti i materiali all’interno della cartella `doc/`.

## 🎯 Obiettivo
Analizzare il codice sorgente del progetto e produrre la documentazione per **ogni singola funzionalità**, garantendo coerenza, chiarezza e facilità di consultazione.

## 📂 Output richiesti per ogni funzionalità

### 1. Diagramma di Flusso (Flowchart)
- Linguaggio: **Mermaid**
- Deve rappresentare:
  - Input della funzionalità  
  - Passi logici interni  
  - Condizioni / branch decisionali  
  - Output finale  

### 2. Sequence Diagram
- Linguaggio: **Mermaid**
- Deve mostrare:
  - Attori o componenti coinvolti  
  - Flusso delle chiamate  
  - Interazioni tra moduli, funzioni o servizi  
  - Dipendenze  

### 3. User Journey (opzionale)
- Linguaggio: **Mermaid (journey)**  
- Deve descrivere:
  - I passi dell’utente nell’utilizzo della funzionalità  
  - Il livello di soddisfazione o difficoltà per ciascun passo  
  - Gli attori coinvolti (utente, sistema, parti esterne)  

### 4. Capability Map (opzionale)
- Linguaggio: **Mermaid** (o strutturata in Markdown se più adatto)
- Deve illustrare:
  - Le capacità principali del sistema  
  - Le sotto-capabilities collegate alla funzionalità  
  - La relazione gerarchica tra capabilities  
  - Come la funzionalità contribuisce alla capability complessiva  

### 5. README dedicato
- File Markdown: `doc/<feature-name>/README.md`
- Deve includere:
  - Descrizione della funzionalità  
  - Scopo e valore  
  - Dettaglio del comportamento  
  - Input / Output  
  - Dipendenze  
  - Esempi d’uso  
  - Limitazioni e edge-case  
  - Riferimenti ai diagrammi generati  

## 📑 Requisiti generali
- Creare una sottocartella `doc/<feature-name>/` per ogni funzionalità.
- Mantenere una struttura uniforme dell’intera documentazione.
- Garantire che tutti i diagrammi siano compatibili con il rendering Mermaid.
- Se necessario, aggiungere documenti trasversali (es. overview architetturale, mappa delle dipendenze, indice globale).

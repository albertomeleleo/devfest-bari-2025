# Specifica di Progetto: WineCellar Manager

## 1. Panoramica del Progetto
L'obiettivo è sviluppare **WineCellar Manager**, un'applicazione web distribuita per la gestione completa di una cantina di vini (Enoteca). Il sistema deve permettere la gestione del catalogo prodotti, il monitoraggio delle giacenze di magazzino e la gestione dell'anagrafica clienti.

## 2. Requisiti Funzionali
L'applicazione deve essere suddivisa in contesti funzionali ben definiti:

### A. Gestione Catalogo Vini (Catalog Context)
*   **Inserimento/Modifica Vini:** Gestione schede tecniche (Nome, Cantina, Annata, Vitigno, Gradazione, Regione, Note di degustazione).
*   **Ricerca:** Filtri avanzati per tipologia (Rosso, Bianco, Bollicine), prezzo e regione.
*   **Classificazione:** Gestione delle categorie e delle denominazioni (DOC, DOCG, IGT).

### B. Gestione Magazzino (Inventory Context)
*   **Stock Tracking:** Monitoraggio della quantità disponibile per ogni etichetta.
*   **Movimentazioni:** Registrazione di ingressi (fornitori) e uscite (vendite/degustazioni).
*   **Alert:** Notifica quando un prodotto scende sotto una soglia minima di giacenza.

### C. Gestione Clienti (Customer Context)
*   **Anagrafica:** Creazione e gestione profili clienti (Privati e B2B).
*   **Storico:** Visualizzazione dei vini acquistati o preferiti (opzionale per future implementazioni di marketing).

## 3. Requisiti Architetturali

### Frontend
*   **Framework:** React (ultima versione stabile).
*   **Stile:** Utilizzo di una libreria UI moderna (es. Material UI o Tailwind CSS).
*   **State Management:** Context API o Redux Toolkit.
*   **Comunicazione:** Axios o React Query per le chiamate REST.

### Backend
*   **Framework:** Spring Boot (v3.x o successiva).
*   **Architettura:** Microservizi distribuiti.
*   **Linguaggio:** Java 17 o 21 (LTS).
*   **Build Tool:** Maven o Gradle.

### Infrastruttura & Microservizi Pattern
*   **API Gateway:** Spring Cloud Gateway per instradare le richieste dal frontend ai microservizi.
*   **Service Discovery:** Netflix Eureka o Consul per la registrazione dei servizi.
*   **Database:** Pattern *Database per Service*. Ogni microservizio deve avere il proprio database isolato (es. PostgreSQL o MySQL).
*   **Comunicazione Inter-service:** Feign Client (sincrona) o RabbitMQ/Kafka (asincrona, se necessaria per aggiornamenti magazzino).

## 4. Struttura Domain Driven Design (DDD)
Ogni microservizio deve rispecchiare un **Bounded Context** e seguire la struttura a strati tipica del DDD:

1.  **Wine Service (Catalog Bounded Context)**
    *   *Aggregate Root:* `Wine`
    *   *Value Objects:* `GrapeVariety`, `Region`, `Price`.
    *   *Responsabilità:* Gestisce le informazioni immutabili del prodotto.

2.  **Warehouse Service (Inventory Bounded Context)**
    *   *Aggregate Root:* `InventoryItem`
    *   *Value Objects:* `StockLevel`, `Location` (Scaffale/Corsia).
    *   *Responsabilità:* Gestisce la quantità fisica. Comunica con il *Wine Service* tramite ID prodotto.

3.  **Customer Service (CRM Bounded Context)**
    *   *Aggregate Root:* `Customer`
    *   *Value Objects:* `Address`, `ContactInfo`.
    *   *Responsabilità:* Gestione dati sensibili e profili utenti.

## 5. Esempio di Struttura del Codice (Backend)
Ogni microservizio dovrà seguire questa gerarchia di package:
```text
com.winecellar.[servicename]
├── domain          # Entità, Value Objects, interfacce Repository (Logica pura)
├── application     # DTOs, Mappers, Service Layer (Casi d'uso)
├── infrastructure  # Implementazione Repository (JPA), Configurazione DB
└── interface       # REST Controllers (API Layer)
```

---

### Istruzioni per l'AI 
Se devi usare questo testo come prompt per generare codice, puoi incollare il testo sopra e aggiungere alla fine:

> *"Sulla base di queste specifiche, genera la struttura del progetto, il file `docker-compose.yml` per orchestrare i servizi e il codice per il microservizio 'Wine Service' implementando le entità DDD e il controller REST."*
# MongoDB Contact Manager

Progetto pratico sviluppato nell'ambito del **Master in Data Engineering** (ProfessionAI).

Dimostrazione delle principali operazioni MongoDB su una collezione di contatti: query avanzate, aggregation pipeline e operazioni CRUD.

---

## Tecnologie

- **MongoDB 7** (Docker)
- **Python 3.11+** con `pymongo`
- **Jupyter Notebook**

---

## Avvio rapido

### 1. Avvia MongoDB con Docker

```bash
docker-compose up -d
```

### 2. Installa le dipendenze Python

```bash
pip install -r requirements.txt
```

### 3. Configura le variabili d'ambiente

```bash
cp .env.example .env
```

Il file `.env` predefinito punta a `mongodb://localhost:27017` — nessuna modifica necessaria per l'esecuzione locale.

### 4. Apri il notebook

```bash
jupyter notebook notebook/mongodb_analysis.ipynb
```

---

## Struttura del progetto

```
├── data/
│   └── utenti.json              # Dataset di 11 contatti
├── notebook/
│   └── mongodb_analysis.ipynb   # Analisi completa con pymongo
├── docker-compose.yml
├── requirements.txt
└── .env.example
```

---

## Esercizi

| # | Operazione | Concetti MongoDB |
|---|---|---|
| 1 | Contatti per società | `find` con filtro |
| 2 | Contatti con più numeri di telefono | `$type`, `$expr`, `$size` |
| 3 | Numeri di telefono per tag | `$in`, proiezione |
| 4 | Contatti senza profilo social | dot notation, `$exists` |
| 5 | Conteggio amici stretti vs non | aggregation, `$group`, `$sum` |
| 6 | Media chiamate amici stretti | `$match`, `$avg` |
| 7 | Aggiunta numero di telefono | update pipeline, `$cond`, `$isArray`, `$concatArrays` |
| 8 | Inserimento nuovo contatto | `insertOne` |

---

## Schema documento

```json
{
  "Nome": "string",
  "Cognome": "string",
  "Numero_di_cellulare": "string | array",
  "Società": "string (opzionale)",
  "Tag": ["string"] ,
  "Altri_contatti": {
    "Email": "string | array",
    "Indirizzo": "string",
    "Profilo_social": "string"
  },
  "Chiamate_ultimo_mese": "int",
  "Amici_stretti": "bool"
}
```

Il campo `Numero_di_cellulare` è definito volutamente eterogeneo (stringa o array) per simulare dati reali e dimostrare la gestione di tipi misti in MongoDB.

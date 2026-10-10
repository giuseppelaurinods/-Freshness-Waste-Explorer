# 🛒 Freshness & Waste Explorer

Benvenuto nel repository ** Freshness & Waste Explorer**. 

Questo progetto di data analytics analizza i dati delle vendite al dettaglio (Retail Store Sales) con un focus specifico sulle dinamiche d'acquisto delle **categorie deperibili** (es. *Butchers, Food, Milk Products, Patisserie*) rispetto a quelle non deperibili. L'obiettivo principale è identificare pattern di vendita, stagionalità e comportamenti dei clienti per ottimizzare la gestione del riordino e ridurre lo spreco di magazzino.

---

## 🎯 Obiettivi del Progetto & Ipotesi di Business

L'analisi è guidata dalla verifica di **5 ipotetici scenari di business**:

1. **Vendite nel Weekend**: Le categorie deperibili generano una quota di fatturato proporzionalmente maggiore nel weekend rispetto a quelle non deperibili?
2. **Stagionalità Mensile**: Esiste una stagionalità mensile riconoscibile nelle vendite dei prodotti deperibili?
3. **Impatto degli Sconti**: Il valore medio dello scontrino (`Total Spent`) aumenta quando viene applicato uno sconto?
4. **Giorni Critici di Vendita**: Alcuni giorni della settimana concentrano una quota sproporzionata delle transazioni sui prodotti deperibili?
5. **Metodi di Pagamento**: Il pagamento in contanti è associato a scontrini di importo inferiore rispetto ai metodi digitali o carte?

---

## 📊 Dataset Utilizzato

- **Fonte**: Kaggle — [*Retail Store Sales: Dirty for Data Cleaning*](https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning)
- **Dimensione**: ~12.575 transazioni
- **Struttura dei dati**: Informazioni dettagliate su transazioni, clienti, categorie merceologiche, prezzi unitari, quantità, sconti applicati, date di vendita e metodi di pagamento.

---

## 🛠️ Pipeline del Progetto

Il lavoro è suddiviso nei seguenti step principali:

1. **Data Collection (`01_data_collection.ipynb`)**:
   - Download automatizzato del dataset tramite l'API `kagglehub`.
   - Caricamento nei DataFrame `pandas` edispezione iniziale della struttura.
   - Parsing e conversione dei tipi di dato (es. conversione di `Transaction Date` in formato datetime ed estrazione di *Anno, Mese, Giorno*).

2. **Data Cleaning (`02_data_cleaning.ipynb`)**:
   - Gestione avanzata dei valori mancanti tramite relazioni logiche e matematiche:
     $$\text{Total Spent} = \text{Price Per Unit} \times \text{Quantity}$$
   - Imputazione del valore `Item` tramite mappatura unica `(Category, Price Per Unit)`.
   - Imputazione della variabile `Quantity` mancante tramite la mediana per ciascun prodotto.
   - Ricostruzione booleana della colonna `Discount Applied` tramite confronto prezzo teorico vs. prezzo reale.
   - Esportazione del dataset pulito (`df_cleaning.csv`).

3. **Exploratory Data Analysis - EDA (`03_eda_analysis.ipynb`)**:
   - **Analisi delle Distribuzioni**: Studio della frequenza delle transazioni, dei volumi di vendita e del fatturato aggregato per categoria merceologica.
   - **Verifica delle Ipotesi di Business**: Test empirico delle 5 ipotesi guida tramite aggregazioni di dati e tabelle pivot.
   - **Analisi Comparativa dei Deperibili**: Confronto delle metriche di vendita (volumi, ricavi, scontrino medio) tra prodotti deperibili e non deperibili.
   - **Data Visualization**: Creazione di un set completo di grafici avanzati (bar chart, boxplot e heatmap di correlazione) realizzati con `Matplotlib` e `Seaborn` per evidenziare pattern stagionali e comportamenti d'acquisto.
## 🚀 Come Eseguire il Progetto

### Requisiti
- Python 3.x
- Librerie: `pandas`, `numpy`, `matplotlib`, `seaborn`, `kagglehub`

### Setup
1. Clona il repository:
   ```bash
   git clone [https://github.com/tuo-username/gda-freshness-waste-explorer.git](https://github.com/tuo-username/gda-freshness-waste-explorer.git)
   cd gda-freshness-waste-explorer


# 📘 Documentazione Tecnica - Jupyter Notebook `Esercizio.ipynb`

## 🎯 Obiettivo
Analisi di un dataset contenente informazioni sui finanziamenti ricevuti dai comuni italiani tramite avvisi pubblici, probabilmente legati al PNRR.

---

## 🧩 1. Importazione e Visualizzazione iniziale dei dati

```python
import pandas as pd
data = pd.read_csv(".../candidature_comuni_finanziate 1.csv", sep=',')
data.head()
```

**Descrizione:**  
- Importazione del file CSV in un DataFrame con `pandas`
- Visualizzazione delle prime righe

---

## 📊 2. Statistiche Descrittive

```python
data.describe()
```

**Descrizione:**  
- Statistiche su colonne numeriche: media, deviazione standard, valori minimi/massimi

---

## 🧱 3. Informazioni Generali sul Dataset

```python
data.info()
```

**Descrizione:**  
- Tipi di dati
- Numero di valori non nulli
- Colonne con valori mancanti: `comune`, `provincia`, `codice_cup`

---

## 📅 4. Conversione Date

```python
data["data_invio_candidatura"] = pd.to_datetime(data["data_invio_candidatura"], errors='coerce')
data["data_finanziamento"] = pd.to_datetime(data["data_finanziamento"], errors='coerce')
```

**Descrizione:**  
- Conversione delle date da stringa a oggetto `datetime`
- `errors='coerce'` converte i valori errati in `NaT`

---

## 🗺️ 5. Aggregazione per Regione

```python
finanziamenti_per_regione = data.groupby("regione")["importo_finanziamento"].sum().sort_values(ascending=False)
```

**Descrizione:**  
- Raggruppamento per `regione` e somma dei finanziamenti
- Ordinamento decrescente

---

## 🔍 Colonne Chiave del Dataset

- `codice_ipa`, `ente`, `tipologia_ente`, `comune`, `provincia`, `regione`
- `importo_finanziamento`, `avviso`
- `data_invio_candidatura`, `data_finanziamento`
- `codice_cup`, `numero_finestra_temporale`, `numero_di_protocollo`
- `stato_candidatura`, `data_stato_candidatura`

---

## ✅ Suggerimenti per Sviluppi Futuri

- Pulizia e gestione valori mancanti
- Analisi visive con grafici
- Studio delle tempistiche tra candidatura e finanziamento
- Esportazione dei risultati

---

**Fine documento.**

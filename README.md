# Detekcija Prevara na Kreditnim Karticama korišćenjem Neuronskih Mreža

## 📋 Opis Projekta

Ovaj projekat implementira sistem za detekciju prevara na kreditnim karticama korišćenjem dubokih neuronskih mreža. 
Projekat je deo ispita **Mašinsko učenje - Neuronske mreže**.

## 🎯 Ciljevi

- Implementacija neuronskih mreža za binarnu klasifikaciju
- Rešavanje problema nebalansiranih podataka (fraud transakcije čine ~0.17% dataseta)
- Optimizacija modela za maksimizaciju recall-a pri detekciji prevara
- Evaluacija performansi korišćenjem relevantnih metrika

## 📊 Dataset

**Izvor:** [Credit Card Fraud Detection - Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud/data)

**Karakteristike:**
- **Veličina:** 284,807 transakcija
- **Features:** 30 kolona
  - `Time`: Vreme od prve transakcije
  - `V1-V28`: PCA transformisane features (anonimizovane)
  - `Amount`: Iznos transakcije
  - `Class`: Target varijabla (0 = Normal, 1 = Fraud)
- **Nebalansiranost:** 492 prevare (0.172%) vs 284,315 normalnih transakcija



## 🏗️ Arhitektura Projekta

### 1. Eksplorativna Analiza Podataka (EDA)
- Analiza distribucije klasa
- Statistički pregled features
- Vizualizacija Amount feature po klasama
- Analiza PCA komponenti (V1-V28)

### 2. Priprema Podataka
- **Skaliranje:** StandardScaler za Amount feature
- **Train-Test Split:** 80/20 sa stratifikacijom
- **Standardizacija:** StandardScaler za sve feature-e
- **Class Weighting:** Balansiranje nebalansiranih klasa

### 3. Arhitektura Neuronske Mreže

```
Input Layer (29 features)
    ↓
Dense (64 neurons, ReLU)
    ↓
Dropout (0.3)
    ↓
Dense (32 neurons, ReLU)
    ↓
Dropout (0.2)
    ↓
Output (1 neuron, Sigmoid)
```

**Hiperparametri:**
- Optimizer: Adam (learning rate = 0.001)
- Loss function: Binary Crossentropy
- Batch size: 2048
- Max epochs: 50
- Callbacks: EarlyStopping, ReduceLROnPlateau, ModelCheckpoint

### 4. Evaluacione Metrike
- **ROC-AUC:** Area Under ROC Curve
- **PR-AUC:** Area Under Precision-Recall Curve
- **Precision, Recall, F1-Score**
- **Confusion Matrix**



## 📚 Naučeni Koncepti

1. **Binararna klasifikacija** sa neuronskim mrežama
2. **Regularizacija** (Dropout, class weights)
3. **Callbacks** (EarlyStopping, ReduceLROnPlateau, ModelCheckpoint)
4. **Evaluacija** na nebalansiranim podacima
5. **Threshold optimization** za business zahteve


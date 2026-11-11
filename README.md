# Využitie metód dátovej analytiky pri podpore diagnostiky konkrétneho ochorenia

**Bakalárska práca** | Ústav umelej inteligencie (ÚUI)  
**Autor:** Anna Berezan  
**Vedúci:** Ing. Anna Biceková, PhD.  
**Rok:** 2025/2026

---

## Popis projektu

Projekt sa zaoberá využitím metód strojového učenia pri predikcii rakoviny krčka maternice. Cieľom bolo porovnať výkonnosť štyroch klasifikačných algoritmov (Logistická regresia, Random Forest, SVM, XGBoost), analyzovať vplyv diagnostických atribútov na presnosť predikcií a identifikovať kľúčové rizikové faktory pomocou metódy SHAP.

---

## Štruktúra projektu
```
├── 01_Exploratory_Data_Analysis.ipynb
├── 02_Baseline_Model_Benchmarking.ipynb
├── 03_Model_Optimization_and_Ablation_Study.ipynb
├── 04_New_Dataset_Experiment.ipynb
├── risk_factors_cervical_cancer.csv
├── sobar-72.csv
└── README.md
```
---

## Popis notebookov

### 01 — Prieskumná analýza dát (EDA)
Analýza datasetu Cervical Cancer Risk Factors (858 pacientok, 36 atribútov).
- Čistenie dát: nahradenie symbolu `?` hodnotou `NaN`, konverzia dátových typov
- Klasifikácia atribútov na binárne (24) a numerické (12)
- Analýza chýbajúcich hodnôt, distribúcií a vzťahov s cieľovou premennou (Biopsy)
- Vizualizácia kľúčových atribútov

### 02 — Porovnanie základných modelov (Baseline)
Vytvorenie referenčných modelov bez optimalizácie hyperparametrov.
- Rozdelenie dát: trénovacia / testovacia množina (80/20)
- Modely: Logistická regresia, Random Forest, SVM, XGBoost
- Hodnotenie: úspešnosť, presnosť, návratnosť, F1-skóre, ROC-AUC
- Konfúzne matice pre všetky modely

### 03 — Optimalizácia modelov a ablačná štúdia
Hlavná experimentálna časť práce.
- Predspracovanie: KNN Imputer, StandardScaler, SMOTE (aplikované výhradne na trénovacej množine)
- Optimalizácia hyperparametrov: GridSearchCV (cv=5, scoring=recall)
- Porovnanie kompletného datasetu vs. redukovaného datasetu (bez diagnostických testov)
- Interpretácia výsledkov pomocou metódy SHAP
- Kompozitné skóre pre výber najlepšieho modelu: Recall (40%) + ROC-AUC (35%) + F1-skóre (25%)

### 04 — Experiment na novom datasete
Doplnkový experiment na datasete Cervical Cancer Behavior Risk (72 pacientok, 19 atribútov).
- Analýza behaviorálnych a psychosociálnych faktorov
- Porovnanie modelov s aplikáciou SMOTE a bez nej
- 5-násobná krížová validácia
- SHAP analýza najlepšieho modelu

---

## Datasety

| Dataset | Zdroj | Záznamy | Atribúty | Cieľová premenná |
|---|---|---|---|---|
| Cervical Cancer Risk Factors | UCI ML Repository | 858 | 36 | Biopsy |
| Cervical Cancer Behavior Risk | UCI ML Repository | 72 | 19 | ca_cervix |

Oba datasety sú dostupné na: https://archive.ics.uci.edu/

---

## Požiadavky

### Python verzia
Python 3.10+

### Inštalácia knižníc
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn shap jupyter

---

## Spustenie

1. Stiahnite repozitár
2. Nainštalujte požadované knižnice
3. Spustite notebooky v poradí: 01 → 02 → 03 → 04
4. Uistite sa, že datasety sa nachádzajú v rovnakom priečinku ako notebooky

---

## Kľúčové výsledky

- Modely na kompletnom datasete dosahovali návratnosť až 0,818
- Po odstránení diagnostických atribútov návratnosť klesla na 0,273–0,455
- Najlepší model na kompletnom datasete: Random Forest (Accuracy: 0,971, ROC-AUC: 0,940)
- Najlepší model na redukovanom datasete: XGBoost (Recall: 0,455, ROC-AUC: 0,692)
- SHAP analýza identifikovala konzistentné rizikové faktory naprieč oboma datasetmi

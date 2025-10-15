# 🧠 asi-wine-quality

Projekt realizowany w ramach **Sprintu 1** — przygotowanie w pełni działającego repozytorium uczenia maszynowego, które każdy może uruchomić „na czysto”.
Celem sprintu jest pokazanie pełnego cyklu: struktura projektu → dane → EDA → prosty baseline w scikit-learn.

---

## 🎯 Cel projektu

Celem projektu jest **predykcja jakości wina** (w skali 0–10) na podstawie jego właściwości fizykochemicznych, takich jak poziom kwasowości, zawartość alkoholu, siarczynów itp.
Zadanie to ma charakter **regresyjny** – model ma przewidzieć wartość ciągłą (`quality`).

---

## 📊 Dane

- **Źródło:** [UCI Machine Learning Repository – Wine Quality](https://archive.ics.uci.edu/ml/datasets/wine+quality)
  (bezpośrednie pliki:
  [red wine CSV](https://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-red.csv),
  [white wine CSV](https://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-white.csv))
- **Licencja:** Creative Commons Attribution 4.0 International (CC BY 4.0)
- **Data pobrania:** 2025-10-14
- Zbiór danych nie zawiera informacji osobowych (PII).

W repozytorium znajduje się próbka (~300 wierszy) w folderze `data/01_raw/winequality_sample.csv` — pełny zbiór można pobrać uruchamiając `scripts/fetch_sample.py`.

---

## 🧮 Metryka ewaluacji

**RMSE (Root Mean Squared Error)**
Uzasadnienie wyboru:
- ma tę samą jednostkę co target (`quality`),
- silnie karze duże błędy predykcji,
- jest intuicyjny i powszechnie stosowany w zadaniach regresyjnych.

---

## 🧱 Struktura repozytorium

```
src/project_name/        # kod projektu (data_loading.py, cleaning.py, utils.py)
notebooks/               # 01_eda.ipynb, 02_baseline_sklearn.ipynb
data/01_raw/             # próbka danych (CSV)
data/02_interim/         # dane pośrednie (.gitkeep)
data/03_processed/       # dane przetworzone (.gitkeep)
tests/                   # testy jednostkowe (pytest)
scripts/                 # np. fetch_sample.py
README.md
environment.yml
.pre-commit-config.yaml
.gitignore
```

---

## ⚙️ Jak uruchomić projekt lokalnie

1. Utwórz środowisko i zainstaluj zależności:
   ```bash
   conda env create -f environment.yml
   conda activate asi-ml
   python -m ipykernel install --user --name asi-ml --display-name "Python (asi-ml)"
   ```
2. Zainstaluj pre-commit i pobierz próbkę danych:
   ```bash
   pre-commit install
   python scripts/fetch_sample.py
   ```
3. Uruchom testy i sprawdź formatowanie:
   ```bash
   pre-commit run -a
   pytest -q
   ```
4. Otwórz notebooki:
   - `notebooks/01_eda.ipynb` — analiza danych + czyszczenie
   - `notebooks/02_baseline_sklearn.ipynb` — prosty model (np. RandomForestRegressor)

---

## 🧪 Testy i jakość kodu

- `pytest -q` — szybkie testy jednostkowe
- `pre-commit run -a` — sprawdzenie formatowania (black, ruff, isort)
Oba polecenia muszą przejść bez błędów przed commitem.

---

## 🚫 Prywatność i bezpieczeństwo

Projekt nie zawiera danych osobowych ani sekretów.
Pliki `.env` i duże dane są wykluczone poprzez `.gitignore`.
Zbiór UCI Wine Quality jest w pełni publiczny.

---

## 📅 Informacje organizacyjne

- **Milestone:** Sprint 1
- **Deadline:** 17 października 2025 r.
- **Iteration (Project):** Sprint 1

---

## 👤 Autorzy

- [Twoje imię i nazwisko lub zespół]

---

### ✅ Definition of Done (Sprint 1)

- Repo z pełną strukturą (`src/`, `data/`, `notebooks/`, `tests/`)
- Środowisko `conda` + kernel Jupytera
- Pre-commit + testy przechodzą
- README zawiera źródło danych, licencję i metrykę
- Notebooki `01_eda.ipynb` i `02_baseline_sklearn.ipynb` są gotowe

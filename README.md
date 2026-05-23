# pz057uf

Tento repozitár obsahuje projekt zameraný na spracovanie a analýzu klinických dát
hospitalizovaných pacientov s COVID-19 pomocou metód strojového učenia.
Projekt je implementovaný v jazyku Python s využitím Jupyter Notebookov.

Zdrojové klinické dáta ako aj rozsahy hodnôt atribútov nie sú súčasťou repozitára
a musia byť vyžiadané samostatne.

## Ciele projektu

- Transformácia a štandardizácia 47 laboratórnych parametrov zo 4 vĺn pandémie
- Extrakcia príznakov z voľného textu Epikrízy — stav prepustenia, komorbiditiy, symptómy, saturácie
- Predikcia závažnosti priebehu ochorenia pomocou klasifikačných modelov strojového učenia

## Štruktúra projektu

```
├── 01_Nacitanie_a_transformacia.ipynb     # načítanie, transformácia, analýza pokrytia
├── 02_Extrakcia_zo_stlpcov.ipynb          # extrakcia príznakov a výpočet indexov
├── 03_Modelovanie.ipynb                   # klasifikačné experimenty
├── rozsah_hodnot_atributov_vyplnene.xlsx  # referenčné rozsahy laboratórnych parametrov
├── requirements.txt
└── README.md
```

## Systémové požiadavky

| Požiadavka | Hodnota |
|---|---|
| Operačný systém | Windows, Linux alebo macOS |
| Python | 3.10 alebo novší |
| RAM | odporúčané 16+ GB |
| Voľné miesto na disku | približne 3 GB pre zdrojové dáta a výstupy |
| Vývojové prostredie | JupyterLab 4.0+ |

## Inštalácia

1. Naklonujte repozitár:

```bash
git clone https://github.com/kkuichi/pz057uf.git
cd pz057uf
```

2. Vytvorte a aktivujte virtuálne prostredie:

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
```

3. Nainštalujte požadované balíky:

```bash
pip install -r requirements.txt
```

## Spustenie

Projekt je určený na spustenie v prostredí JupyterLab. Po aktivácii prostredia spustite:

```bash
jupyter lab
```

Notebooky spúšťajte v poradí 01 → 02 → 03 — každý závisí na výstupe predchádzajúceho.
Zdrojové dáta umiestnite do priečinka `VEGA_dáta z 13-11-2024/` vedľa notebookov.

## Použité technológie

- Python 3.10+
- scikit-learn, CatBoost, XGBoost
- Pandas, NumPy, SciPy
- Matplotlib, Seaborn
- PyArrow, OpenPyXL

## Výsledky

Najlepší výsledok dosiahol model CatBoost na príznakových setoch kombinujúcich
prvú aj poslednú nameranú hodnotu laboratórnych parametrov doplnenú o referenčné statusy
(mixed + ref/allowed) s imputáciou mediánom:
F1 macro 0.694, Balanced accuracy 0.709, ROC AUC 0.846.

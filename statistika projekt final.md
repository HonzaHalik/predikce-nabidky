# Úvod
V této práci se zaměřuji na porovnání přesnosti předpovědí modelů OLS a ARIMA při predikci počtu aktivních inzerátů na realitním trhu v Praze. Cílem je zjistit, který z těchto modelů poskytuje lepší predikce počtu inzerátů na následující měsíc. Tento projekt vznikl v rámci předmětu Statistika a slouží k prohloubení znalostí v oblasti analýzy časových řad.

# Data
Data byla sesbírána z webu sreality.cz a obsahují měsíční údaje o počtu aktivních inzerátů od března 2016 do března 2023 (celkem 84 pozorování). Průměrný počet aktivních inzerátů je 5200 se směrodatnou odchylkou 1200. Data byla sbírána automatizovaně pomocí Python skriptu s následujícími charakteristikami:

```python
Dataset shape: (84, 4)
Descriptive statistics:
count    84.000000
mean     5200.345238
std      1197.234521
min      3245.000000
25%      4321.750000
50%      4987.500000
75%      5892.250000
max      8234.000000
```

# Metodologie
Formulujeme následující hypotézy:
- H_0: Model ARIMA nepředpovídá počet inzerátů lépe než model OLS
- H_A: Model ARIMA předpovídá počet inzerátů lépe než model OLS

Pro testování využijeme následující metriky:
1. Mean Absolute Error (MAE)
2. Root Mean Square Error (RMSE)
3. Koeficient determinace (R²)
4. Akaike Information Criterion (AIC) pro ARIMA model

Pro OLS model používáme následující nezávislé proměnné:
- Počet aktivních inzerátů v předchozím měsíci
- Počet nových inzerátů v předchozím měsíci
- Počet zbylých inzerátů v předchozím měsíci

Pro ARIMA model používáme parametry:
- p = 2 (autoregresní část)
- d = 1 (diferenciace)
- q = 2 (klouzavé průměry)

# Výsledky
Výsledky OLS modelu:
- MAE: 245.31
- RMSE: 312.45
- R²: 0.85

Výsledky ARIMA modelu:
- MAE: 198.76
- RMSE: 267.89
- AIC: 1245.32
- BIC: 1267.45

## Výsledky párového t-testu
Pro ověření statistické významnosti rozdílu mezi modely byl proveden párový t-test:
- t-statistika: 12.4567
- p-hodnota: < 0.0001
- 95% interval spolehlivosti: [35.24, 58.16]

Výsledky t-testu ukazují, že rozdíl v přesnosti mezi modely OLS a ARIMA je statisticky velmi významný (p < 0.0001). To znamená, že ARIMA model skutečně poskytuje lepší předpovědi než OLS model, a tento rozdíl není dílem náhody.

Model ARIMA dosáhl lepších výsledků v obou hlavních metrikách (MAE a RMSE). Průměrný rozdíl v přesnosti předpovědí mezi modely je přibližně 46.55 jednotek (střed intervalu spolehlivosti), což představuje zlepšení o přibližně 19%.

Model ARIMA dosáhl lepších výsledků v obou hlavních metrikách (MAE a RMSE). Rozdíl v přesnosti je statisticky významný na hladině významnosti 5% (p-hodnota < 0.05).

# Diskuze
Oba modely prokázaly dobrou schopnost predikce, ale ARIMA model dosáhl lepších výsledků. To lze přičíst několika faktorům:
- ARIMA model lépe zachycuje časovou závislost v datech
- ARIMA model dokáže lépe pracovat se sezónními vlivy
- OLS model může být příliš jednoduchý pro zachycení komplexních vztahů v datech

Omezení studie:
- Relativně krátká časová řada
- Možné strukturální změny na trhu během sledovaného období
- Nezahrnutí externích ekonomických faktorů

# Závěr
Analýza ukázala, že model ARIMA poskytuje přesnější předpovědi počtu aktivních inzerátů než model OLS. ARIMA dosáhla o 19% nižší MAE a o 14% nižší RMSE. Tyto výsledky naznačují, že pro predikci počtu inzerátů je vhodnější použít sofistikovanější model časových řad (ARIMA) než jednoduchý lineární model (OLS). Pro praktické využití doporučuji používat model ARIMA, zejména v případech, kdy je důležitá přesnost předpovědi na kratší časové období.

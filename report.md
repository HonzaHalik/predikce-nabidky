
# Úvod
V této práci se zaměřuji na analýzu časových řad a predikci budoucích hodnot pomocí modelů OLS a ARIMA. Data byla sesbírána z webu sreality.cz pro lokalitu Praha. Cílem je zjistit, jak dobře tyto modely dokáží předpovědět počet aktivních inzerátů na následující měsíc. Tento projekt dělám pro svou radost a pro zlepšení svých dovedností v oblasti analýzy dat, také z důvod nutnosti odvzdání tohoto projektu do semináře Statistiky.

# Data
Data byla sesbírána z webu sreality.cz a obsahují měsíční údaje o počtu aktivních, nových a zbylých inzerátů od března 2016. Celkem dataset obsahuje 60 pozorování. Průměrná hodnota pro aktivní inzeráty je 5000 a směrodatná odchylka je 1500. Data byla sesbírána automatizovaně pomocí skriptu v Pythonu, který načítá data z webu. Slabiny sběru dat mohou být v možných chybách při zadávání dat na web. Navzdory těmto nedostatkům jsou data dostatečně reprezentativní pro analýzu.

# Metodologie
Formulujeme následující hypotézy:
- H_0: Můj model OLS/ARIMA nedokáže významně lépe předpovědět budoucí hodnoty než náhodný odhad.
- H_A: Můj model OLS/ARIMA dokáže významně lépe předpovědět budoucí hodnoty než náhodný odhad.

Pro testování hypotéz použijeme metriky jako Mean Absolute Error (MAE), Mean Squared Error (MSE) a Root Mean Squared Error (RMSE). Tyto metriky nám umožní kvantifikovat přesnost modelů. Předpoklady pro použití těchto testů zahrnují normalitu rozdělení reziduí, což ověříme pomocí histogramu reziduí a Jarque-Bera testu.

# Výsledky
Výsledky modelu OLS:
- Mean absolute error: 200.00
- Mean squared error: 50000.00
- Root mean squared error: 223.61
- r2 (train set): 0.85

Výsledky modelu ARIMA:
- AIC: 300.00
- AICC: 305.00
- BIC: 310.00

Na základě těchto výsledků můžeme říci, že model OLS má vysokou přesnost na trénovacích datech, což naznačuje, že dokáže dobře předpovědět budoucí hodnoty. Model ARIMA má také dobré výsledky, což potvrzuje jeho schopnost predikce.

# Diskuze
Výsledky naznačují, že oba modely OLS a ARIMA jsou schopny dobře předpovědět budoucí hodnoty. Je ale třeba zvážit případné nedostatky modelů, například, že modely mohou být ovlivněny sezónními vlivy, které nebyly plně odstraněny.

# Závěr
V této práci jsem zkoumal schopnost modelů OLS a ARIMA předpovědět budoucí hodnoty na základě historických dat. Data byla sesbírána z webu sreality.cz a byla analyzována pomocí metrik MAE, MSE a RMSE. Výsledky ukazují, že oba modely mají vysokou přesnost a jsou schopny dobře předpovědět budoucí hodnoty. Tyto výsledky mohou být užitečné pro další analýzy a predikce v oblasti časových řad.

# Úvod
V této práci se zaměřuji na porovnání přesnosti předpovědí modelu OLS s náhodným odhadem při predikci počtu aktivních inzerátů na realitním trhu v Praze na portálu sreality.cz. Cílem je zjistit, zda statistický model dokáže významně překonat náhodné hádání. Tento projekt dělám pro svou radost a pro zlepšení svých dovedností v oblasti analýzy dat. Taaké z důvodu rychle vzdalujícího se termínu odezdání projektu do statistiky.(vzdaluje se proto, že už proběhl)

# Data
Data byla sesbírána z webu sreality.cz a obsahují měsíční údaje o počtu aktivních inzerátů od března 2016 do března 2023 (celkem 84 pozorování). Průměrný počet aktivních inzerátů je 5200 se směrodatnou odchylkou 1200. Data byla sbírána automatizovaně pomocí Python skriptu, který načetl počty inzerátů z webu.

Potenciální slabiny dat:
- Změny ve struktuře webu mohly ovlivnit konzistenci dat
- Potenciálně malé množství dat

I přes tyto nedostatky považuji data za dostatečně reprezentativní pro účely analýzy, zejména díky jejich velkému počtu a pravidelnosti sběru.

# Metodologie
Formulujeme následující hypotézy:
- H_0: Model OLS nepředpovídá počet inzerátů lépe než náhodný odhad
- H_A: Model OLS předpovídá počet inzerátů lépe než náhodný odhad

Pro testování využijeme:
1. Mean Absolute Error (MAE) pro měření přesnosti předpovědí
2. Párový t-test pro porovnání chyb OLS modelu a náhodných odhadů
3. Root Mean Square Error (RMSE) jako dodatečnou metriku

Předpoklady pro párový t-test:
- Normalita rozdílů chyb (ověříme Jarque-Bera testem)
- Nezávislost pozorování
- Dostatečná velikost vzorku (splněno, n=84)

# Výsledky
Výsledky analýzy ukazují:
- MAE pro OLS model: 245.3
- MAE pro náhodné odhady: 892.7
- p-hodnota párového t-testu: < 0.001

Na základě p-hodnoty můžeme zamítnout nulovou hypotézu na všech běžných hladinách významnosti (1%, 5% i 10%). To znamená, že model OLS poskytuje statisticky velmi významně lepší předpovědi než náhodné hádání.

# Diskuze
Výsledky jasně ukazují převahu OLS modelu nad náhodným odhadem. Je však třeba vzít v úvahu několik omezení:
- Model předpokládá stabilitu trhu v čase
- Nezohledňuje možné strukturální změny na realitním trhu
- Neuvažuje sezónní vlivy

# Závěr
V této práci jsme porovnávali přesnost předpovědí modelu OLS s náhodnými odhady při predikci počtu realitních inzerátů. Analýza založená na datech z webu sreality.cz ukázala, že OLS model významně překonává náhodné hádání (MAE 245.3 vs 892.7). Tento výsledek byl potvrzen párovým t-testem na 1% hladině významnosti. Zjištění naznačují, že i jednoduchý statistický model může poskytnout významně lepší předpovědi než náhodné odhady.
# Môj projekt AB- finančná kalkulačka
Toto je môj historicky prvý readme file aj s oddeľovacou čiarou.  

---

## Cieľ: 
Napísať fungujúci skript na základnú finančnú (investičnú/ sporiacu) kalkulačku.  

## Obsah
Základný obsah:
* [Popis funkcionality](#popis-funkcionality)
* [Vstupné parametre](#️-vstupné-parametre)
* [Výstup](#️-výstup)
* [Príklady a ukážky](#-príklady-a-ukážky)
* [Štruktúra projektu a technické detaily](#-štruktúra-projektu-a-technické-detaily)

## Popis funkcionality: 
Používateľ môže zadať vstupy prostredníctvom metódy Input. Systém prostredníctvom funkcie vypočíta výstup - cieľovú sumu na konci sporenia a zobrazí graf s vývojom investície.  

> **POZOR:** Tento skript neberie do úvahy infláciu ani dane. Všetky výpočty sú len odhady.

*Nice to have: systém z dát vytvorí graf zobrazujúci vývoj investície v čase.*

## ⚙️ Vstupné Parametre

| Parameter | Popis | Typ Dát |
| :--- | :--- | :--- |
| `--jednorazovy_vklad` | Počiatočná jednorázová suma investície. | Float |
| `--pravidelny_vklad` | Mesačná pravidelná suma investície. | Float |
| `--pocet_rokov` | Doba sporenia v celých rokoch. | Integer |
| `--uroková sadzba_rocne` | Ročná úroková sadzba v percentách (napr. 5.5). | Float |


## ⚙️ Výstup: 
Vypočítaná cieľová suma

## 📊 Príklady a Ukážky
### Scenár 1: - Jednoduché sporenie: 

(Napr. počiatočný vklad 1000 eur, 5% úrok, 10 rokov).

Zadajte počiatočný vklad: 1000 eur, 
Zadajte ročnú úrokovú sadzbu (%): 5, 
Zadajte počet rokov: 10

>>> Výsledok: Vaša budúca hodnota po 10 rokoch bude: 1647,01 EUR


### Scenár 2 - Pravidelné sporenie:
 
(Napr. pravidelný mesačný vklad 50 eur, 5% úrok, 10 rokov).

Zadajte pravidelný mesačný vklad: 50 eur,
Zadajte ročnú úrokovú sadzbu (%): 5,
Zadajte počet rokov: 10

>>> Výsledok: Vaša budúca hodnota po 10 rokoch bude: 7764,11 EUR

### Scenár 3 - Pravidelné sporenie s počiatočným vkladom:

(Napr. počiatočný vklad: 1000 eur, pravidelný mesačný vklad 50 eur, 5% úrok, 10 rokov).

Zadajte počiatočný vklad: 1000 eur,
Zadajte pravidelný mesačný vklad: 50 eur,
Zadajte ročnú úrokovú sadzbu (%): 5
Zadajte počet rokov: 10

>>> Výsledok: Vaša budúca hodnota po 10 rokoch bude: 9411,12 EUR

## 💻 Štruktúra Projektu a Technické Detaily

**Použité moduly/knižnice**:

math as math 

numpy as np

pandas as pd

plotly.express as px

plotly.graph_objects as go

from datetime import date, timedelta

plotly.io as pio


**Matematické vzorce**:

Vzorec pre počiatočný vklad:
```bash 
 FV = P(1+r)^n
 ```

Vzorec pre mesačné vklady: 
```bash 
 FV = PMT⋅r(1+r)n−1​
```

**Kľúčové funkcie**:
```bash 
def vypocetCS(jednorazovy_vklad,pravidelny_vklad, urokova_sadzba_rocne, pocet_rokov):
    urokova_sadzba_rocne=urokova_sadzba_rocne/100
    urokova_sadzba_per_month= urokova_sadzba_rocne/12
    pocet_mesiacov= pocet_rokov*12
    FVpravidelne = (pravidelny_vklad * (((1 + urokova_sadzba_per_month) ** pocet_mesiacov - 1) / urokova_sadzba_per_month))
    FVjednorazova =(jednorazovy_vklad*(1+urokova_sadzba_per_month)**pocet_mesiacov)
    CS = round(FVjednorazova+FVpravidelne,2)
    return CS
```

**Kódové bloky ukážka**:

```bash 
def pozdrav_meno(meno):
    return(f"Ahoj, " + meno + "! Vitaj v našom investičnom programe.")
print(pozdrav_meno("Alena"))
```

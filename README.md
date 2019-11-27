# Analiza podatkov s programom R, 2019/20

Repozitorij z gradivi pri predmetu APPR v študijskem letu 2019/20

* [![Shiny](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=shiny/APPR-2019-20/projekt.Rmd) Shiny
* [![RStudio](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=rstudio) RStudio

## Analiza zdravstvenega varstva v državah EU

V sklopu projekta bom analizirala zdravstveno varstvo v državah EU. Analizriala bom javne izdatke za zdravstvo v državah na prebivalca ter kot delež BDP, prav tako privatne izdatke za zdravstvo ter celotno strukturo zdravstvenega sistema, predvsem pa koliko zaposlenih je v državi v zdravstvu na prebivalca. Te podatke bom nato primerjala s splošnim zdravjem prebivalstva v državah ter poskušala priti do zaključkov v kakšnih zdravstvenih sistemih so ljudje bolj zdravi, ter kateri zdravstveni sistemi so bolj učinkoviti.

Vire za svoj projekt bom pridobila na EUROSTATU,spletni strani World Health Organisation ter OECD.
WHO: https://gateway.euro.who.int/en/datasets/european-health-for-all-database/#health-care-utilization-and-expenditure
EUROSTAT: https://ec.europa.eu/eurostat/web/health/data/database
OECD: https://www.oecd-ilibrary.org


V sklopu analize bom primerjala slednje podatke držav EU:
1. Tabela: izdatki držav za javno zdravje, primerjava per capita ter delež BDP
https://gateway.euro.who.int/en/indicators/hfa_567-6712-public-sector-expenditure-on-health-as-of-gdp-who-estimates/

https://gateway.euro.who.int/en/indicators/hfa_571-6722-public-expenditure-on-health-ppp-per-capita-who-estimates/

2. Tabela: izdatki posameznikov za zdravstene storitve
https://gateway.euro.who.int/en/indicators/hfa_585-6861-private-households-out-of-pocket-payments-on-health-as-of-private-sector-health-expenditure/

3. Tabela: delež izdatkov javnega zdravja v primerjavi z izdatki zasebnega
https://gateway.euro.who.int/en/indicators/hfa_572-6730-public-sector-health-expenditure-as-of-total-health-expenditure-who-estimates/

4. Tabela: število zaposlenih v zdravstvu, absolutno ter na prebivalca
https://appsso.eurostat.ec.europa.eu/nui/show.do?dataset=hlth_rs_prshp1&lang=en

5. Tabela: število ljudi, ki prejema socialne prispevke za invalidnost na 100 000 ljudi
https://gateway.euro.who.int/en/indicators/hfa_414-2720-people-receiving-socialdisability-benefits-per-100-000/

6. Tabela: povprečno število dni v bolnišnici
https://data.oecd.org/healthcare/length-of-hospital-stay.htm

7. Tabela: število pričakovanih zdravih let življenja v EU v primerjavi z pričakovano življenjsko dobo (po državah ter spolu)
https://appsso.eurostat.ec.europa.eu/nui/show.do?dataset=hlth_hlye&lang=en

8. Tabela: zdravstveno stanje posamzenikov po njihovem mnenju (po državah ter dohodku)
https://appsso.eurostat.ec.europa.eu/nui/show.do?dataset=hlth_silc_10&lang=en


Cilj analize je ugotoviti ali višina izdatkov države za javno zdravje vpliva na splošno zdravje populacije ter efektivnost zdravstvenega sistema držav.


## Program

Glavni program in poročilo se nahajata v datoteki `projekt.Rmd`.
Ko ga prevedemo, se izvedejo programi, ki ustrezajo drugi, tretji in četrti fazi projekta:

* obdelava, uvoz in čiščenje podatkov: `uvoz/uvoz.r`
* analiza in vizualizacija podatkov: `vizualizacija/vizualizacija.r`
* napredna analiza podatkov: `analiza/analiza.r`

Vnaprej pripravljene funkcije se nahajajo v datotekah v mapi `lib/`.
Podatkovni viri so v mapi `podatki/`.
Zemljevidi v obliki SHP, ki jih program pobere,
se shranijo v mapo `../zemljevidi/` (torej izven mape projekta).

## Potrebni paketi za R

Za zagon tega vzorca je potrebno namestiti sledeče pakete za R:

* `knitr` - za izdelovanje poročila
* `rmarkdown` - za prevajanje poročila v obliki RMarkdown
* `shiny` - za prikaz spletnega vmesnika
* `DT` - za prikaz interaktivne tabele
* `rgdal` - za uvoz zemljevidov
* `rgeos` - za podporo zemljevidom
* `digest` - za zgoščevalne funkcije (uporabljajo se za shranjevanje zemljevidov)
* `readr` - za branje podatkov
* `rvest` - za pobiranje spletnih strani
* `tidyr` - za preoblikovanje podatkov v obliko *tidy data*
* `dplyr` - za delo s podatki
* `gsubfn` - za delo z nizi (čiščenje podatkov)
* `ggplot2` - za izrisovanje grafov
* `mosaic` - za pretvorbo zemljevidov v obliko za risanje z `ggplot2`
* `maptools` - za delo z zemljevidi
* `extrafont` - za pravilen prikaz šumnikov (neobvezno)

## Binder

Zgornje [povezave](#analiza-podatkov-s-programom-r-201819)
omogočajo poganjanje projekta na spletu z orodjem [Binder](https://mybinder.org/).
V ta namen je bila pripravljena slika za [Docker](https://www.docker.com/),
ki vsebuje večino paketov, ki jih boste potrebovali za svoj projekt.

Če se izkaže, da katerega od paketov, ki ji potrebujete, ni v sliki,
lahko za sprotno namestitev poskrbite tako,
da jih v datoteki [`install.R`](install.R) namestite z ukazom `install.packages`.
Te datoteke (ali ukaza `install.packages`) **ne vključujte** v svoj program -
gre samo za navodilo za Binder, katere pakete naj namesti pred poganjanjem vašega projekta.

Tako nameščanje paketov se bo izvedlo pred vsakim poganjanjem v Binderju.
Če se izkaže, da je to preveč zamudno,
lahko pripravite [lastno sliko](https://github.com/jaanos/APPR-docker) z želenimi paketi.

Če želite v Binderju delati z git,
v datoteki `gitconfig` nastavite svoje ime in priimek ter e-poštni naslov
(odkomentirajte vzorec in zamenjajte s svojimi podatki) -
ob naslednjem zagonu bo mogoče delati commite.
Te podatke lahko nastavite tudi z `git config --global` v konzoli
(vendar bodo veljale le v trenutni seji).

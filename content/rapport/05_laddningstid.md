
Laddningstid
=======================

I denna rapport kommer jag att undersöka tre webbplatsers laddningstid genom att använda googles verktyg Pagespeed samt devtools. Jag ska undersöka om det skiljer sig mycket mellan de olika sidorna samt om jag kan se möjliga åtgärder som skulle kunna förbättra laddningstiderna.

Urval
-----------------------

Jag kommer att titta på tre statliga myndigheters sida. Detta eftersom det är intressant ur ett medborgarperspektiv att dessa sidor är driftsäkra, enkla och snabba att använda. För att få lite bredd i urvalet har jag valt ut mydigheter som alla är ganska stora, men som kanske används på olika sätt; Försäkringskassan är den stora myndigheten som nästan alla medborgare kommer i kontakt med då och då, Skolverket som är viktigt för alla landets lärare och så till sist den kanske lite mer udda Folkhälsomyndigheten.

Metod
-----------------------

För att genomföra undersökningen använder jag googles tjänst PageSpeed som analyserar laddningstid och ger förslag på förbättringar. Jag använde också devtools nätverk. Dessutom förde jag in det resultat jag fick i ett [Google kalkylark](https://docs.google.com/spreadsheets/d/1CrNT9J1tYRfF6gmrhspPeJAbgv8WZcsdOK2TvwaOLW8/edit?usp=sharing).

Resultat
-----------------------

#### Försäkringskassan

Genom PageSpeed bedöms försäkringskassan som 99 för dator och 61 för mobil enhet. Genom devtools får FK en genomsnittlig laddningstid på 1,98s, använder 39 resurser och har en storlek på 1,87Mb.

[FIGURE src="image/forsakringskassan.png" alt="Försäkringskassans förstasida för privatpersoner"]

För att förbättra sidan föreslår PageSpeed att man ska snabba upp första uppritningen av sidan genom att ta bort resurser som tar tid från laddningen. Det verkar handla om mindre formatmallar (javascript) och mer kod direkt in på sidan, men jag är inte säker på att jag greppar detta råd riktigt.

#### Skolverket

Skolverket får omdömet 99 för dator och 50 för mobil på PageSpeed. I devtools ser jag att laddningstiden blir 1,60s, resurserna 55 och storleken 2,73Mb.

[FIGURE src="image/skolverket.png" alt="Skolverkets förstasida"]

Som möjliga förbättringar skulle de kunna bli bättre på att hantera bilder, hantera storleken bättre, komprimera mer.

#### Folkhälsomyndigheten

Folkhälsomyndigheten får omdömet 100 för dator och 95 för mobil. I devtools ser jag att laddningstiden blir 3,98s, 26 resurser och att storleken på sidan är 1,30Mb.

[FIGURE src="image/folkhalsomyndigheten.png" alt="Folkhälsomyndighetens förstasida"]

Resultaten från denna sida är motstridiga, jag vet inte riktigt hur jag ska tolka det. Kanske är det just bildformaten som behöver moderniseras, precis som PageSpeed föreslår. Att använda modernare format då, som JPEG 2000 eller WebP istället för traditionella jpeg.

Analys
-----------------------

De sidor jag har analyserat är ganska likartade. De får alla goda resultat på analysen från dator, däremot är de långsammare för mobilskärm. För alla sidorna verkar det handla om att göra den första inläsningen och uppritningen av sidan snabbare, och att det ligger kod i vägen som tar tid från detta.

Folkhälsomyndigheten som får bra betyg i PageSpeed är i själva verket väldigt långsam, med laddningstid på 3,98s som genomsnitt. Däremot blir DOM-siffran bättre, 1,26s. Det verkar vara en bild som gör att processen blir seg, det syns att en av bilderna på sidan tar mycket längre tid att rendera än det övriga innehållet. Sidan fick också rådet att se över bildformat och modernisera dessa.

Min rangordning för detta test blir följande:

* 1. Skolverket. Snabbast tid i devtools, men något sämre på mobilsidan enligt PageSpeed. Sidan laddas snabbt, allt above the fold är på plats genast.

* 2. Försäkringskassan. Värden som är väldigt lika skolverkets, men något långsammare laddningstid enligt devtools. Sidan laddas snabbt men det stör att jag ser hur ramar kommer först och text ramlar in någon millisekund senare. Inte lika snabbt och precist som Skolverket.

* 3. Folkhälsomyndigheten. Absolut på första plats enligt PageSpeed, men den vansinnigt långa laddningstiden i devtools gör att sidan åker ned på tredje plats. Fixar de sin sega bild är de absolut en konkurrent om förstaplatsen.

PageSpeed menar att en snabb sida laddas på ungefär 1 sekund, en genomsnittlig på 1-2,5 sekunder och en långsam på >2,5 sekunder. Det stämmer ganska bra med min intuitiva uppfattning också, Skolverket och försäkringskassans sidor kändes snabba och direkta medan Folkhälsomyndighetens upplevdes som oerhört långsam när den sista bilden sakta rullades ut. Så om jag själv ska bestämma en gräns för laddningstider tar jag vägledning av PageSpeed och sätter 2 sekunder som brytpunkt mellan en snabb eller långsam sida.

Referenser
-----------------------
- [PageSpeed](https://developers.google.com/speed/pagespeed/insights/?hl=sv)
- About the [PageSpeed](https://developers.google.com/speed/docs/insights/v5/about) Insights API. (2018).

Rapportförfattare
-----------------------

Elin Andreasson

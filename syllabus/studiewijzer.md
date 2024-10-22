# Studiewijzer

In deze studiewijzer verwijzen we naar hoofdstukken en opgaven uit [deze syllabus](assets/Cryptografie.pdf).

## Inleiding

*Bestudeer uit de syllabus hoofdstuk 1 op pagina 4 en 5.*

*Bestudeer uit de syllabus hoofdstuk 2 op pagina 6 t/m 8. Maak opgave 1.*

## Symmetrische cryptografie

*Bestudeer uit de syllabus van hoofdstuk 3 pagina 9 t/m 11 en maak opgaven 2, 3 en eventueel 4.*

Symmetrische cryptosystemen zijn gebaseerd op het versleutelen en ontcijferen met behulp van dezelfde sleutel. Een voorbeeld van een symmetrisch cryptosysteem is het schuifsysteem waarbij de encryptiefunctie van de vorm $E_k(x) = x + k$ is. De versleuteling met behulp van deze encryptiefuncties levert niet veel op als het gaat om geheimhouding van de boodschap. Dus daar moet een tandje bij. Bij de encryptiefunctie $E_k(x) = x + k$ maken we alleen gebruik van optellen. We gaan nu ook een vermenigvuldiging toevoegen. Dit is niet nieuw voor je, want bij de lineaire functie $f(x) = ax + b$ voer je ook een vermenigvuldiging en een optelling uit. Onze encryptiefunctie krijgt ook deze vorm. Bij de notatie moeten we uiteraard $a$ en $b$ aangeven en dat doen we weer in een subscript, in het algemeen: $E_{(a,b)}(x) = ax + b$.

:::{admonition} Voorbeeld
:class: hint

We nemen $E_{(3,7)}(x) = 3x + 7$.

Een verschil met de bekende lineaire functie is dat het domein niet $\mathbb{R}$ is. Immers, we gebruiken deze functie om een letter uit ons alfabet op een andere letter af te beelden. En het aantal letters is beperkt, dus ook het aantal getallen dat we voor $x$ kunnen substitueren.

Laten we eens aannemen dat we uitsluitend met hoofdletters van ons alfabet werken, dus we werken dan met gehele getallen van 0 tot en met 25. Dan is $E_{(3,7)}(1) = 3 \cdot 1 + 7 = 10$, dus een B wordt versleuteld tot een K. $E_{(3,7)}(20) = 3 \cdot 20 + 7 = 67 = 15$, dus een U wordt versleuteld tot een P.

Het lijkt merkwaardig om "$67 = 15$" op te schrijven als je met wiskunde bezig bent (en zeker ook in andere omstandigheden). Wat we hier echter doen heet *modulair rekenen* en om precies te zijn rekenen we *modulo 26*. Dit betekent kort door de bocht dat je in je rekenwerk de 26 als een 0 mag beschouwen. Dat betekent dat 1 hetzelfde is als 27 en ook dat 67 hetzelfde is als 15. Vandaar de notatie "$67 = 15$".

:::

Het is natuurlijk wel van essentieel belang dat we weten in welk modulair systeem we aan het rekenen zijn. In de wiskunde zeggen dat hier rekenen in $\mathbb{Z}_{26}$.[^z]

[^z]: De verzameling van gehele getallen wordt in de wiskunde aangegeven met $\mathbb{Z}$.

*Maak uit de syllabus van hoofdstuk 3 op pagina 12 opgaven 6 en 7.*

:::{exercise}
:label: ex-encryptie-conflict

We werken weer met een alfabet van 26 letters, dus we rekenen in $\mathbb{Z}_{26}$.

Bereken $E_{(2,12)}(0)$ en $E_{(2,12)}(13)$ en leg uit welk probleem we krijgen met deze encryptiefunctie.

:::

*Bestudeer uit de syllabus paragraaf 3.3 en 3.4 en maak opgaven 18, 19 en 23.*

:::{note}

In de eerste zin van &sect;3.3 wordt gesuggereerd dat een monoalfabetische substitutie iets compleet anders is dan een affien cryptosysteem. Het is weliswaar niet hetzelfde, maar een affien cryptosysteem met een fatsoenlijke decryptiefunctie (zie {ref}`ex-encryptie-conflict` uit deze studiewijzer) is ook een monoalfabetische substitutie.

:::

## Coderen

*Bestudeer uit de syllabus hoofdstuk 4 op pagina 21 en 22 en maak opgaven 2 en 3.*

## Getaltheorie

### Priemgetallen en Euclides

*Bestudeer uit de syllabus paragraaf 5.1 en 5.2 op pagina 23 t/m 28 en maak opgaven 5, 9 en 16.*

:::{note}
De syllabus is al een tijdje geleden geschreven. Het grootste priemgetal dat we nu kennen is $2^{82\space589\space933} − 1$. Dit is het 51e Mersenne-priemgetal, gevonden in december 2018, ook door GIMPS.
:::

Bij de asymmetrische cryptosystemen waar we in hoofdstuk 6 naar gaan kijken speelt de getaltheorie uit hoofdstuk 5 een belangrijke rol. Daarbij kijken we eerst naar delers en priemgetallen. Een eenvoudige manier om priemgetallen te vinden is aan de hand van de Zeef van Eratosthenes (Griekse geleerde).

:::{seealso}
Een facultatief uitstapje... Bewijs de volgende stelling:

*Stelling:* Er zijn oneindig veel priemgetallen.
:::

De grootste gemene deler van twee getallen $a$ en $m$ is - zoals de term al zegt - het grootste getal dat deler is van zowel $a$ als $m$. Notatie $ggd(a,m)$. Er zijn meerdere manieren om de ggd van twee getallen te berekenen, onder andere door priemfactorontbinding en met het algoritme van Euclides.

Facultatief: in de opgaven 12 en 14 kun je de methode van Euclides aantonen, dus laat je zien dat $ggd(a,m) = ggd(a,r)$ waarbij $r = \text{rest bij deling van } a \text{ door } m$.

:::{exercise}
**Facultatieve opgave**

Maria heeft 42 appels, 60 peren en 90 kersen geplukt. Ze wil alle vruchten verdelen over zoveel mogelijk mensen. Iedereen moet hetzelfde krijgen. Hoeveel mensen kan Maria dan een portie geven?
:::

:::{admonition} Voorbeeld
:class: hint

We kunnen $ggd(60,198)$ op meerdere manieren berekenen.

Een manier is om alle delers op te schrijven en dan de grootste gemeenschappelijke deler eruit te halen. Voor grote getallen is dat niet erg efficiënt.

Wanneer we naar de priemfactorontbinding kijken, krijgen we $60 = 2^2 \cdot 3 \cdot 5$ en $198 = 2 \cdot 3^2 \cdot 11$. In beide ontbindingen zit één keer de factor 2 en één keer de factor 3, dus $ggd(60,198) = 2 \cdot 3 = 6$.

Daarnaast kunnen we ook het algoritme van Euclides toepassen. Dat kan met berekeningen onder elkaar of in een tabel. Gezien we de tabel nog uitgebreider gaan toepassen, passen we het algoritme in een tabel toe:

| $a$ | $m$ | $q$ | $r$ |
|:---:|:---:|:---:|:---:|
| 60  | 198 | 0   | 60  |
| 198 | 60  | 3   | 18  |
| 60  | 18  | 3   | 6   |
| 18  | 6   | 3   | 0   |
| 6   | 0   |     |     |

:::

### Modulo-rekenen

*Bestudeer uit de syllabus paragraaf 5.3 op pagina 28 t/m 33 en maak opgaven 18, 24, 29, 30. Maak eventueel ook opgaven 20, 22 en 23.*

Bij het reduceren van een positief geheel getal modulo $m$ ga je net zo vaak $m$ van het geheel getal afhalen (bij een negatief getal ga je juist $m$ bij het getal optellen) totdat je een zo klein mogelijk positief getal overhoudt. Dit noemen we ook wel de rest na deling door $m$.

Eenvoudig voorbeeld: $15 \bmod 10 = 5 \bmod 10$, je kunt namelijk één keer 10 van 15 afhalen, dus 15 is in $\mathbb{Z}_{10}$ gelijk aan 5.

Met behulp van de rekenregels voor modulo-rekenen weet je hoe je met optelling en vermenigvuldiging om moet gaan. Probeer hier ook handig mee te werken zie het volgende voorbeeld en {ref}`ex-modulo-rekenregels`.

:::{admonition} Voorbeeld
:class: hint
Bereken, zonder rekenmachine, $78 \cdot 77 \cdot 76$ in $\mathbb{Z}_{81}$.

We gaan nu niet deze vermenigvuldiging uitvoeren! We bedenken even dat in $\mathbb{Z}_{81}$ geldt: $81 = 0$ en dus $78 = -3$ etc.

Dus $78 \cdot 77 \cdot 76 = -3 \cdot -4 \cdot -5 = -60 = 21$. Klaar!
:::

:::{exercise}
:label: ex-modulo-rekenregels
{style=lower-alpha}
1. Bereken $19 \cdot 39$ in $\mathbb{Z}_{40}$.
2. Bereken $25 \cdot 44$ in $\mathbb{Z}_{50}$.
3. Bereken op een handige manier $7^{11}$ in $\mathbb{Z}_{50}$.
:::

### Inverse en het uitgebreide algoritme van Euclides

*Bestudeer uit de syllabus paragraaf 5.4 en 5.5 op pagina 33 t/m 40 en maak opgaven 34, 43, 46 en 48. Meer oefening nodig? Maak dan ook opgaven 44, 45 en 47.*

Door het toepassen van het uitgebreide algoritme van Euclides voor de $ggd(a,m)$ kunnen we de lineaire Diophantische vergelijking $ab+mk=ggd(a,m)$ oplossen. Vervolgens kunnen we hieruit, alleen wanneer $ggd(a,m)=1$, de inverse van $a$ in $\mathbb{Z}_m$ verkrijgen.

Dit kun je doen door twee extra kolommen toe te voegen aan het algoritme van Euclides welke je $b$ en $k$ noemt. Op bladzijde 37 en 38 wordt laten zien hoe die kolom nu ingevuld kan worden.

Een andere manier is door 'terug te werken' zoals in opgave 42 (waarbij gebruik wordt gemaakt van de resultaten in opgave 40 en 41) gedaan wordt. Vind hierin voor jezelf de manier die het beste aansluit.

*Maak van paragraaf 5.5 opgaven 49 en 50 op pagina 40.*

We kunnen nu encryptiefuncties bekijken waar de inverse bij modulo-rekenen een rol speelt. In opgave 49 en 50 vind je twee voorbeelden van encryptiefuncties waarin je met de inverse gaat werken om versleutelde boodschappen te ontcijferen. Daarnaast gaat de inverse van een getal in $\mathbb{Z}_m$ nodig zijn bij het asymmetrische cryptosysteem RSA, welke in hoofdstuk 6 aan bod komt.

### Euler en Fermat

*Bestudeer uit de syllabus paragraaf 5.6 op pagina 40 en 41 en maak opgaven 54 en 55.*

Probeer ervoor te zorgen dat je bij machtsverheffen in $\mathbb{Z}_m$ op een efficiënte manier te werk gaat, door op een handige manier de machten te herschrijven en de machtenregel toe te passen. Kijk hiervoor ook nog even terug naar {ref}`ex-modulo-rekenregels`c in deze studiewijzer.

*Bestudeer uit de syllabus paragraaf 5.7 op pagina 42 t/m 45 en maak opgaven 57, 58, 59 en 60.*

De Eulerindicator, die het aantal getallen $a$ aangeeft zodat $0 \le a \le m-1$ en waarvoor $a$ een inverse in $\mathbb{Z}_m$ heeft (dus waarvoor $ggd(a,m)=1$), wordt genoteerd als $\phi(m)$. De resultaten uit opgaven 57c en 58d zijn van belang om de Eulerindicator van elk getal te kunnen berekenen. De Eulerindicator gaat ook een rol spelen bij het asymmetrische cryptosysteem RSA.

De stelling van Euler en de kleine stelling van Fermat kunnen helpen om grote machten efficiënter module $m$ te reduceren. Onder andere deze stellingen worden in hoofdstuk 7 'bewezen'. Mocht je geïnteresseerd zijn in de bewijzen van deze stellingen -- waar mooie wiskunde achter zit -- dan kun je je verder verdiepen in de theorie en opgaven van hoofdstuk 7.

*Maak van paragraaf 5.7 opgaven 62, 63, 64 en 65 op pagina 44 en 45.*

Oefeningen waarin encryptiefuncties met module rekenen terugkomen en welke handig zijn om te oefenen zijn 62, 63, 64 en 65. Hierin zijn de laatste twee wat uitdagender, gezien in deze opdrachten de inverse weer terugkomt.

## Asymmetrische cryptografie

*Bestudeer uit de syllabus paragraaf 6.1 op pagina 48 en 49.*

Bij asymmetrische cryptografie -- ook wel public key cryptografie genoemd -- wordt gewerkt met sleutelparen bestaande uit een privé-sleutel en een publieke sleutel. Hierbij wordt de privé-sleutel geheim gehouden door de gebruiker en de publieke sleutel wordt bekend gemaakt. Zo hoeven geen sleutels uitgewisseld te worden tussen gebruikers, hetgeen een voordeel is ten opzichte van symmetrische cryptografie.

Een asymmetrisch cryptosysteem berust op een algoritme welke eenvoudig uit te voeren is, maar waarvan het inverse algoritme zeer moeilijk uit te voeren is (ook wel een 'trapdoor one-way algoritme' genoemd), tenzij extra informatie over de privé-sleutel bekend is. Een nadeel hiervan is dat zo'n algoritme vaak meer rekentijd kost.

In de algoritmes voor asymmetrische cryptografie die we in dit hoofdstuk verder gaan bekijken komt de wiskunde terug die in hoofdstuk 5 aan bod is gekomen.

### Diffie-Hellman sleutelprotocol

*Bestudeer uit de syllabus paragraaf 6.2 op pagina 49 t/m 53 en maak opgaven 3 en 8. Maak eventueel de opgaven 9, 10 en 11.*

:::{note}
In het voorbeeld na opgave 2 staat een foutje: Alice stuurt Bob natuurlijk de combinatie $(p,\bar g,\bar A)$. Die combinatie is haar publieke sleutel.
:::

Het Diffie-Hellman sleutelprotocol is een sleuteluitwisselingsprotocol ontworpen door Whitfield Diffie en Martin Hellman die ervoor zorgt dat gebruikers op een veilige manier een sleutel kunnen afspreken. Dit kan dan bijvoorbeeld weer worden gebruikt om met behulp van een symmetrisch cryptosysteem boodschappen te vercijferen met de afgesproken sleutel vanuit Diffie-Hellman. Het algoritme is op bladzijde 50 uitgewerkt inclusief een voorbeeld. Restklassen en modulorekenen met machten in $\mathbb{Z}_p$ komt hier terug. Het algoritme is gebaseerd op het Diffie-Hellman-completeringsprobleem: het is ondoenlijk om bij de getallen $\bar g$, $\bar g^a$ en $\bar g^b$ in $\mathbb{Z}_p$ de restklasse $\bar g^{a\cdot b}$ in $\mathbb{Z}_p$ te vinden. Hierbij gaan we ervan uit dat gewerkt wordt met grote getallen.

Je komt er in de facultatieve opgaven 9, 10 en 11 achter dat niet iedere restklasse in $\mathbb{Z}_p$ even geschikt is om als $\bar g$ gebruikt te worden.

### RSA en digitale handtekeningen

*Bestudeer uit de syllabus paragraaf 6.3 en 6.4 op pagina 53 t/m 56 en maak opgaven 14, 15, 16, 17 en 18.*

RSA is een veelgebruikt asymmetrisch cryptosysteem ontworpen door Ron Rivest, Adi Shamir en Leonard Adleman (vandaar de naam RSA). Het RSA-algoritme wordt gebruikt om berichten op een veilige manier te vercijferen en te ontcijferen, waarbij iedere gebruiker een publieke en geheime sleutel kiest aan de hand van het gegeven algoritme op bladzijde 53. Op bladzijde 54 is een voorbeeld van dit algoritme uitgewerkt met kleine getallen. Het algoritme is gebaseerd op het volgende wiskundige probleem: wanneer gegeven het getal $m$, dan is het ondoenlijk om binnen afzienbare tijd de ontbinding $p\cdot q = m$ te vinden. Hierbij gaan we er weer vanuit dat gewerkt wordt met grote getallen.

Een te vercijferen bericht zet je eerst om naar getallen, bijvoorbeeld met de ASCII-tabel. Vervolgens worden deze codes achter elkaar gezet, opgesplitst in blokken van bepaalde lengte en vercijferd. Gezien de hoeveelheid rekentijd van het RSA-algoritme wordt RSA vaak gebruikt voor het versturen van een sleutel van een symmetrisch cryptosysteem.

Met behulp van RSA kan worden achterhaald of de afzender van een boodschap ook inderdaad is wie hij zegt dat hij is. Een voorbeeld waarin dit van belang is, is bij het overschrijven van geld naar een bepaalde rekening bij een bank. De opdrachtgever kan met behulp van een digitale handtekening aangeven dat hij gemachtigd is. Zo'n digitale handtekening kan gemaakt worden met behulp van RSA. Door per gebruiker een geheime en publieke sleutel te kiezen, kan iedere gebruiker een eigen digitale handtekening maken en versturen aan een andere gebruiker. De andere gebruiker kan vervolgens controleren of de handtekening inderdaad door deze persoon gemaakt is. Andere toepassingen van RSA naast digitale certificaten en handtekeningen zijn bijvoorbeeld te vinden in de authenticatie en beveiliging van informatie.

*Het bestuderen en maken van de opgaven van hoofdstuk 7, waarin de bewijzen van verschillende rekenregels en stellingen uit de syllabus terugkomen, is facultatief.*

## Uitwerkingen

:::{solution} ex-encryptie-conflict
:label: sol-encryptie-conflict

$E_{(2, 12)}(0) = 2 \cdot 0 + 12 = 12$ en \
$E_{(2, 12)}(13) = 2 \cdot 13 + 12 = 26 + 12 = 0 + 12 = 12$.

Dus zowel de A als de N worden versleuteld tot een M. We kunnen hier dus onmogelijk een decryptiefunctie opstellen. Ook hier komen we uitgebreid op terug.
:::

:::{solution} ex-modulo-rekenregels
:label: sol-modulo-rekenregels

{style=lower-alpha}
1. In $\mathbb{Z}_{40}$ is $19 \cdot 39 = 19 \cdot -1 = -19 = 21$
2. In $\mathbb{Z}_{50}$ is $25 \cdot 44 = 50 \cdot 22 = 0$
3. In $\mathbb{Z}_{50}$ is $7^2 = 49 = -1$, dus $7^{11} = (-1)^5 \cdot 7 = -7 = 43$
:::

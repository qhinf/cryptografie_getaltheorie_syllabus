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

## Uitwerkingen

:::{solution} ex-encryptie-conflict

$E_{(2, 12)}(0) = 2 \cdot 0 + 12 = 12$ en \
$E_{(2, 12)}(13) = 2 \cdot 13 + 12 = 26 + 12 = 0 + 12 = 12$.

Dus zowel de A als de N worden versleuteld tot een M. We kunnen hier dus onmogelijk een decryptiefunctie opstellen. Ook hier komen we uitgebreid op terug.

:::

# Eindopdracht

In deze opdracht gaan jullie praktisch aan de slag met de stof uit deze module, zowel vanuit de wiskunde als vanuit de informatica. Je werkt hierbij in groepjes samen.

De opdrachten sluiten aan bij asymmetrische cryptografie. De theorie voor deze opdrachten zijn grotendeels te vinden in hoofdstuk 4 t/m 6 van [de syllabus](assets/Cryptografie.pdf). De opdracht is onderverdeeld in drie delen, waarvan het de bedoeling is dat je deze onderdelen chronologisch doorloopt en gebruik maakt van elkaars hulp om tot een goed product te komen.

Bij de onderdelen staat vermeld hoeveel punten je kan scoren voor dit onderdeel en wanneer je ongeveer met een onderdeel klaar dient te zijn om op schema te lopen. Werk de onderdelen per groepje in één document uit, wat je op de aangewezen plaats in teams per groepje eenmaal inlevert.

De deadline van het gehele document is {{ eerste_inlevermoment }}. Naast het uitvoeren van onderstaande opdrachten verwachten we van jullie dat jullie bijhouden wie wat gedaan heeft. Zorg dat je dit overzicht als bijlage bij je document invoegt.

## Deel 1 (10 punten)

*Werk aan deel 1 in week 1 en 2 van de module.*

{style=lower-alpha}
1. In deel 1a ligt de focus op delers, priemgetallen en priemfactoren.
   
   **Wiskunde**: leg in je eigen woorden uit wat delers en priemgetallen zijn en wat ontbinden in priemfactoren betekent.

   **Code en commentaar**: maak in Python een functie die bij een gegeven getal kan aangeven of het een priemgetal is of niet.

   ```python
   def priem(getal):
       return True # als het getal een priemgetal is
       return False # als het getal geen priemgetal is
   ```

   **Uitleg code**: leg het 'waarom' en 'hoe' van de code uit.

2. In deel 1b ligt de focus op de grootste gemene deler en het algoritme van Euclides.

   **Wiskunde**: leg in eigen woorden uit wat een grootste gemene deler is en hoe het algoritme van Euclides werkt.

   **Code en commentaar**: maak in Python een functie waarin het algoritme van Euclides wordt toegepast om de grootste gemene deler van de getallen $a$ en $m$ te vinden.

   ```python
   def ggd_euclides(a, m):
       return ggd # bereken de ggd van a en m, met het algoritme van Euclides
   ```

   **Uitleg code**: leg het 'waarom' en 'hoe' van de code uit.

## Deel 2 (15 punten)

*Werk aan deel 2 in week 2 t/m 4 van de module.*

{style=lower-alpha}
1. In deel 2a ligt de focus op modulo rekenen en de inverse.

   **Wiskunde**: leg in eigen woorden uit wat modulo rekenen is en wat een inverse in $\mathbb{Z}_m$ is.

   **Code en commentaar**: maak in Python een functie waarmee je modulo kunt rekenen, zonder de `%` operator te gebruiken.

   ```python
   def modulo(a, m):
       return a % m # maar dan zonder % te gebruiken!
   ```

   **Uitleg code**: leg het 'waarom' en 'hoe' van je code uit.

2. In deel 2b ligt de focus op het uitgebreide algoritme van Euclides en het vinden van een inverse.

   **Wiskunde**: leg in eigen woorden uit hoe het uitgebreide algoritme van Euclides werkt. Leg uit hoe het de grootste gemene deler van $a$ en $m$ bepaalt en ook hoe en wanneer dit algoritme toegepast kan worden om de inverse van $a$ in $\mathbb{Z}_m$ te vinden.

   **Code en commentaar**: maak in Python een functie waarin het uitgebreide algoritme van Euclides toegepast wordt om van twee getallen $a$ en $m$ zowel de grootste gemene deler als getallen $b$ en $k$ te vinden zodat $a\cdot b + m\cdot k = ggd(a,m)$. Licht ook toe wanneer en waar de inverse van $a$ in $\mathbb{Z}_m$ te vinden is met het programma.

   Optimaliseer je code, zodat deze makkelijk te begrijpen is en zo min mogelijk dingen doet die geen nut hebben.

   ```python
   def ggd_uitgebreid(a, m):
       return ggd(a,m), b, k # berekend met het uitgebreide algoritme van Euclides
   ```

   **Uitleg code**: leg het 'waarom' en 'hoe' van de code uit.

## Deel 3 (30 punten)

*Werk aan deel 3 in week 4 t/m 8 van de module.*

**Wiskunde**: leg in eigen woorden uit wat de Eulerindicator $\phi(m)$ is en hoe deze berekend kan worden. Leg uit hoe het Diffie-Hellman sleutelprotocol werkt. Leg uit hoe het RSA-encryptie algoritme werkt in $\mathbb{Z}_m$ en werk dit uit in een eigen voorbeeld.

**Code en commentaar**: maak in Python een programma met:

- *functies.py*: hierin staan alle functies die je tot nu toe gemaakt hebt, en eventueel ook nog eigen functies.
- *diffie_hellman.py*: alle functies om sleutels uit te wisselen met het Diffie-Hellman protocol.
- *rsa.py*: hier maak je een class die het RSA-protocol implementeerd. Maak hierbij gebruik van de functies in *functies.py*.
  - `p` en `q` zijn je input. Controleer of dit wel priemgetallen zijn!
  - `m` ($m$), `__phi` ($\phi(m)$), `e` ($\bar e$) en `__d` ($\bar d$) bereken je zelf. (De `__` geeft aan dat een variabele "privé" is.)

Download [hier een .zip bestand](assets/Cryptografie_PythonStarter.zip) waarin deze structuur al voor je is voorbereid.

Het bestand *main.py* is al geschreven. Daarin worden de functies van Diffie-Hellman en RSA getest. Lees dit bestand goed door, zodat je weet wat elke functie moet doen, en voer het uit om te testen of je implementatie correct is.

**Uitleg code**: leg het 'waarom' en 'hoe' van de code uit.

## Beoordeling

:::{list-table}
:header-rows: 1
:stub-columns: 2
:width: 100%

* - Onderwerp
  - \%
  - 10
  - 7
  - 5
  - 2
* - Wiskunde
  - 35
  - De wiskundige theorie wordt duidelijk uitgelegd en is goed te begrijpen.
  - Bijna alle wiskundige theorie wordt duidelijk uitgelegd en is redelijk te begrijpen.
  - De wiskundige theorie wordt niet erg duidelijk uitgelegd en is matig te begrijpen.
  - Er wordt geen wiskundige theorie uitgelegd / de theorie is onduidelijk.
* - Code
  - 20
  - De code werkt in alle gevallen en is duidelijk geschreven.
  - De code werkt bijna altijd, alleen in sommige gevallen niet.
  - De code werkt vaak, maar is lastig te begrijpen.
  - De code geeft een error / geeft meestal geen goede waardes.
* - Commentaar
  - 15
  - Alles wordt duidelijk uitgelegd en is goed te begrijpen.
  - Bijna alles wordt duidelijk uitgelegd, en is goed te volgen voor een programmeur.
  - Er staat commentaar, maar nog niet alles is duidelijk.
  - Geen / niet nuttig commentaar.
* - Uitleg
  - 30
  - Het 'waarom' en 'hoe' van de code is helder uitgelegd.
  - Er is een goede uitleg, maar sommige onderdelen gaan te snel / langzaam.
  - De uitleg maakt niet alles duidelijk.
  - Geen / vage uitleg.

:::

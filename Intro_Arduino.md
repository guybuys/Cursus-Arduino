# Hoofdstuk 1: De basis van programmeren met Arduino

Arduino-programmering is gebaseerd op het schrijven van code die wordt uitgevoerd op Arduino-microcontrollers. In dit hoofdstuk zullen we de basisprincipes van Arduino-programmering verkennen.

## 1.1 Inleiding tot Arduino-programmering

Arduino-programmering omvat het schrijven van code die wordt uitgevoerd op Arduino-borden. Deze borden zijn voorzien van microcontrollers die kunnen worden geprogrammeerd met behulp van de Arduino-programmeertaal.
De programmeertaal wordt Arduino-programmeertaal genoemd, maar het is eigenlijk een variant van C/C++. De Arduino-programmeertaal is gebaseerd op de standaard C/C++-taal, maar het bevat enkele specifieke bibliotheken en functies die zijn geoptimaliseerd voor de Arduino-hardware en omgeving.

In principe kun je Arduino-code schrijven met behulp van de basisprincipes van C/C++, waaronder variabelen, functies, lussen en voorwaardelijke instructies. De Arduino-bibliotheken bieden extra functionaliteit om de interactie met hardwarecomponenten zoals sensoren, LED's, motoren, enzovoort te vergemakkelijken.

Dus, hoewel de Arduino-programmeertaal in wezen C/C++ is, biedt het een eenvoudigere syntax en enkele specifieke functies die het gemakkelijker maken om met Arduino-borden te werken.

## 1.2 De setup en loop functies

Een fundamenteel concept in Arduino-programmering is het gebruik van de `setup()` en `loop()` functies. Elk Arduino-programma moet minstens deze twee functies bevatten. Het minimale programma (dat niets doet maar niet als fout aanzien wordt), ziet er dus zo uit:

```cpp
void setup() {
}
void loop() {
}
```

### De `setup()` functie

De `setup()` functie wordt slechts één keer uitgevoerd wanneer het Arduino-bord wordt opgestart of gereset. Het wordt gebruikt voor het initialiseren van variabelen, het configureren van pinnen en het voorbereiden van het bord voor de hoofduitvoering van het programma.

Hier is een voorbeeld van hoe de `setup()` functie eruit kan zien:

```cpp
void setup() {
    // Initialisatie van pinnen
    pinMode(13, OUTPUT); // Configureer pin 13 als een uitvoerpin
    Serial.begin(9600);  // Initialiseer de seriële communicatie met een baudrate van 9600
}
```

### De `loop()` functie

De `loop()` functie is het hart van elk Arduino-programma. Deze functie wordt herhaaldelijk uitgevoerd nadat de `setup()` functie is voltooid. Het bevat de hoofdlogica van het programma en wordt continu uitgevoerd zolang het Arduino-bord is ingeschakeld.

Hier is een voorbeeld van hoe de `loop()` functie eruit kan zien:

```cpp
void loop() {
    // Hoofdprogrammalogica
    digitalWrite(13, HIGH); // Zet pin 13 aan
    delay(1000);             // Wacht 1 seconde
    digitalWrite(13, LOW);  // Zet pin 13 uit
    delay(1000);             // Wacht 1 seconde
}
```
# Hoofdstuk 2: Variabelen en Datatypes

In dit hoofdstuk zullen we de basisprincipes van het aanmaken van variabelen met verschillende datatypes in Arduino-programmering verkennen.

## 2.1 Variabelen en hun types

Variabelen in Arduino-programmering zijn symbolische namen voor geheugenlocaties waarin gegevens kunnen worden opgeslagen en gewijzigd tijdens de uitvoering van het programma. Het type van een variabele bepaalt welk soort gegevens het kan bevatten.

### bool

Het `bool` datatype vertegenwoordigt een logische waarde die waar (`true`) of onwaar (`false`) kan zijn. Dit datatype wordt vaak gebruikt voor het opslaan van binaire informatie, zoals aan/uit- of ja/nee-staten.

```cpp
bool isLEDOn = true; // Definieer een bool variabele genaamd isLEDOn en wijs de waarde true toe
```

### int
Het `int` datatype wordt gebruikt voor het opslaan van gehele getallen zonder decimale punten. Het kan zowel positieve als negatieve gehele getallen opslaan.Het gegevenstype `int` een bereik van -32 768 tot 32 767.

```cpp
int sensorValue = 0; // Definieer een int variabele genaamd sensorValue en wijs de waarde 0 toe
```

### float
Het `float` datatype wordt gebruikt voor het opslaan van getallen met een decimaal punt, ook wel bekend als kommagetallen.

```cpp
float temperature = 25.5; // Definieer een float variabele genaamd temperature en wijs de waarde 25.5 toe
```

## 2.2 Variabelen declareren en initialiseren
Om een variabele in Arduino te gebruiken, moet deze worden gedeclareerd met een datatype en een unieke naam. De variabele kan vervolgens worden geïnitialiseerd met een beginwaarde, indien nodig.

Voorbeeld
```cpp
int ledPin = 13; // Declareer een int variabele genaamd ledPin en wijs de waarde 13 toe als pinnummer
```
# Hoofdstuk 3: Operatoren

**Operatoren** worden gebruikt om verschillende bewerkingen uit te voeren op gegevens, variabelen of expressies, afhankelijk van het type operator en de gegeven context.

Hier zijn enkele veelvoorkomende soorten operatoren:

##### Rekenkundige operatoren:
- **+** (optelling): Voegt twee waarden samen.
- **-** (aftrekking): Trekt de ene waarde af van de andere.
- **\*** (vermenigvuldiging): Vermenigvuldigt twee waarden.
- **/** (deling): Deelt de ene waarde door de andere.
##### Toekenningsoperatoren:
- **=** (toekenning): Wijs een waarde toe aan een variabele.
- **+=**, **-=**, **\*=**, **/=** (samengestelde toekenning): Voer een bewerking uit en wijs het resultaat toe aan de variabele.
##### Vergelijkingsoperatoren:
- **==** (gelijk aan): Test of twee waarden gelijk zijn.
- **!=** (niet gelijk aan): Test of twee waarden ongelijk zijn.
- **<**, **<=**, **>**, **>=** (vergelijking): Test of de ene waarde kleiner dan, kleiner dan of gelijk aan, groter dan, of groter dan of gelijk aan de andere waarde is.
##### Logische operatoren:
- **&&** (logische EN): Test of beide voorwaarden waar zijn.
- **||** (logische OF): Test of ten minste één van de voorwaarden waar is.
- **!** (logische NIET): Negatie van een voorwaarde.
##### Bitwise operatoren:
- **&** (bitwise EN): Voert een bitwise AND-bewerking uit.
- **|** (bitwise OF): Voert een bitwise OR-bewerking uit.
- **^** (bitwise XOR): Voert een bitwise XOR-bewerking uit.
- **<<** (bitwise linksverschuiving): Verschuift de bits naar links.
- **>>** (bitwise rechtsverschuiving): Verschuift de bits naar rechts.

# Hoofdstuk 4: Functies in Arduino-programmering

Functies in Arduino-programmering stellen ons in staat om stukken code te organiseren en te hergebruiken. In dit hoofdstuk zullen we leren hoe functies moeten worden opgebouwd en hoe variabelen kunnen worden doorgegeven aan of geretourneerd vanuit functies.

## 4.1 De opbouw van een functie

Een functie in Arduino-programmering bestaat uit een functiekop en een functieblok. De functiekop definieert de naam van de functie, het retourtype (indien van toepassing) en eventuele parameters die de functie accepteert. Het functieblok bevat de uitvoerbare code van de functie.

Een voorbeeld van de opbouw van een functie:

```cpp
// Functiekop
int addNumbers(int a, int b) {
    // Functieblok
    int result = a + b;
    return result;
}
```
In dit voorbeeld is addNumbers de naam van de functie, int is het retourtype, en int a en int b zijn de parameters die de functie accepteert.

## 4.2 Functies met parameters
Functies kunnen parameters accepteren, waardoor ze kunnen worden aangeroepen met verschillende waarden. Parameters worden gedefinieerd tussen de haakjes van de functiekop.

Een voorbeeld van een functie met parameters:

```cpp
void blinkLED(int pinNumber, int duration) {
    digitalWrite(pinNumber, HIGH);
    delay(duration);
    digitalWrite(pinNumber, LOW);
    delay(duration);
}
```
In dit voorbeeld accepteert de functie blinkLED twee parameters: pinNumber en duration.

## 4.3 Functies met retourwaarden
Functies kunnen ook retourwaarden teruggeven aan de code die ze heeft aangeroepen. Het retourtype van de functie wordt gedefinieerd in de functiekop, en de return-instructie wordt gebruikt om een waarde terug te geven.

Een voorbeeld van een functie met een retourwaarde:

```cpp
int calculateSum(int a, int b) {
    int sum = a + b;
    return sum;
}
```
In dit voorbeeld retourneert de functie calculateSum het resultaat van de optelling van a en b.

## Hoofdstuk 5: Printen met **Serial**

**'Serial'** is een *ingebouwde klasse* die wordt gebruikt voor *seriële communicatie*. We gaan momenteel niet dieper in op het *concept* 'klasse' maar je kan het beschouwen als een apart programma dat in andere programma's kan gebruikt worden. Alles wat behoort tot de **Serial**-klasse begint met **'Serial.'** met daar een fuctie-naam (en haakjes) achter. Een *functie* van een *klasse* noemen we **'methode'**. 
In Arduino wordt Serial gebruikt om toegang te krijgen tot de seriële interface van de Arduino-board, waarmee je gegevens kunt verzenden en ontvangen via de seriële poort (USB-poort) van het board.

Als klasse biedt **Serial** verschillende *methoden* voor het initiëren van de seriële communicatie, het verzenden en ontvangen van gegevens, en het configureren van de seriële poort. Enkele veelgebruikte *methoden* zijn: 
- **begin()**, dit is voor de initiële configuratie. Voordat je Serial kunt gebruiken, moet je het initiëren met een bepaalde baudrate (de snelheid van communiceren in bits per seconde). De bautrate van zender en ontvanger moet op dezelfde waarde staan. Langs de kant van de Arduino kan dit worden gedaan in de setup()-functie met de begin()-methode, bijvoorbeeld *Serial.begin(9600);*.
- **print()**, je kunt gegevens verzenden naar de seriële poort of *printen* in de *serial monitor* van de *Arduino IDE* op je computer. Met de *Serial.print()* methode kunnen variabelen, tekst of andere gegevens verzonden worden. 
- **println()** doet hetzelfde als de Serial.print() methode maar zorgt dat hij **na** de geprinte gegevens naar de volgende lijn sprint. Hierdoor zal de volgende print() of println() vanop een nieuwe lijn geprint worden.

Hier is een eenvoudig voorbeeld van het gebruik van de Serial-klasse in Arduino:

```cpp
void setup() {
    // Initialize serial communication with a baud rate of 9600
    Serial.begin(9600);
}

void loop() {
    // Print "Hello, World!" to the serial monitor
    Serial.println("Hello, World!");
    delay(1000); // Wait for 1 second
}
```
In dit voorbeeld wordt de **Serial**-klasse gebruikt om de tekst **"Hello, World!"** naar de seriële monitor te verzenden met behulp van de println()-methode. De seriële communicatie wordt eerst geïnitialiseerd in de setup()-functie met de begin()-methode.

## Hoofdstuk 6: Control flow statements (Controlestructuren)

In dit hoofdstuk zullen we leren hoe we de uitvoeringsstroom van een Arduino-programma kunnen beheren met behulp van control flow statements. Control flow statements stellen ons in staat om beslissingen te nemen en herhalingen uit te voeren, wat essentieel is voor het creëren van complexe en dynamische programma's.

### 6.1. Het if-statement

##### Beschrijving en doel:

Het **if**-statement is een van de meest fundamentele controlestructuren in Arduino-programmering.
Het doel ervan is om een bepaalde *codeblok* uit te voeren als een bepaalde *voorwaarde* waar is.
Het stelt ons in staat om beslissingen te nemen in ons programma op basis van de huidige toestand van variabelen of andere gegevens.

##### Voorbeeld:

```cpp
if (condition) {
    // Code die wordt uitgevoerd als de voorwaarde waar is
}
```
Het *keyword* **if** wordt gevolgd door een *voorwaarde* tussen haakjes ( ).
Als de voorwaarde *waar* is, wordt het daaropvolgende *codeblok* tussen de accolades { } uitgevoerd.
Als de voorwaarde *onwaar* is, wordt het *codeblok* overgeslagen en gaat het programma verder met de volgende instructie na het **if**-statement.
##### Voorbeelden:

```cpp
int sensorValue = analogRead(A0);

// Controleer of de sensorwaarde groter is dan een bepaalde drempelwaarde
if (sensorValue > 500) {
    digitalWrite(LED_BUILTIN, HIGH);  // Schakel de LED aan als de sensorwaarde groter is dan 500
}
```
In dit voorbeeld wordt de waarde van een analoge sensor gelezen en opgeslagen in *sensorValue*.
Het **if**-statement controleert of *sensorValue* groter is dan 500.
Als dat het geval is, wordt de ingebouwde LED op het Arduino-bordje ingeschakeld.

##### Gebruik van logische operatoren:

Naast eenvoudige voorwaarden, kunnen we ook complexere voorwaarden samenstellen met logische operatoren.
De meest gebruikte logische operatoren zijn:
**&&** (logische **EN**): Geeft *waar* als beide voorwaarden waar zijn.
**||** (logische **OF**): Geeft *waar* als minstens één van de voorwaarden waar is.
**!** (logische **NIET**): Geeft de omgekeerde waarde van de voorwaarde.
##### Voorbeeld van logische operatoren:

```cpp
int temperature = 25;
int humidity = 70;

// Controleer of zowel de temperatuur hoger is dan 20 graden Celsius en de luchtvochtigheid hoger is dan 60%
if ((temperature > 20) && (humidity > 60)) {
    // Voer code uit als de temperatuur hoger is dan 20 graden en de luchtvochtigheid hoger is dan 60%
}
```
In dit voorbeeld wordt hey **if**-statement gebruikt in combinatie met de logische **EN**-operator (&&) om te controleren of zowel de temperatuur hoger is dan 20 graden Celsius als de luchtvochtigheid hoger is dan 60%.
Dit geeft je een goed startpunt om het **if**-statement te begrijpen en te gebruiken in Arduino-programmering, evenals het gebruik van logische operatoren om complexere voorwaarden te evalueren. Het is een goede gewoonte om iedere voorwaarde apart tussen haakjes te zetten.

### 6.2. Het else-statement

##### Beschrijving en doel:

Het **else**-statement wordt gebruikt als aanvulling op een **if**-statement en wordt uitgevoerd als de voorwaarde van het **if**-statement onwaar is. Hiermee kan je een alternatief *uitvoeringspad* definiëren voor wanneer de voorwaarde van het **if**-statement niet waar is.

##### Voorbeeld:
```cpp
int sensorValue = analogRead(A0);

// Controleer of de sensorwaarde groter is dan een bepaalde drempelwaarde
if (sensorValue > 500) {
    digitalWrite(LED_BUILTIN, HIGH);  // Schakel de LED aan als de sensorwaarde groter is dan 500
} else {
    digitalWrite(LED_BUILTIN, LOW);   // Schakel de LED uit als de sensorwaarde niet groter is dan 500
}
```
In dit voorbeeld wordt het **if**-statement gebruikt om te controleren of *sensorValue* groter is dan 500.
Als dat het geval is, wordt de ingebouwde LED ingeschakeld.
Als de voorwaarde niet *waar* is, wordt het **else**-statement uitgevoerd en wordt de LED uitgeschakeld.
#### Combinatie van meerdere if- en else-statements:

We kunnen **if**- en **else**-statements combineren om meerdere alternatieve uitvoeringspaden te definiëren.
Hierdoor kunnen we verschillende acties ondernemen op basis van verschillende voorwaarden.
Voorbeeld van het combineren van **if**- en **else**-statements:

```cpp
int sensorValue = analogRead(A0);

// Controleer de sensorwaarde en voer verschillende acties uit op basis van de waarde
if (sensorValue > 750) {
    // Voer code uit als de sensorwaarde groter is dan 750
} else if (sensorValue > 500) {
    // Voer code uit als de sensorwaarde tussen 500 en 750 ligt
} else {
    // Voer code uit als de sensorwaarde 500 of minder is
}
```
In dit voorbeeld wordt de *sensorwaarde* gecontroleerd en worden verschillende acties uitgevoerd op basis van de waarde.
Als de *sensorwaarde* groter is dan 750, wordt de eerste *codeblok* uitgevoerd.
Als de *sensorwaarde* tussen 500 en 750 ligt, wordt de tweede *codeblok* uitgevoerd.
Als geen van de bovenstaande voorwaarden *waar* is, wordt het laatste *codeblok* uitgevoerd.

### 6.3 De while-loop
##### Beschrijving en doel:

De **while**-loop is een *controlestructuur* die wordt gebruikt om een blok code herhaaldelijk uit te voeren zolang een bepaalde voorwaarde *waar* is.
Het doel ervan is om herhaalde taken uit te voeren zolang de voorwaarde geldig blijft, waardoor de flexibiliteit en controle van je programma wordt vergroot.

##### Voorbeeld:

```cpp
while (condition) {
    // Code die herhaaldelijk wordt uitgevoerd zolang de voorwaarde waar is
}
```
Het *keyword* **while** wordt gevolgd door een voorwaarde tussen haakjes ( ).
Zolang deze voorwaarde *waar* is, wordt het daaropvolgende *codeblok* tussen de accolades { } herhaaldelijk uitgevoerd.
Als de voorwaarde *onwaar* wordt, wordt de uitvoering van de loop gestopt en gaat het programma verder met de volgende instructie na de while-loop.
##### Voorbeeld:

```cpp
int count = 0;

// Voer een lus uit zolang count kleiner is dan 5
while (count < 5) {
    Serial.println(count);
    count++; // Verhoog de waarde van count met 1 bij elke iteratie
    delay(1000); // Wacht 1 seconde tussen elke iteratie
}
```
In dit voorbeeld wordt een **while**-loop gebruikt om de waarde van count af te drukken en te verhogen totdat deze 5 bereikt.
De loop wordt herhaaldelijk uitgevoerd zolang count kleiner is dan 5.
Bij elke iteratie wordt de waarde van count met 1 verhoogd, en er wordt een vertraging van 1 seconde (delay(1000)) toegepast tussen elke iteratie.
Opmerking:

Het is belangrijk om ervoor te zorgen dat de voorwaarde van een **while**-loop op een gegeven moment onwaar wordt, anders kan de loop in een *oneindige lus* terechtkomen en komt het programma vast te zitten.
Zorg ervoor dat de voorwaarde wordt bijgewerkt binnen de loop, zodat deze op enig moment onwaar wordt en de uitvoering van de loop eindigt.

### 6.4 De for-loop
##### Beschrijving en doel:

- De **for**-loop is een controlestructuur die wordt gebruikt om een blok code herhaaldelijk uit te voeren voor een specifiek aantal keren.
- Het doel ervan is om herhaalde taken uit te voeren waarbij de iteratie expliciet wordt gecontroleerd, waardoor het gemakkelijker wordt om te werken met sequentiële gegevens of om een specifiek aantal iteraties uit te voeren.

##### Syntax in Arduino:

```cpp
for (initialization; condition; update) {
    // Code die herhaaldelijk wordt uitgevoerd zolang de voorwaarde waar is
}
```
De **for**-loop bestaat uit drie delen gescheiden door puntkomma's:
- **initialization**: Een uitdrukking die wordt uitgevoerd aan het begin van elke iteratie om een variabele te initialiseren of andere voorbereidende taken uit te voeren.
- **condition**: Een voorwaarde die wordt gecontroleerd aan het begin van elke iteratie. Zolang deze voorwaarde waar is, wordt het codeblok uitgevoerd. Als de voorwaarde onwaar wordt, wordt de loop beëindigd.
- **update**: Een uitdrukking die wordt uitgevoerd aan het einde van elke iteratie om de variabele te updaten of andere aanpassingen uit te voeren.

Voorbeelden:

```cpp
// Druk de getallen 0 tot en met 4 af
for (int i = 0; i < 5; i++) {
    Serial.println(i);
}
```
In dit voorbeeld wordt een **for**-loop gebruikt om de getallen 0 tot en met 4 af te drukken.
- De variabele **i** wordt *geïnitialiseerd* op 0.
- De loop wordt herhaald zolang **i** *kleiner is dan 5*.
- Na elke iteratie wordt de waarde van **i** *met 1 verhoogd* (**i++**).

Opmerking:

De for-loop is bijzonder handig wanneer je een bekend aantal iteraties hebt of wanneer je wilt itereren over sequentiële gegevens, zoals arrays *(dit leren we binnenkort nog)*.
Zorg ervoor dat je de variabelen initialiseert, de voorwaarde controleert en de update uitvoert op een manier die logisch en correct is om onverwacht gedrag te voorkomen.

### 6.5 De switch-case-structuur

##### Beschrijving en doel:

- De switch-case-structuur is een controlestructuur die wordt gebruikt om een blok code uit te voeren op basis van de waarde van een enkele variabele of expressie.
- Het wordt vaak gebruikt wanneer je meerdere mogelijke waarden wilt controleren en verschillende acties wilt uitvoeren op basis van deze waarden.
- Het biedt een alternatief voor het opeenvolgend gebruiken van meerdere if-else if-statements, waardoor je code overzichtelijker kan worden.

##### Syntax in Arduino:

```cpp
switch (expression) {
    case value1:
        // Code die wordt uitgevoerd als expression gelijk is aan value1
        break;
    case value2:
        // Code die wordt uitgevoerd als expression gelijk is aan value2
        break;
    // Voeg meer cases toe indien nodig
    default:
        // Code die wordt uitgevoerd als geen van de bovenstaande cases overeenkomt
        break;
}
```

- Het *keyword* **'switch'** wordt gevolgd door een *expressie* tussen haakjes ( ), bijvoorbeeld een variabele.
- Elke **'case'** bevat een mogelijke waarde die wordt vergeleken met de *expressie*.
- Als de *expressie* gelijk is aan de waarde in een **'case'**, wordt de bijbehorende code uitgevoerd.
- Het **break**-statement wordt gebruikt om de **switch**-**case**-structuur te verlaten en de uitvoering van de code te stoppen.
- Het **default**-*keyword* wordt gebruikt om een standaardactie op te geven als **geen** van de andere cases overeenkomt.

##### Voorbeelden:

```cpp
int key = 2;

// Controleer de waarde van de sleutel en voer verschillende acties uit op basis van de waarde
switch (key) {
    case 1:
        Serial.println("De sleutel is 1");
        break;
    case 2:
        Serial.println("De sleutel is 2");
        break;
    case 3:
        Serial.println("De sleutel is 3");
        break;
    default:
        Serial.println("Ongeldige sleutel");
        break;
}
```
In dit voorbeeld wordt de waarde van de *variabele* **key** gecontroleerd en worden verschillende acties uitgevoerd op basis van de waarde.
Als **key** gelijk is aan 1, 2 of 3, wordt een bijbehorende boodschap afgedrukt.
Als **key** geen van deze waarden heeft, wordt de boodschap "Ongeldige sleutel" afgedrukt.


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

# Hoofdstuk 2: Pinnen en de bijhorende Arduino functies

## 2.1 Inleiding tot de Arduino pinnen

Pinnen op een Arduino-board zijn fysieke aansluitingen die kunnen worden gebruikt om gegevens te verzenden en ontvangen van externe apparaten. Elk pin heeft een uniek nummer dat wordt gebruikt om deze te identificeren in de code. Afhankelijk van het type board zijn er digitale pinnen (die alleen aan of uit kunnen staan) en analoge pinnen (die variabele spanningen kunnen meten).

## 2.2 pinMode() functie

De **pinMode()** functie wordt gebruikt om de modus van een pin in te stellen als input of output. Deze functie heeft twee parameters: het pinnummer en de modus (INPUT of OUTPUT).

Voorbeeld:

```cpp
int ledPin = 13;
void setup() {
  pinMode(ledPin, OUTPUT); // Stel de pin 13 in als output
}
```
## 2.3 digitalWrite() functie

De **digitalWrite()** functie wordt gebruikt om een digitale pin in te schakelen (HIGH) of uit te schakelen (LOW). Deze functie heeft twee parameters: het pinnummer en de staat (HIGH of LOW).

Voorbeeld:

```cpp
int ledPin = 13;
void loop() {
  digitalWrite(ledPin, HIGH); // Schakel de LED aan
  delay(1000); // Wacht 1 seconde
  digitalWrite(ledPin, LOW); // Schakel de LED uit
  delay(1000); // Wacht 1 seconde
}
```
## 2.4 digitalRead() functie

De **digitalRead()** functie wordt gebruikt om de huidige staat van een digitale pin te lezen. Deze functie geeft **HIGH** terug als de pin actief is (hoog) en **LOW** als de pin inactief is (laag).

Voorbeeld:

```cpp
int switchPin = 2;
void loop() {
  int state = digitalRead(switchPin); // Lees de staat van de schakelaar
  if (state == HIGH) {
    // Voer actie uit als de schakelaar is ingedrukt
  }
}
```
## 2.5 analogRead() functie

De **analogRead()** functie wordt gebruikt om de analoge waarde te lezen van een analoge pin. Deze functie geeft een getal tussen 0 en 1023 terug, dat overeenkomt met een spanning tussen 0V en 5V (voor een standaard Arduino UNO-board).

Voorbeeld:

```cpp
int sensorPin = A0;
void loop() {
  int sensorValue = analogRead(sensorPin); // Lees de waarde van de sensor
}
```
## 2.6 analogWrite() functie

De **analogWrite()** functie wordt gebruikt om een **PWM** (Pulse Width Modulation) signaal uit te sturen op een PWM-compatibele pin. Deze functie heeft twee parameters: het **pinnummer** en de gewenste **duty cycle** (een waarde tussen 0 en 255, waarbij 0 de pin volledig uitschakelt en 255 de pin volledig inschakelt).

Voorbeeld:

```cpp
int ledPin = 9;
void loop() {
  analogWrite(ledPin, 128); // Stel de helderheid van de LED in op de helft
}
```
Dit hoofdstuk geeft een allereerste basis overzicht over het gebruik van pinnen op een Arduino-board en de bijbehorende functies om ze te bedienen. Met deze functies kun je digitale en analoge pinnen configureren, hun toestand lezen en schrijven, en PWM-signalen genereren voor taken zoals het regelen van de helderheid van een LED. Afhankelijke van het type Arduino-bord en de gebruikte micro controller, kunnen er verschillen zijn bij het bebruik van analogRead en analogWrite.

# Hoofdstuk 3: Variabelen en Datatypes

In dit hoofdstuk zullen we de basisprincipes van het aanmaken van variabelen met verschillende datatypes in Arduino-programmering verkennen.

## 3.1 Variabelen en hun types

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

## 3.2 Variabelen declareren en initialiseren
Om een variabele in Arduino te gebruiken, moet deze worden gedeclareerd met een datatype en een unieke naam. De variabele kan vervolgens worden geïnitialiseerd met een beginwaarde, indien nodig.

Voorbeeld
```cpp
int ledPin = 13; // Declareer een int variabele genaamd ledPin en wijs de waarde 13 toe als pinnummer
```
# Hoofdstuk 4: Operatoren

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

# Hoofdstuk 5: Functies in Arduino-programmering

Functies in Arduino-programmering stellen ons in staat om stukken code te organiseren en te hergebruiken. In dit hoofdstuk zullen we leren hoe functies moeten worden opgebouwd en hoe variabelen kunnen worden doorgegeven aan of geretourneerd vanuit functies.

## 5.1 De opbouw van een functie

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

## 5.2 Functies met parameters
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

## 5.3 Functies met retourwaarden
Functies kunnen ook retourwaarden teruggeven aan de code die ze heeft aangeroepen. Het retourtype van de functie wordt gedefinieerd in de functiekop, en de return-instructie wordt gebruikt om een waarde terug te geven.

Een voorbeeld van een functie met een retourwaarde:

```cpp
int calculateSum(int a, int b) {
    int sum = a + b;
    return sum;
}
```
In dit voorbeeld retourneert de functie calculateSum het resultaat van de optelling van a en b.

## Hoofdstuk 6: Printen met **Serial**

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

## Hoofdstuk 7: Control flow statements (Controlestructuren)

In dit hoofdstuk zullen we leren hoe we de uitvoeringsstroom van een Arduino-programma kunnen beheren met behulp van control flow statements. Control flow statements stellen ons in staat om beslissingen te nemen en herhalingen uit te voeren, wat essentieel is voor het creëren van complexe en dynamische programma's.

### 7.1. Het if-statement

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

### 7.2. Het else-statement

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

### 7.3 De while-loop
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

### 7.4 De for-loop
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

### 7.5 De switch-case-structuur

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

# Hoofdstuk 8: Arrays in Arduino

## 8.1 Inleiding tot Arrays

Een **array** is een datatype waarmee je meerdere waarden van hetzelfde gegevenstype kunt opslaan in één variabele. In Arduino worden arrays vaak gebruikt om een verzameling van gegevens, zoals sensorwaarden, op te slaan, of om meerdere LED's of andere componenten te beheren. Array kan je vertalen als 'rij' of 'reeks'.

## 8.2 Declaratie en Initialisatie van Arrays

In Arduino kun je een array declareren en initialiseren met de gewenste grootte en gegevens. Hier is een voorbeeld van hoe je een array van integers declareert en initialiseren:

```cpp
int sensorValues[5] = {0, 10, 20, 30, 40}; // Een array van 5 integers
In dit voorbeeld hebben we een array sensorValues gemaakt met 5 elementen, en we hebben deze geïnitialiseerd met de waarden 0, 10, 20, 30 en 40.
```

## 8.3 Toegang tot Elementen van een Array

Je kunt individuele elementen van een array benaderen door hun index te gebruiken. De index begint meestal bij 0 voor het eerste element en gaat verder tot de grootte van de array minus één. Hier is hoe je toegang krijgt tot een element van een array:

```cpp
int value = sensorValues[2]; // Toegang tot het derde element van de array (index 2)
```
In dit voorbeeld krijgt value de waarde 20, omdat dit het derde element is van de array sensorValues.

## 8.4 Itereren over een Array

Je kunt een loop gebruiken om door alle elementen van een array te itereren en ze één voor één te verwerken. Dit kan handig zijn als je alle sensorwaarden wilt afdrukken of als je alle LED's in een array wilt inschakelen. Hier is een voorbeeld van hoe je over een array kunt itereren:

```cpp
for (int i = 0; i < 5; i++) {
  Serial.println(sensorValues[i]); // Druk elk element van de array af
}
```
In dit voorbeeld gebruiken we een for-loop om door elk element van de array sensorValues te itereren en de waarde ervan af te drukken naar de seriële monitor.

## 8.5 Een Array gebruiken om pinnen te sturen

Laten we een voorbeeld maken van hoe je pinnummers in een array kunt plaatsen en vervolgens een looplicht kunt maken met behulp van iteratie. Laten we zeggen dat we een looplicht willen maken met LED's die zijn aangesloten op pinnen 2 tot en met 7 op een Arduino-bord. Hier is hoe je dat kunt doen:

```cpp
// Definieer de pinnen voor het looplicht
int ledPins[] = {2, 3, 4, 5, 6, 7};
int numberOfLEDs = sizeof(ledPins) / sizeof(ledPins[0]);

void setup() {
  // Configureer alle pinnen als uitgang
  for (int i = 0; i < numberOfLEDs; i++) {
    pinMode(ledPins[i], OUTPUT);
  }
}

void loop() {
  // Schakel elk LED aan en uit in een loop
  for (int i = 0; i < numberOfLEDs; i++) {
    digitalWrite(ledPins[i], HIGH); // Schakel LED aan
    delay(100); // Wacht 100 milliseconden
    digitalWrite(ledPins[i], LOW); // Schakel LED uit
  }
}
```
In dit voorbeeld hebben we een array ledPins gemaakt die de pinnen bevat waarop onze LED's zijn aangesloten. We hebben ook een variabele **numberOfLEDs** gedefinieerd om het aantal LED's in de array te bepalen.

In de **setup()**-functie worden alle pinnen geconfigureerd als uitgangen met behulp van een **for-loop** die over de ledPins array itereert.

In de **loop()**-functie gebruiken we opnieuw een **for-loop** om door elke pin in de ledPins array te itereren. We schakelen elke **LED** afwisselend aan en uit met behulp van **digitalWrite()** en **delay()** om een looplichteffect te creëren.

Dit voorbeeld demonstreert hoe je pinnen in een array kunt plaatsen en vervolgens kunt itereren over de array om een reeks acties uit te voeren, zoals het aansturen van LED's in dit geval.

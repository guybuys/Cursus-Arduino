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

# Hoofdstuk 3: Functies in Arduino-programmering

Functies in Arduino-programmering stellen ons in staat om stukken code te organiseren en te hergebruiken. In dit hoofdstuk zullen we leren hoe functies moeten worden opgebouwd en hoe variabelen kunnen worden doorgegeven aan of geretourneerd vanuit functies.

## 3.1 De opbouw van een functie

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

## 3.2 Functies met parameters
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

## 3.3 Functies met retourwaarden
Functies kunnen ook retourwaarden teruggeven aan de code die ze heeft aangeroepen. Het retourtype van de functie wordt gedefinieerd in de functiekop, en de return-instructie wordt gebruikt om een waarde terug te geven.

Een voorbeeld van een functie met een retourwaarde:

```cpp
int calculateSum(int a, int b) {
    int sum = a + b;
    return sum;
}
```
In dit voorbeeld retourneert de functie calculateSum het resultaat van de optelling van a en b.

## 3.4 Samenvatting
Functies zijn een essentieel concept in Arduino-programmering waarmee we code kunnen organiseren en hergebruiken. We hebben geleerd hoe functies moeten worden opgebouwd, hoe parameters kunnen worden doorgegeven aan functies, en hoe functies retourwaarden kunnen teruggeven aan de code die ze heeft aangeroepen.

Copy code

Dit hoofdstuk legt uit hoe functies in Arduino-programmering worden gebruikt, inclusief hun opbouw, het doorgeven van parameters, en het retourneren van waarden. Je kunt dit voorbeeld uitbreiden met meer uitleg, voorbeelden en oefeningen om de leerervaring te verbeteren.





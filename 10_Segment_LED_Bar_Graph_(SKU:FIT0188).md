---
title: 10 Segment LED Bar Graph (SKU:FIT0188)
permalink: /10_Segment_LED_Bar_Graph_(SKU:FIT0188)/
---

[200px|thumb|link=<https://www.dfrobot.com/product-636.html>| [10 Segment LED Bar Graph](https://www.dfrobot.com/product-636.html)](/File:10LEDBarGraph.jpg "wikilink")

Introduction
------------

These 10 segment bar graph LEDs have many uses. With a compact footprint, and a simple hookup, they are easy for prototyping or finished products. Essentially, they are 10 individual red LEDs housed together.

### Applications

-   Audio equipment
-   Instrument panels
-   Digital readout display
-   Signal strength display
-   Power status display
-   Art display

### Specification

-   Forward Current (Per Segment): 25mA
-   Max Reverse Voltage: 5v
-   10 segment bar
-   Color: Super Bright Red
-   Industrial standard size
-   Low power consumption
-   Categorized for luminous intensity

### Shipping List

-   10 segment led bar graph - Red (1 unit)

Connection Diagram
------------------

[700px|thumb|center| 10 Segment LED Bar Graph Connection](/File:FIT0188_Connection.png "wikilink")

Please note that the connection diagram shows the pins connected in reverse order for the sake of clarity. When you run the sample code included here you might notice a reverse order sequence. If you wish to wire the LEDs in the correct order you should wire:
Arduino D2 to PIN1
Arduino D3 to PIN2
Arduino D4 to PIN3
Arduino D5 to PIN4
and so on...
Alternatively you could modify the sample code to operate in the expected order.

Sample Code
-----------

~~~~ {.cpp}
// #
// # Editor     : Lauren from DFRobot
// # Date       : 19.03.2012

// # Product name: 10 Segment LED Bar Graph
// # Product SKU : FIT0188
// # Version     : 1.0

// # Description:
// # The sketch for using the 10 Segment LED Bar Graph with prototype shield

// # Connection:
// #        LED Bar positive pins -- Arduino digital pins through a 1K resistor
// #        LED Bar negative pins -- GND

const int ledPin[10] =  {
  2,3,4,5,6,9,10,11,12,13};      // the number of the LED pins
int ledState = 0;

void setup() {
  Serial.begin(9600);
  // set the digital pin as output:
  for(int i = 0; i < 10 ;i ++){
    pinMode(ledPin[i], OUTPUT);
    digitalWrite(ledPin[i], LOW);
  }
  ledState = 1;
  display(ledState);
  delay(100);
}

void loop()
{
  for(int i = 0; i < 9; i++){
    ledState = ledState << 1;
    display(ledState);
    delay(50);
    Serial.println(ledState,BIN);
  }
  for(int i = 9; i > 0; i--){
    ledState = ledState >> 1;
    display(ledState);
    delay(50);
    Serial.println(ledState,BIN);
  }
}

void display(int sat){
  for(int i = 0; i < 10 ;i ++){
    digitalWrite(ledPin[i],bitRead(ledState,i));
  }
}
~~~~
<img src="https://www.dfrobot.com/wiki/images/thumb/4/47/DRI0027_Diagram.png/550px-DRI0027_Diagram.png" alt="" style="max-width:100%;">
[image:nextredirectltr.pngGo](/image:nextredirectltr.png "wikilink") Shopping [10 Segment LED Bar Graph (SKU:FIT0188)](https://www.dfrobot.com/product-636.html)

Category: [DFRobot](https://www.dfrobot.com/) \> [Sensors & Modules](https://www.dfrobot.com/category-156.html) \> [LCDs, LEDs & Displays](https://www.dfrobot.com/category-53.html) \> [LEDs](https://www.dfrobot.com/category-131.html) [category: Product Manual](/category:_Product_Manual "wikilink") [category: FIT Series](/category:_FIT_Series "wikilink") [category: Components](/category:_Components "wikilink") [category: Source](/category:_Source "wikilink") [category: Diagram](/category:_Diagram "wikilink")

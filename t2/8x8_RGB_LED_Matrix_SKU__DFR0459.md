<p><img src="DFR0459.jpg" title="fig:DFR0459.jpg" alt="DFR0459.jpg" />]</p>
<h2 id="introduction">Introduction</h2>
<p>The 8x8 RGB LED Matrix! This module is a square panel with a XH2.54 3-pin interface.<br />This 8x8 RGB full-color LED matrix module is based on WS2812 intelligent control LEDs. Each LED can be independently addressed with RGB pixels that can achieve 256 levels of brightness. That’s 16777216 colors in total with a scanning frequency no less than 400Hz!<br />The 8x8 RGB LED Matrix is single wire control board. The module also supports cascading control. All you need to do is connect Din to the DOUT port. In combination with the open source Arduino library, you can control an entire array of LEDs using just one pin!<br /></p>
<table>
<tbody>
<tr class="odd">
<td align="left"><div class="figure">
<img src="warning_yellow.png" title="warning_yellow.png" alt="warning_yellow.png" /><p class="caption">warning_yellow.png</p>
</div></td>
<td align="left"><p>Note: Each LED requires a maximum current of 18mA. When multiple modules are in use, it is recommended to use external power supply to power multiple LEDs matrix.</p></td>
</tr>
</tbody>
</table>
<h2 id="features">Features</h2>
<ul>
<li>Full Color RGB</li>
<li>Supports Cascade Control</li>
<li>Supports External Power Supply</li>
</ul>
<h2 id="specification">Specification</h2>
<ul>
<li>Operating Voltage: 5V</li>
<li>LED Type: WS2812</li>
<li>Communication Interface: XH2.54 3Pin</li>
<li>Operating Temperature: -25 ~ +80 ℃</li>
<li>Dimension: 65 * 65 mm / 2.56 * 2.56 inches</li>
<li>Weight: 140g</li>
</ul>
<h2 id="board-overview">Board Overview</h2>
<table>
<tbody>
<tr class="odd">
<td align="left"><div class="figure">
<img src="Name_DFR0459_back.png" title="Name_DFR0459_back.png" alt="Name_DFR0459_back.png" /><p class="caption">Name_DFR0459_back.png</p>
</div></td>
<td align="left"><table>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Num</strong></p></td>
<td align="left"><p><strong>Label</strong></p></td>
<td align="left"><p><strong>Description</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>1</p></td>
<td align="left"><p>5V</p></td>
<td align="left"><p>Power +</p></td>
</tr>
<tr class="odd">
<td align="left"><p>2</p></td>
<td align="left"><p>GND</p></td>
<td align="left"><p>Power -</p></td>
</tr>
<tr class="even">
<td align="left"><p>3</p></td>
<td align="left"><p>DIN</p></td>
<td align="left"><p>Data IN</p></td>
</tr>
<tr class="odd">
<td align="left"><p>4</p></td>
<td align="left"><p>DOUT</p></td>
<td align="left"><p>Data OUT</p></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>
<p><br /></p>
<h2 id="tutorial">Tutorial</h2>
<p>In this tutorial, we'll show you how to light the Matrix in 5 minutes.<br />===Requirements===</p>
<ul>
<li><strong>Hardware</strong>
<ul>
<li><a href="https://www.dfrobot.com/index.php?route=product/product&amp;search=DFRduino&amp;description=true&amp;product_id=838">DFRduino UNO</a> x 1</li>
<li>8x8 RGB LED Matrix x1</li>
</ul></li>
</ul>
<ul>
<li><strong>Software</strong>
<ul>
<li>Arduino IDE (Version requirements: V1.6.?), [<a href="https://www.arduino.cc/en/Main/Software">https://www.arduino.cc/en/Main/Software</a>| Click to Download Arduino IDE from Arduino®]</li>
</ul></li>
</ul>
<p><br /></p>
<h3 id="connection-diagram">Connection Diagram</h3>
<p><img src="DFR0459_Conection.png" title="fig:DFR0459_Conection.png" alt="DFR0459_Conection.png" /><br /></p>
<h3 id="sample-code">Sample Code</h3>
<p>In this section, we'll use <a href="https://github.com/adafruit/Adafruit_NeoPixel">Adafruit_NeoPixel RGB LED Lbrary</a>. [<a href="https://www.arduino.cc/en/Guide/Libraries">https://www.arduino.cc/en/Guide/Libraries</a>#.UxU8mdzF9H0| How to install Libraries in Arduino IDE]</p>
<p><br /></p>
<pre class="Arduino"><code>#include &lt;Adafruit_NeoPixel.h&gt;
#ifdef __AVR__
  #include &lt;avr/power.h&gt;
#endif

#define PIN 6

// Parameter 1 = number of pixels in strip
// Parameter 2 = Arduino pin number (most are valid)
// Parameter 3 = pixel type flags, add together as needed:
//   NEO_KHZ800  800 KHz bitstream (most NeoPixel products w/WS2812 LEDs)
//   NEO_KHZ400  400 KHz (classic &#39;v1&#39; (not v2) FLORA pixels, WS2811 drivers)
//   NEO_GRB     Pixels are wired for GRB bitstream (most NeoPixel products)
//   NEO_RGB     Pixels are wired for RGB bitstream (v1 FLORA pixels, not v2)
//   NEO_RGBW    Pixels are wired for RGBW bitstream (NeoPixel RGBW products)
Adafruit_NeoPixel strip = Adafruit_NeoPixel(64, PIN, NEO_GRB + NEO_KHZ800);

// IMPORTANT: To reduce NeoPixel burnout risk, add 1000 uF capacitor across
// pixel power leads, add 300 - 500 Ohm resistor on first pixel&#39;s data input
// and minimize distance between Arduino and first pixel.  Avoid connecting
// on a live circuit...if you must, connect GND first.

void setup() {
  // This is for Trinket 5V 16MHz, you can remove these three lines if you are not using a Trinket
  #if defined (__AVR_ATtiny85__)
    if (F_CPU == 16000000) clock_prescale_set(clock_div_1);
  #endif
  // End of trinket special code


  strip.begin();
  strip.show(); // Initialize all pixels to &#39;off&#39;
}

void loop() {
  // Some example procedures showing how to display to the pixels:
  //colorWipe(strip.Color(255, 0, 0), 50); // Red
 // colorWipe(strip.Color(0, 255, 0), 50); // Green
  //colorWipe(strip.Color(0, 0, 255), 50); // Blue
//colorWipe(strip.Color(0, 0, 0, 255), 50); // White RGBW
  // Send a theater pixel chase in...
 // theaterChase(strip.Color(127, 127, 127), 50); // White
  //theaterChase(strip.Color(127, 0, 0), 50); // Red
  //theaterChase(strip.Color(0, 0, 127), 50); // Blue

  rainbow(20);
  //rainbowCycle(20);
  //theaterChaseRainbow(50);
}

// Fill the dots one after the other with a color
void colorWipe(uint32_t c, uint8_t wait) {
  for(uint16_t i=0; i&lt;strip.numPixels(); i++) {
    strip.setPixelColor(i, c);
    strip.show();
    delay(wait);
  }
}

void rainbow(uint8_t wait) {
  uint16_t i, j;

  for(j=0; j&lt;256; j++) {
    for(i=0; i&lt;strip.numPixels(); i++) {
      strip.setPixelColor(i, Wheel((i+j) &amp; 255));
    }
    strip.show();
    delay(wait);
  }
}

// Slightly different, this makes the rainbow equally distributed throughout
void rainbowCycle(uint8_t wait) {
  uint16_t i, j;

  for(j=0; j&lt;256*5; j++) { // 5 cycles of all colors on wheel
    for(i=0; i&lt; strip.numPixels(); i++) {
      strip.setPixelColor(i, Wheel(((i * 256 / strip.numPixels()) + j) &amp; 255));
    }
    strip.show();
    delay(wait);
  }
}

//Theatre-style crawling lights.
void theaterChase(uint32_t c, uint8_t wait) {
  for (int j=0; j&lt;10; j++) {  //do 10 cycles of chasing
    for (int q=0; q &lt; 3; q++) {
      for (uint16_t i=0; i &lt; strip.numPixels(); i=i+3) {
        strip.setPixelColor(i+q, c);    //turn every third pixel on
      }
      strip.show();

      delay(wait);

      for (uint16_t i=0; i &lt; strip.numPixels(); i=i+3) {
        strip.setPixelColor(i+q, 0);        //turn every third pixel off
      }
    }
  }
}

//Theatre-style crawling lights with rainbow effect
void theaterChaseRainbow(uint8_t wait) {
  for (int j=0; j &lt; 256; j++) {     // cycle all 256 colors in the wheel
    for (int q=0; q &lt; 3; q++) {
      for (uint16_t i=0; i &lt; strip.numPixels(); i=i+3) {
        strip.setPixelColor(i+q, Wheel( (i+j) % 255));    //turn every third pixel on
      }
      strip.show();

      delay(wait);

      for (uint16_t i=0; i &lt; strip.numPixels(); i=i+3) {
        strip.setPixelColor(i+q, 0);        //turn every third pixel off
      }
    }
  }
}

// Input a value 0 to 255 to get a color value.
// The colours are a transition r - g - b - back to r.
uint32_t Wheel(byte WheelPos) {
  WheelPos = 255 - WheelPos;
  if(WheelPos &lt; 85) {
    return strip.Color(255 - WheelPos * 3, 0, WheelPos * 3);
  }
  if(WheelPos &lt; 170) {
    WheelPos -= 85;
    return strip.Color(0, WheelPos * 3, 255 - WheelPos * 3);
  }
  WheelPos -= 170;
  return strip.Color(WheelPos * 3, 255 - WheelPos * 3, 0);
}                       </code></pre>
<p><br /></p>
<h3 id="expected-results">Expected Results</h3>
<h2 id="faq">FAQ</h2>
<table>
<tbody>
<tr class="odd">
<td align="left"><p>For any questions, advice or cool ideas to share, please visit the <a href="http://www.dfrobot.com/forum/"><strong>DFRobot Forum</strong></a>.</p></td>
</tr>
</tbody>
</table>
<p><br /></p>
<h2 id="more">More</h2>
<ul>
<li><a href="https://github.com/Arduinolibrary/RGB_LED_Matrix/raw/master/WS2812%20DataSheet.pdf">WS2812 Datasheet</a></li>
</ul>
<p><br /> <img src="DFshopping_car1.png" title="fig:DFshopping_car1.png" alt="DFshopping_car1.png" /> Shopping from <a href="https://www.dfrobot.com/product-1555.html"><strong><u>8x8 RGB LED Matrix</u></strong></a> or <a href="http://www.dfrobot.com/index.php?route=information/distributorslogo"><strong>DFRobot Distributor</strong>.</a></p>
<p><br /><br /></p>---
title: 8x8 RGB LED Matrix SKU: DFR0459
permalink: /8x8_RGB_LED_Matrix_SKU:_DFR0459/
---


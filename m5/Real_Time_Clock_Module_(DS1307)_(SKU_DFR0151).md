<p>![fig:DFR0151.jpg](https://github.com/DFRobot/DFRobotDocument/Real_Time_Clock_Module_(DS1307)_(SKU:DFR0151)/image/DFR0151.jpg  "DFR0151.jpg")==Sample Code==</p>
<pre class="sourceCode cpp"><code class="sourceCode cpp"><span class="co">// #############################################################################// #// # Scriptname : DS1307_Test.pde// # Author     : Peter Schmelzer, Oliver Kraus// # Date       : 2011-04-08// # Editor     : Lauren from DFRobot// # Date       : 30.12.2011// # Description:// # Test file for the DS1307new library. Assumes that you have a DS1307 // # connected to the I2C-Bus of your Arduino and that it has a battery backup.// # Update the library and sketch to compatible with IDE V1.0 and earlier// # Version    : 1.0// #############################################################################// *********************************************// INCLUDE// *********************************************#include &lt;Wire.h&gt;                       // For some strange reasons, Wire.h must be included here#include &lt;DS1307new.h&gt;// *********************************************// DEFINE// *********************************************// *********************************************// VARIABLES// *********************************************uint16_t startAddr = 0x0000;            // Start address to store in the NV-RAMuint16_t lastAddr;                      // new address for storing in NV-RAMuint16_t TimeIsSet = 0xaa55;            // Helper that time must not set again// *********************************************// SETUP// *********************************************void setup(){  pinMode(2, INPUT);                    // Test of the SQW pin, D2 = INPUT  digitalWrite(2, HIGH);                // Test of the SQW pin, D2 = Pullup on  Serial.begin(9600);/*   PLEASE NOTICE: WE HAVE MADE AN ADDRESS SHIFT FOR THE NV-RAM!!!                  NV-RAM ADDRESS 0x08 HAS TO ADDRESSED WITH ADDRESS 0x00=0                  TO AVOID OVERWRITING THE CLOCK REGISTERS IN CASE OF                  ERRORS IN YOUR CODE. SO THE LAST ADDRESS IS 0x38=56!*/  RTC.setRAM(0, (uint8_t *)&amp;startAddr, sizeof(uint16_t));// Store startAddr in NV-RAM address 0x08 /*   Uncomment the next 2 lines if you want to SET the clock   Comment them out if the clock is set.   DON&#39;T ASK ME WHY: YOU MUST UPLOAD THE CODE TWICE TO LET HIM WORK   AFTER SETTING THE CLOCK ONCE.*///  TimeIsSet = 0xffff;//  RTC.setRAM(54, (uint8_t *)&amp;TimeIsSet, sizeof(uint16_t));  /*  Control the clock.  Clock will only be set if NV-RAM Address does not contain 0xaa.  DS1307 should have a battery backup.*/  RTC.getRAM(54, (uint8_t *)&amp;TimeIsSet, sizeof(uint16_t));  if (TimeIsSet != 0xaa55)  {    RTC.stopClock();            RTC.fillByYMD(2011,4,8);    RTC.fillByHMS(22,7,0);        RTC.setTime();    TimeIsSet = 0xaa55;    RTC.setRAM(54, (uint8_t *)&amp;TimeIsSet, sizeof(uint16_t));    RTC.startClock();  }  else  {    RTC.getTime();  }/*   Control Register for SQW pin which can be used as an interrupt.*/  RTC.ctrl = 0x00;                      // 0x00=disable SQW pin, 0x10=1Hz,                                        // 0x11=4096Hz, 0x12=8192Hz, 0x13=32768Hz  RTC.setCTRL();  Serial.println(&quot;DS1307 Testsketch&quot;);  Serial.println(&quot;Format is \&quot;hh:mm:ss dd-mm-yyyy DDD\&quot;&quot;);  uint8_t MESZ;  MESZ = RTC.isMEZSummerTime();  Serial.print(&quot;MEZ=0, MESZ=1 : &quot;);  Serial.println(MESZ, DEC);      Serial.println();}// *********************************************// MAIN (LOOP)// *********************************************void loop(){  RTC.getTime();  if (RTC.hour &lt; 10)                    // correct hour if necessary  {    Serial.print(&quot;0&quot;);    Serial.print(RTC.hour, DEC);  }   else  {    Serial.print(RTC.hour, DEC);  }  Serial.print(&quot;:&quot;);  if (RTC.minute &lt; 10)                  // correct minute if necessary  {    Serial.print(&quot;0&quot;);    Serial.print(RTC.minute, DEC);  }  else  {    Serial.print(RTC.minute, DEC);  }  Serial.print(&quot;:&quot;);  if (RTC.second &lt; 10)                  // correct second if necessary  {    Serial.print(&quot;0&quot;);    Serial.print(RTC.second, DEC);  }  else  {    Serial.print(RTC.second, DEC);  }  Serial.print(&quot; &quot;);  if (RTC.day &lt; 10)                    // correct date if necessary  {    Serial.print(&quot;0&quot;);    Serial.print(RTC.day, DEC);  }  else  {    Serial.print(RTC.day, DEC);  }  Serial.print(&quot;-&quot;);  if (RTC.month &lt; 10)                   // correct month if necessary  {    Serial.print(&quot;0&quot;);    Serial.print(RTC.month, DEC);  }  else  {    Serial.print(RTC.month, DEC);  }  Serial.print(&quot;-&quot;);  Serial.print(RTC.year, DEC);          // Year need not to be changed  Serial.print(&quot; &quot;);  switch (RTC.dow)                      // Friendly printout the weekday  {    case 1:      Serial.print(&quot;MON&quot;);      break;    case 2:      Serial.print(&quot;TUE&quot;);      break;    case 3:      Serial.print(&quot;WED&quot;);      break;    case 4:      Serial.print(&quot;THU&quot;);      break;    case 5:      Serial.print(&quot;FRI&quot;);      break;    case 6:      Serial.print(&quot;SAT&quot;);      break;    case 7:      Serial.print(&quot;SUN&quot;);      break;  }  Serial.print(&quot; seconds since 1.1.2000:&quot;);  Serial.print(RTC.time2000, DEC);  uint8_t MESZ = RTC.isMEZSummerTime();  Serial.print(&quot; MEZ=0, MESZ=1 : &quot;);  Serial.print(MESZ, DEC);      Serial.print(&quot; - Address in NV-RAM is: &quot;);  RTC.getRAM(0, (uint8_t *)&amp;lastAddr, sizeof(uint16_t));  Serial.print(lastAddr, HEX);  lastAddr = lastAddr + 1;              // we want to use it as addresscounter for example  RTC.setRAM(0, (uint8_t *)&amp;lastAddr, sizeof(uint16_t));  RTC.getRAM(54, (uint8_t *)&amp;TimeIsSet, sizeof(uint16_t));  if (TimeIsSet == 0xaa55)              // check if the clock was set or not  {    Serial.println(&quot; - Clock was set!&quot;);  }  else  {    Serial.println(&quot; - Clock was NOT set!&quot;);  }      delay(1000);                          // wait a second}</span></code></pre>
<p>==Documentation==<a href="http://www.dfrobot.com/image/data/DFR0151/DS1307%20library%20v1.0(DFRobot).rar">Arduino Library (compatible with IDE version 1.0 and lower)</a><br /><a href="http://www.dfrobot.com/image/data/DFR0151/DFR0151.rar">Sample code, library, and wiring diagram</a><br /><br /><a href="image:nextredirectltr.png" title="wikilink">image:nextredirectltr.pngGo</a> Shopping <a href="https://www.dfrobot.com/product-511.html">Real Time Clock Module (DS1307) (SKU:DFR0151)</a><br /><br /><a href="category:_Product_Manual" title="wikilink">category: Product Manual</a><a href="category:_DFR_Series" title="wikilink">category: DFR Series</a><a href="category:_Modules" title="wikilink">category: Modules</a><a href="category:_source" title="wikilink">category: source</a><a href="category:_Diagram" title="wikilink">category: Diagram</a></p>---
title: Real Time Clock Module (DS1307) (SKU:DFR0151)
permalink: /Real_Time_Clock_Module_(DS1307)_(SKU:DFR0151)/
---


<h2 id="introduction">Introduction</h2>
<p><a href="image:sensors_for_arduino10.png" title="wikilink">thumbThe</a> <em>DFRobot Tilt Sensor</em> is a digital mercury-based tilt switch that is either closed, disconnected or open. The module is based on the number of mercury switches. The mercury flows to the low-lying and could therefore be used as a simple tilt sensor. The dedicated sensor expansion boards with the Arduino, in combination, can achieve very interesting and an interactive work.<em>Note: Mercury is a toxic substance, please be careful to avoid breaking the glass case.</em>==Specification==*Digital mercury-based tilt switch*Can be used as a simple tilt sensor==Pin Definition==Touch Sensor module pin definition ::#Input:#Power:#GND<a href="image:Tilt_Sensor.png" title="wikilink">thumb</a>==Connection Diagram==<a href="image:Tilt_Sensor_Connection_Diagram.png" title="wikilink">thumb</a>==Sample Code==</p>
<pre class="sourceCode cpp"><code class="sourceCode cpp"><span class="dt">int</span> ledPin = <span class="dv">13</span>;                <span class="co">// Connect LED to pin 13int switcher = 3;                 // Connect Tilt sensor to Pin3void setup(){  pinMode(ledPin, OUTPUT);      // Set digital pin 13 to output mode  pinMode(switcher, INPUT);       // Set digital pin 3 to input mode}void loop(){       if(digitalRead(switcher)==HIGH) //Read sensor value     {         digitalWrite(ledPin, HIGH);   // Turn on LED when the sensor is tilted     }   else     {        digitalWrite(ledPin, LOW);    // Turn off LED when the sensor is not triggered     }}</span></code></pre>
<p><br /><br /><a href="image:nextredirectltr.png" title="wikilink">image:nextredirectltr.pngGo</a> Shopping <a href="http://www.dfrobot.com/index.php?route=product/product&amp;keyword=dfr0028&amp;category_id=0&amp;description=1&amp;model=1&amp;product_id=77">DFRobot Tilt Sensor (SKU:DFR0028)</a><a href="category:_Product_Manual" title="wikilink">category: Product Manual</a><a href="category:_DFR_Series" title="wikilink">category: DFR Series</a><a href="category:_Sensors" title="wikilink">category: Sensors</a><a href="category:source" title="wikilink">category:source</a><a href="category:Diagram" title="wikilink">category:Diagram</a></p>---
title: DFRobot Tilt Sensor (SKU:DFR0028)
permalink: /DFRobot_Tilt_Sensor_(SKU:DFR0028)/
---

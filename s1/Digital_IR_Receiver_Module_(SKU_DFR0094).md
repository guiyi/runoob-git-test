<h2 id="introduction">Introduction</h2>
<p><a href="image:DFR0094.jpg" title="wikilink">thumb</a>]IR is widely used in remoter control. With this IR receiver, the Arduino project is able to receive command from any IR remoter controller if you have the right decoder. Well, it will be also easy to make your own IR controller using IR transmitter.==Specification==*Power Supply:5V*Interface:Digital*Modulate Frequency:38Khz*Module interface socket:<a href="JST_PH2.0" title="wikilink">JST PH2.0</a>==Wiring Diagram==The following image shows a suggested connection method. You may use any Digital I/O pin that is not in use by another device.<br /><br />NOTE: In the sample code below Digital pin 11 is in use, you may either change your wiring or change the sample code to match.<br />![fig:Connect_DFR0094.png](https://github.com/DFRobot/DFRobotDocument/Digital_IR_Receiver_Module_(SKU:DFR0094)/image/Connect_DFR0094.png  "Connect_DFR0094.png")==Sample Code==IR Receiver test code:</p>
<pre class="sourceCode cpp"><code class="sourceCode cpp"><span class="co">/* * IRremote: IRrecvDemo - demonstrates receiving IR codes with IRrecv * An IR detector/demodulator must be connected to the input RECV_PIN. * Version 0.1 July, 2009 * Copyright 2009 Ken Shirriff * http://arcfn.com */</span>#include &lt;IRremote.h&gt;<span class="dt">int</span> RECV_PIN = <span class="dv">11</span>;IRrecv irrecv(RECV_PIN);decode_results results;<span class="dt">void</span> setup(){  Serial.begin(<span class="dv">9600</span>);  irrecv.enableIRIn(); <span class="co">// Start the receiver}void loop() {  if (irrecv.decode(&amp;results)) {    Serial.println(results.value, HEX);    irrecv.resume(); // Receive the next value  }}</span></code></pre>
<p><a href="http://www.dfrobot.com/image/data/DFR0107/IRremote.zip">IR Remote Library</a> Includes some sample codes for sending and receiving.<br /><br /><br /><a href="image:nextredirectltr.png" title="wikilink">image:nextredirectltr.pngGo</a> Shopping <a href="https://www.dfrobot.com/product-351.html">Digital IR Receiver Module</a><br /><br /><a href="category:_Product_Manual" title="wikilink">category: Product Manual</a><a href="category:_DFR_Series" title="wikilink">category: DFR Series</a><a href="category:_Modules" title="wikilink">category: Modules</a><a href="category:_Sensors" title="wikilink">category: Sensors</a><a href="category:source" title="wikilink">category:source</a><a href="category:Diagram" title="wikilink">category:Diagram</a></p>---
title: Digital IR Receiver Module (SKU:DFR0094)
permalink: /Digital_IR_Receiver_Module_(SKU:DFR0094)/
---

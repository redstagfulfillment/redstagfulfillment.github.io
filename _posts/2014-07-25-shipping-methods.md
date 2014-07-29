---
layout: page
title: "Shipping Methods"
category: doc
parent: "API Basics"
date: 2014-07-29 12:12:51
order: 130
---

RSF now supports "UPS" and "FedEx" carriers. Supported methods are listed below. Others methods are not supported.

#### FedEx Methods

<table class="table-striped">
<tr>
  <th>flatrate_flatrate</th>
  <td>
  	<pre><code>{ "shipping_method" : "flatrate_flatrate" }</code></pre>
  	The "Flat Rate - Fixed" method.
  </td>	
</tr>
<tr>
  <th>fedex_EUROPE_FIRST_INTERNATIONAL_PRIORITY</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_EUROPE_FIRST_INTERNATIONAL_PRIORITY" }</code></pre>
  	The "Federal Express - Europe First Priority" method.
  </td>	
</tr>
<tr>
  <th>fedex_FEDEX_1_DAY_FREIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FEDEX_1_DAY_FREIGHT" }</code></pre>
  	The "Federal Express - 1 Day Freight" method.
  </td>	
</tr>
<tr>
  <th>fedex_FEDEX_2_DAY_FREIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FEDEX_2_DAY_FREIGHT" }</code></pre>
  	The "Federal Express - 2 Day Freight" method.
  </td>	
</tr>
<tr>
  <th>fedex_FEDEX_2_DAY</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FEDEX_2_DAY" }</code></pre>
  	The "Federal Express - 2 Day" method.
  </td>	
</tr>
<tr>
  <th>fedex_FEDEX_2_DAY_AM</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FEDEX_2_DAY_AM" }</code></pre>
  	The "Federal Express - 2 Day AM" method.
  </td>	
</tr>
<tr>
  <th>fedex_FEDEX_3_DAY_FREIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FEDEX_3_DAY_FREIGHT" }</code></pre>
  	The "Federal Express - 3 Day Freight" method.
  </td>	
</tr>
<tr>
  <th>fedex_FEDEX_EXPRESS_SAVER</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FEDEX_EXPRESS_SAVER" }</code></pre>
  	The "Federal Express - Express Saver" method.
  </td>	
</tr>
<tr>
  <th>fedex_FEDEX_GROUND</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FEDEX_GROUND" }</code></pre>
  	The "Federal Express - Ground" method.
  </td>	
</tr>
<tr>
  <th>fedex_FIRST_OVERNIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FIRST_OVERNIGHT" }</code></pre>
  	The "Federal Express - First Overnight" method.
  </td>	
</tr>
<tr>
  <th>fedex_GROUND_HOME_DELIVERY</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_GROUND_HOME_DELIVERY" }</code></pre>
  	The "Federal Express - Home Delivery" method.
  </td>	
</tr>
<tr>
  <th>fedex_INTERNATIONAL_ECONOMY</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_INTERNATIONAL_ECONOMY" }</code></pre>
  	The "Federal Express - International Economy" method.
  </td>	
</tr>
<tr>
  <th>fedex_INTERNATIONAL_ECONOMY_FREIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_INTERNATIONAL_ECONOMY_FREIGHT" }</code></pre>
  	The "Federal Express - Intl Economy Freight" method.
  </td>	
</tr>
<tr>
  <th>fedex_INTERNATIONAL_FIRST</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_INTERNATIONAL_FIRST" }</code></pre>
  	The "Federal Express - International First" method.
  </td>	
</tr>
<tr>
  <th>fedex_INTERNATIONAL_GROUND</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_INTERNATIONAL_GROUND" }</code></pre>
  	The "Federal Express - International Ground" method.
  </td>	
</tr>
<tr>
  <th>fedex_INTERNATIONAL_PRIORITY</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_INTERNATIONAL_PRIORITY" }</code></pre>
  	The "Federal Express - International Priority" method.
  </td>	
</tr>
<tr>
  <th>fedex_INTERNATIONAL_PRIORITY_FREIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_INTERNATIONAL_PRIORITY_FREIGHT" }</code></pre>
  	The "Federal Express - Intl Priority Freight" method.
  </td>	
</tr>
<tr>
  <th>fedex_PRIORITY_OVERNIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_PRIORITY_OVERNIGHT" }</code></pre>
  	The "Federal Express - Priority Overnight" method.
  </td>	
</tr>
<tr>
  <th>fedex_SMART_POST</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_SMART_POST" }</code></pre>
  	The "Federal Express - Smart Post" method.
  </td>	
</tr>
<tr>
  <th>fedex_STANDARD_OVERNIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_STANDARD_OVERNIGHT" }</code></pre>
  	The "Federal Express - Standard Overnight" method.
  </td>	
</tr>
<tr>
  <th>fedex_FEDEX_FREIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FEDEX_FREIGHT" }</code></pre>
  	The "Federal Express - Freight" method.
  </td>	
</tr>
<tr>
  <th>fedex_FEDEX_NATIONAL_FREIGHT</th>
  <td>
  	<pre><code>{ "shipping_method" : "fedex_FEDEX_NATIONAL_FREIGHT" }</code></pre>
  	The "Federal Express - National Freight" method.
  </td>	
</tr>
</table>

#### UPS Methods

<table class="table-striped">
<tr>
  <th>ups_11</th>
  <td>
  	<pre><code>{ "shipping_method" : "ups_11" }</code></pre>
  	The "United Parcel Service - UPS Standard" method.
  </td>	
</tr>
<tr>
  <th>ups_12</th>
  <td>
  	<pre><code>{ "shipping_method" : "ups_12" }</code></pre>
  	The "United Parcel Service - UPS Three-Day Select" method.
  </td>	
</tr>
<tr>
  <th>ups_14</th>
  <td>
  	<pre><code>{ "shipping_method" : "ups_14" }</code></pre>
  	The "United Parcel Service - UPS Next Day Air Early A.M." method.
  </td>	
</tr>
<tr>
  <th>ups_54</th>
  <td>
  	<pre><code>{ "shipping_method" : "ups_54" }</code></pre>
  	The "United Parcel Service - UPS Worldwide Express Plus" method.
  </td>	
</tr>
<tr>
  <th></th>
  <td>
  	<pre><code>{ "shipping_method" : "" }</code></pre>
  	The "" method.
  </td>	
</tr>
<tr>
  <th></th>
  <td>
  	<pre><code>{ "shipping_method" : "" }</code></pre>
  	The "" method.
  </td>	
</tr>
<tr>
  <th></th>
  <td>
  	<pre><code>{ "shipping_method" : "" }</code></pre>
  	The "" method.
  </td>	
</tr>
<tr>
  <th></th>
  <td>
  	<pre><code>{ "shipping_method" : "" }</code></pre>
  	The "" method.
  </td>	
</tr>
<tr>
  <th></th>
  <td>
  	<pre><code>{ "shipping_method" : "" }</code></pre>
  	The "" method.
  </td>	
</tr>
</table>

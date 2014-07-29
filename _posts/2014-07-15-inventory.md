---
layout: page
title: "Inventory"
category: ref
date: 2014-07-15 17:27:49
order: 10
---

RSF tracks inventory using the following statuses:

 * **Expected** - Listed on open ASNs, RMAs and Other Deliveries that have not yet been received.
 * **Processed** - Counted on an ASN, RMA or Other Delivery but not yet put-away.
 * **Put-Away** - Has been received on an ASN, RMA or Other Delivery that has not yet been committed to the inventory.
   If you have auto-commit enabled this should always be 0.
 * **Available** - Available for new orders.
 * **Reserved** - Reserved by existing orders and on the shelf waiting to be picked.
 * **Picked** - Picked from the shelves but not yet shipped.

Additionally, products have two flags that can be set which will affect whether or not they are retrieved in an inventory request.

 * **Status** - Enabled/Disabled - If "Disabled", the product is effectively deleted and will not appear in responses to inventory requests.
 * **Visibility** - Visible/Not Visible - If "Not Visible", the product will not appear in the inventory list but may still be ordered via the Merchant Panel.

#### Properties

<table class="table-striped">
<tr><th>sku</th>
<td>
	<pre><code>{ "sku" : "BlueWidget-1" }</code></pre>
	A unique identifier for a product. The SKU does appear on the packing slip. It is recommended that this be human-readable
	and end with a per-pack quantity to facilitate proper receiving. For example, a single blue widget may be "BlueWidget-1" and
	a pack of 5 blue widgets may be "BlueWidget-5". Maximum character length is 64.
</tr>
<tr><th>qty_expected</th>
<td>
	<pre><code>{ "qty_expected" : 1 }</code></pre>
	The "Expected" quantity.
</tr>
<tr><th>qty_processed</th>
<td>
	<pre><code>{ "qty_processed" : 1 }</code></pre>
	The "Processed" quantity.
</tr>
<tr><th>qty_putaway</th>
<td>
	<pre><code>{ "qty_putaway" : 1 }</code></pre>
	The "Put-Away" quantity.
</tr>
<tr><th>qty_available</th>
<td>
	<pre><code>{ "qty_available" : 1 }</code></pre>
	The "Available" quantity.
</tr>
<tr><th>qty_reserved</th>
<td>
	<pre><code>{ "qty_reserved" : 1 }</code></pre>
	The "Reserved" quantity.
</tr>
<tr><th>qty_picked</th>
<td>
	<pre><code>{ "qty_picked" : 1 }</code></pre>
	The "Picked" quantity.
</tr>
</table>


inventory.list `(string|array|null $skus)`
====

Get inventory levels for one or more products by SKU.

#### Parameters

<table class="table"><thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td><ul>
        <li>null - Get inventory for all products.</li>
        <li>string - Get inventory for a single product by SKU.</li>
        <li>array - Get inventory for the specified products by SKU.</li>
        </ul></td>
    </tr>
</tbody></table>

#### Return Value

An array of objects or an empty array if there were no matching SKUs.

#### Example Request

Get inventory for two SKUs:

```javascript
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "inventory.list",
        ["BlueWidget-1","BlueWidget-5"]
    ]
}
```

Get all inventory:

```javascript
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "inventory.list"
    ]
}
```

#### Example Response

```javascript
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "result" : [
        {
            "sku" : "BlueWidget-1",
            "qty_expected"  : 0,
            "qty_processed" : 0,
            "qty_putaway"   : 50,
            "qty_available" : 22,
            "qty_reserved"  : 16,
            "qty_picked"    : 1
        },
        {
            "sku" : "BlueWidget-5",
            "qty_expected"  : 40,
            "qty_processed" : 0,
            "qty_putaway"   : 0,
            "qty_available" : 3,
            "qty_reserved"  : 2,
            "qty_picked"    : 0
        }
    ]
}
```
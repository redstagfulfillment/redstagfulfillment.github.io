---
layout: page
title: "Packing"
category: ref
parent: "Order"
date: 2017-11-10 14:42:47
order: 17
---

#### Methods

 * [order_packing.create](#order_packing_create)
 * [order_packing.edit](#order_packing_edit)
 * [order_packing.info](#order_packing_info)
 * [order_packing.list](#order_packing_list)
 * [order_packing.delete](#order_packing_delete)
 
----
 
#### Entity Properties

 * [Order Packing](#order_packing_properties)
 
----

## Entity Properties

<h3 id="order_packing_properties">
    Order Packing Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>note</th>
        <td>
            <pre><code>{ "note" : "Place Amazon FBA Label in a pouch" }</code></pre>
            Instructions to the packer. The note is required.
        </td>
    </tr>
    <tr>
        <th>file_name</th>
        <td>
            <pre><code>{ "file_name" : "amazon_fba_3425232.pdf" }</code></pre>
            The "file_name" property.
        </td>
    </tr>
    <tr>
        <th>file_content</th>
        <td>
            <pre><code>{ "file_content" : "base64 encoded file content" }</code></pre>
            The "file_content" property. Must be base64 encoded.
        </td>
    </tr>
    <tr>
        <th>print_copies</th>
        <td>
            <pre><code>{ "print_copies" : "one_per_shipment" }</code></pre>
            The "print_copies" property. Allowed values: "one_per_order", "one_per_shipment", "one_per_package", "none".
        </td>
    </tr>
    <tr>
        <th>print_target</th>
        <td>
            <pre><code>{ "print_target" : "LASER" }</code></pre>
            The "print_target" property. Allowed values: "4X6_LABEL", "SMALL_LABEL", "LASER".
        </td>
    </tr>
</tbody>
</table>

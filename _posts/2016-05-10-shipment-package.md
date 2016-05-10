---
layout: page
title: "Package"
category: ref
parent: "Shipment"
date: 2016-05-10 19:22:01
order: 27
---

#### Methods

 * [package.search](#package_search)
 
----

#### Entity Properties

 * [Package](#package_properties)

----

----

<h1 id="package_search">
package.search
<code>(null|object $filters, array $options = [], null|string|object $fields = [])</code>
</h1>

Retrieve list of packages by filters. Package data can be customized by specifying properties to retrieve.

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td><ul>
        <li>null - Retrieve list of all packages.</li>
        <li>object - Retrieve list of packages using specified <a href="/doc/search-filters.html" title="Search Filters">filters</a>.</li>
        </ul></td>
    </tr>
    <tr>
        <td>1</td>
        <td><ul>
        <li>null - No options will be applied.</li>
        <li>object - Apply specified <a href="/doc/search-options.html" title="Search Options">options</a>.</li>
        </ul></td>
    </tr>
    <tr>
        <td>2</td>
        <td>
            <ul>
                <li>null - Retrieve "shipment_id", "order_unique_id" and "order_ref".</li>
                <li>string '*' - Retrieve all properties excluding "items" and "tracking_numbers".</li>
                <li>object - List of properties to retrieve in addition to "shipment_id", "order_unique_id" and "order_ref". List may include '*'.</li>
            </ul>
            <p>
            See "<a href="#package_properties">Package Properties</a>". Example:
            <code>['*', 'package_status']</code>
            </p>
        </td>
    </tr>
</tbody>
</table>

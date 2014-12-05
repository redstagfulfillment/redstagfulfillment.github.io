---
layout: page
title: "Media"
category: ref
parent: "Product"
date: 2014-12-05 12:40:01
order: 17
---

#### Methods

 * [product_media.list](#product_media_list)
 * [product_media.info](#product_media_info)
 * [product_media.types](#product_media_types)
 * [product_media.create](#product_media_create)
 * [product_media.update](#product_media_update)
 * [product_media.remove](#product_media_remove)

----

<h1 id="product_media_list">
product_media.list
<code>(string $sku, null|string|number $store = 0)</code>
</h1>

Retrieve list of product images

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>string - Product SKU.</td>
    </tr>
    <tr>
        <td>1</td>
        <td><ul>
            <li>null - Use default store.</li>
            <li>int - Use specified store.</li>
            <li>string - Use specified store.</li>
        </ul></td>
    </tr>
</tbody>
</table>

----

<h1 id="product_media_info">
product_media.info
<code>(string $sku, string $file, null|string|number $store = 0)</code>
</h1>

Retrieve product images

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>string - Product SKU.</td>
    </tr>
    <tr>
        <td>1</td>
        <td>string - Image file.</td>
    </tr>
    <tr>
        <td>2</td>
        <td><ul>
            <li>null - Use default store.</li>
            <li>int - Use specified store.</li>
            <li>string - Use specified store.</li>
        </ul></td>
    </tr>
</tbody>
</table>

----

<h1 id="product_media_types">
product_media.types
<code>(number $setId)</code>
</h1>

Retrieve product image types

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>int - Attribute set id.</td>
    </tr>
</tbody>
</table>

----

<h1 id="product_media_create">
product_media.create
<code>(string $sku, object $data, null|string|number $store = 0)</code>
</h1>

Upload new product image

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>string - Product SKU.</td>
    </tr>
    <tr>
        <td>1</td>
        <td>object - Image data.</td>
    </tr>
    <tr>
        <td>2</td>
        <td><ul>
            <li>null - Use default store.</li>
            <li>int - Use specified store.</li>
            <li>string - Use specified store.</li>
        </ul></td>
    </tr>
</tbody>
</table>

----

<h1 id="product_media_update">
product_media.update
<code>(string $sku, string $file, object $data, null|string|number $store = 0)</code>
</h1>

Update product image

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>string - Product SKU.</td>
    </tr>
    <tr>
        <td>1</td>
        <td>string - Image file.</td>
    </tr>
    <tr>
        <td>2</td>
        <td>object - Image data.</td>
    </tr>
    <tr>
        <td>3</td>
        <td><ul>
            <li>null - Use default store.</li>
            <li>int - Use specified store.</li>
            <li>string - Use specified store.</li>
        </ul></td>
    </tr>
</tbody>
</table>

----

<h1 id="product_media_remove">
product_media.remove
<code>(string $sku, string $file)</code>
</h1>

Remove product image

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>string - Product SKU.</td>
    </tr>
    <tr>
        <td>1</td>
        <td>string - Image file.</td>
    </tr>
</tbody>
</table>

---
layout: page
title: "Import Formats"
category: doc
date: 2015-06-18 19:52:21
order: 180
---

* [Order - Standard CSV](#order_standard_csv)
* [Order - Standard JSON](#order_standard_json)
* [Product - Standard CSV](#product_standard_csv)
* [Product - Standard JSON](#product_standard_json)
* [Delivery - Standard CSV](#delivery_standard_csv)
* [Delivery - Standard JSON](#delivery_standard_json)

---

Red Stag Fulfillment supports importing <a href="/ref/order.html">orders</a>, <a href="/ref/product.html">products</a> and <a href="/ref/delivery.html">deliveries</a>.

---

<h1 id="order_standard_csv">
Order - Standard CSV
</h1>

Import orders in CSV format.

#### Filter

```javascript
filter {
  if ([message] =~ /^(u|U)nique/) {
    drop {}
  }
  csv {
    columns => [
      "unique_id", "order_ref", "shipping_method", "custom_greeting", "note", "signature_required", "overbox",
      "requested_ship_date", "delayed_ship_date", "firstname", "lastname", "company", "street1", "street2",
      "city", "region", "postcode", "country", "phone", "sku", "qty"
    ]
  }
  push {
    unique_field => "order_ref"
    target => "order_items"
    fields => [ "sku", "qty" ]
  }
  ruby {
    code => '
      event["items"] = Hash.new; 
      event["order_items"].each { |value| event["items"]["#{value["sku"]}"] = "#{value["qty"]}" }
    '
    remove_field => [ "order_items" ]
  }
  ruby {
    code => 'event["raw_data"] = event["message"].first'
  }
}
```

#### Example

unique_id,order_ref,shipping_method,custom_greeting,note,signature_required,overbox,requested_ship_date,delayed_ship_date,firstname,lastname,company,street1,street2,city,region,postcode,country,phone,sku,qty
,123456,ups_01,,,,,,,Gates,Bill,Microsoft,11 Times Square,,New York,NY,10036,US,212.245.2100,product1,5
,123456,,,,,,,,,,,,,,,,,,product2,1
,123456,,,,,,,,,,,,,,,,,,product3,2

<h1 id="order_standard_json">
Order - Standard JSON
</h1>

Import orders in JSON format.

#### Filter

```javascript
filter {
  json {
    source => "message"
  }
  ruby {
    code => 'event["raw_data"] = event["message"]'
  }
}
```

#### Example

{ "order_ref" : "123456", "shipping_method" : "ups_01", "firstname" : "Gates", "lastname" : "Bill", "company" : "Microsoft", "street1" : "11 Times Square", "city" : "New York", "region" : "NY", "postcode" : "10036", "country" : "US", "phone" : "212.245.2100", "items" : { "product1" : 2, "product2" : 3, "product3" : 1} }
{ "order_ref" : "987654", "shipping_method" : "ups_01", "firstname" : "Gates", "lastname" : "Bill", "company" : "Microsoft", "street1" : "11 Times Square", "city" : "New York", "region" : "NY", "postcode" : "10036", "country" : "US", "phone" : "212.245.2100", "items" : { "product1" : 2, "product2" : 3, "product3" : 1} }
{ "order_ref" : "102030", "shipping_method" : "ups_01", "firstname" : "Gates", "lastname" : "Bill", "company" : "Microsoft", "street1" : "11 Times Square", "city" : "New York", "region" : "NY", "postcode" : "10036", "country" : "US", "phone" : "212.245.2100", "items" : { "product1" : 2, "product2" : 3, "product3" : 1} }

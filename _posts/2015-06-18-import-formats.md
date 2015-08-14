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

Red Stag Fulfillment supports importing <a href="/ref/order.html">orders</a>, <a href="/ref/product.html">products</a> and <a href="/ref/delivery.html">deliveries</a>. <a href="http://logstash.net">Logstash</a> configuration is used to filter import data. Standard CSV and JSON filters use the same values as API. Read <a href="#custom_filter">here</a> how to create custom import format.

---
<h2 id="order_standard_csv">
Order - Standard CSV
</h2>

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

```
,123456,ups_01,,,,,,,Bill,Gates,Microsoft,11 Times Square,,New York,NY,10036,US,212.245.2100,product1,5
,123456,,,,,,,,,,,,,,,,,,product2,1
,123456,,,,,,,,,,,,,,,,,,product3,2
```

<h2 id="order_standard_json">
Order - Standard JSON
</h2>

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

```javascript
{ 
  "order_ref" : "123456", 
  "shipping_method" : "ups_01", 
  "firstname" : "Bill",
  "lastname" : "Gates",
  "company" : "Microsoft", 
  "street1" : "11 Times Square", 
  "city" : "New York", 
  "region" : "NY", 
  "postcode" : "10036", 
  "country" : "US", 
  "phone" : "212.245.2100", 
  "items" : { 
    "product1" : 2, 
    "product2" : 3, 
    "product3" : 1
  }
}
```

<strong><span style="color:red">Important!</span></strong> JSON for each order must be a single line. Multi-line JSON is not allowed.

<h2 id="product_standard_csv">
Product - Standard CSV
</h2>

Import products in CSV format.

#### Filter

```javascript
filter {
  if ([message] =~ /^(s|S)ku/) {
    drop {}
  }
  csv {
    columns => [
      "sku", "name", "barcode", "goods_type", "weight", "length", "width", "height"
    ]
  }
  ruby {
    code => 'event["raw_data"] = event["message"].first'
  }
}
```

#### Example

```
sku,name,barcode,goods_type,weight,length,width,height
productsku,Product Name,productbarcode,NORMAL,"1.75","123","100","28"
```

<h2 id="product_standard_json">
Product - Standard JSON
</h2>

Import products in JSON format.

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

```javascript
{ 
  "sku" : "productsku", 
  "name" : "Product Name", 
  "barcode" : "productbarcode", 
  "goods_type" : "NORMAL", 
  "weight" : "1.75", 
  "length" : "123", 
  "width" : "100", 
  "height" : "28"
}
```

<strong><span style="color:red">Important!</span></strong> JSON for each product must be a single line. Multi-line JSON is not allowed.

<h2 id="delivery_standard_csv">
Delivery - Standard CSV
</h2>

Import deliveries in CSV format. "id" field is optional (not saved) and can be any unique value. The "id" field is only used to combine multi-line delivery items for a single delivery.

#### Filter

```javascript
filter {
  if ([message] =~ /^(i|I)d/) {
    drop {}
  }
  csv {
    columns => [
      "id", "delivery_type", "sender_name", "carrier_name", "expected_delivery",
      "merchant_ref", "sender_ref", "sku", "qty_expected"
    ]
  }
  push {
    unique_field => "id"
    target => "items"
    fields => [ "sku", "qty_expected" ]
  }
  ruby {
    code => 'event["raw_data"] = event["message"].first'
  }
}
```

#### Example

```
id,delivery_type,sender_name,carrier_name,expected_delivery,merchant_ref,sender_ref,sku,qty_expected
456,asn,Bill Gates,FedEx,"2014-07-31",12345,333,product1,5
456,,,,,,,product2,1
```

<h2 id="delivery_standard_json">
Delivery - Standard JSON
</h2>

Import deliveries in JSON format.

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

```javascript
{ 
  "delivery_type" : "asn", 
  "sender_name" : "Bill Gates", 
  "carrier_name" : "FedEx", 
  "expected_delivery" : "2014-07-31", 
  "merchant_ref" : "12345", 
  "sender_ref" : "333", 
  "items" : [ 
    { 
      "sku" : "product1", 
      "qty_expected" : 5
    }, 
    { 
      "sku" : "product2", 
      "qty_expected" : 1 
    } 
  ] 
}
```

<strong><span style="color:red">Important!</span></strong> JSON for each delivery must be a single line. Multi-line JSON is not allowed.

---

<h2 id="custom_filter">
Create custom import format
</h2>

Logstash uses input {...}, filter {...} and output {...} configuration. "input" and "output" configuration is already defined and only "filter" part of the configuration can be changed. "input" uses stdin and adds "line_number" to each line of the import file. "output" is different for each import type. Custom import format should get data after "input", make required modifications and prepare the data for the "output" format corresponding to the import type. Standard CSV and JSON configuration can be taken as a basis.

#### input

```javascript
input {
  stdin { type => "stdin-type" }
}

filter {
  ruby {
    code => '
      if !$LINE
        $LINE = 0;
      end;
      $LINE += 1; event["line_number"] = $LINE;'
  }
}
```

#### output for Order

```javascript
filter {
  ruby {
    code => 'event["parsed_data"] = {
      "api_method" => "order.create",
      "args" => {
        "items" => event["items"],
        "address" => {
          "firstname"=> event["firstname"],
          "lastname" => event["lastname"],
          "company"  => event["company"],
          "street1"  => event["street1"],
          "city"     => event["city"],
          "region"   => event["region"],
          "postcode" => event["postcode"],
          "country"  => event["country"],
          "phone"    => event["phone"]
        },
        "info" => {
          "unique_id"           => event["unique_id"],
          "order_ref"           => event["order_ref"],
          "shipping_method"     => event["shipping_method"],
          "custom_greeting"     => event["custom_greeting"],
          "note"                => event["note"],
          "signature_required"  => event["signature_required"],
          "overbox"             => event["overbox"],
          "requested_ship_date" => event["requested_ship_date"],
          "delayed_ship_date"   => event["delayed_ship_date"]
        }
      }
    }'
  }
}
```

#### output for Product

```javascript
filter {
  ruby {
    code => 'event["parsed_data"] = {
      "api_method" => "product.create",
      "args" => {
        "sku" => event["sku"],
        "product_data" => {
          "name"         => event["name"],
          "barcode"      => event["barcode"],
          "goods_type"   => event["goods_type"],
          "weight"       => event["weight"],
          "length"       => event["length"],
          "width"        => event["width"],
          "height"       => event["height"]
        }
      }
    }'
  }
}
```

#### output for Delivery

```javascript
filter {
  ruby {
    code => 'event["parsed_data"] = {
      "api_method" => "delivery.create",
      "args" => {
        "delivery_type" => event["delivery_type"],
        "data" => {
          "sender_name"       => event["sender_name"],
          "carrier_name"      => event["carrier_name"],
          "expected_delivery" => event["expected_delivery"],
          "delivery_type"     => event["delivery_type"],
          "merchant_ref"      => event["merchant_ref"],
          "sender_ref"        => event["sender_ref"]
        },
        "items" => event["items"]
      }
    }'
  }
}
```

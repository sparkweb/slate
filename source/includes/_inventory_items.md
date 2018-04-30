# Inventory Items

## Inventory Item Properties

A valid inventory item includes a name and code (sku).

Attribute | Description
--------- | -----------
`name` | The name of the product
`code` | The product's unique sku
`price` | The item price (decimal)
`cost` | The item cost (decimal)
`weight` | The shipping weight of the item
`stock` | The number of avilable units
`metadata` | An array with special information about the inventory item. Used by some integations.
`location` | The warehouse or fulfillment method responsible for this item
`update_source` | The name of the last system to update the item's details
`date_added` | The date the item was added to Order Desk <i class="label label-info">read-only</i>
`date_updated` | The date the item was updated in Order Desk <i class="label label-info">read-only</i>


## Get All Inventory Items

Get the all the store's inventory items.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>https://app.orderdesk.me/api/v2/inventory-items</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->get("inventory-items");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/inventory-items"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
```

> Response:

```json
{
  "status": "success",
  "execution_time": "0.6651 seconds",
  "records_returned": 5,
  "total_records": "5",
  "inventory_items": [
    {
      "id": 2510,
      "name": "Three Wolf T-Shirt, X-Large / Black",
      "code": "3wolf-11",
      "price": 10,
      "cost": 8,
      "weight": 0.8,
      "stock": 48,
      "update_source": "Shopify",
      "location": "",
      "date_added": "2014-08-09 09:06:53",
      "date_updated": "2014-08-09 09:06:53"
    },
    {
      "id": 2511,
      "name": "Three Wolf T-Shirt, X-Large / Yellow",
      "code": "3wolf-12",
      "price": 10,
      "cost": 8,
      "weight": 0.8,
      "stock": 51,
      "update_source": "Shopify",
      "location": "",
      "date_added": "2014-08-09 09:06:53",
      "date_updated": "2014-08-09 09:06:53"
    },
    {
      "id": 2509,
      "name": "Three Wolf T-Shirt, X-Large / Blue",
      "code": "3wolf-10",
      "price": 10,
      "cost": 8,
      "weight": 0.8,
      "stock": 88,
      "update_source": "Shopify",
      "location": "",
      "date_added": "2014-08-09 09:06:53",
      "date_updated": "2014-08-09 09:06:53"
    },
    {
      "id": 2500,
      "name": "Three Wolf T-Shirt, Large / Black",
      "code": "3wolf-8",
      "price": 10,
      "cost": 8,
      "weight": 0.8,
      "stock": 99,
      "update_source": "Shopify",
      "location": "",
      "date_added": "2014-08-09 09:06:53",
      "date_updated": "2014-08-09 09:06:53"
    },
    {
      "id": 2515,
      "name": "White iPhone, White iPhone",
      "code": "whiteiphone",
      "price": 10,
      "cost": 8,
      "weight": 0.8,
      "stock": 108,
      "update_source": "Shopify",
      "location": "",
      "date_added": "2014-08-09 09:06:53",
      "date_updated": "2014-08-09 09:06:53"
    }
  ]
}
```



## Get A Single Inventory Item

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>https://app.orderdesk.me/api/v2/inventory-items/&lt;id&gt;</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->get("inventory-items");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/inventory-items/2510"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
```

> Response:

```json
{
  "status": "success",
  "execution_time": "0.0767 seconds",
  "records_returned": 1,
  "inventory_item": {
    "id": 2510,
    "name": "Three Wolf T-Shirt, X-Large / Black",
    "code": "3wolf-11",
    "price": 10,
    "cost": 8,
    "weight": 0.8,
    "stock": 48,
    "update_source": "Shopify",
    "location": "",
    "date_added": "2014-08-09 09:06:53",
    "date_updated": "2014-08-09 09:06:53"
  }
}
```



## Update Inventory Item

All fields should be passed through. Any empty fields will be set to blank on the record.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-put">PUT</i>
    <h6>https://app.orderdesk.me/api/v2/inventory-items/&lt;id&gt;</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$args = array(
  "name" => "Three Wolves T-Shirt",
  "code" => "3wolf-11",
  "price" => 11.00,
  "stock" => 52,
);
$result = $od->put("inventory-items", $args);
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/inventory-items/2510"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -H "X-HTTP-Method-Override: PUT"
  -X POST
  -d '{"name": "Three Wolves T-Shirt", "code" => "3wolf-11", "price" => 11.00, "stock" => 52}'
```

> Response:

```json
{
  "status": "success",
  "message": "Inventory Item Updated",
  "execution_time": "0.1420 seconds"
}
```


## Create Inventory Item

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-post">POST</i>
    <h6>https://app.orderdesk.me/api/v2/inventory-items</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$args = array(
  "name" => "Three Wolves T-Shirt",
  "code" => "3wolf-XX",
  "price" => 11.00,
  "stock" => 52,
);
$result = $od->post("inventory-items", $args);
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/inventory-items"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X POST
  -d '{"name": "Three Wolves T-Shirt", "code" => "3wolf-XX", "price" => 11.00, "stock" => 52}'
```

> Response:

```json
{
  "status": "success",
  "message": "Inventory Item Added",
  "execution_time": "0.1761 seconds"
}
```


## Delete an Inventory Item

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-delete">DELETE</i>
    <h6>https://app.orderdesk.me/api/v2/inventory-item/&lt;id&gt;</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->delete("inventory-items/2509");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/inventory-items/2509"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X DELETE
```

> Response:

```json
{
  "status": "success",
  "message": "Inventory Item 2509 Deleted",
  "execution_time": "0.0836 seconds"
}
```

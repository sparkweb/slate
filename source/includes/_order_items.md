# Order Items

## Order Item Properties ##

Attribute | Description
--------- | -----------
`id` | Order Desk's Internal ID # for the order item <i class="label label-info">read-only</i>
`name` | Item name
`price` | Item price, defaults to `0.00`
`quantity` | Item quantity, integer format, defaults to `1`
`weight` | Item weight, decimal format
`code` | Item SKU or product code
`delivery_type` | Avaliable options are `ship`, `noship`, `download`, or `future`. Defaults to `ship`
`category_code` | Further details about the type of item, freeform text
`variation_list` | Array with a list of variations in `key => value` format. Ex: `['Size': 'Large', 'Color': 'Red']`
`metadata` | Array with a list of extra (hidden) order details in `key => value` format

<aside class="notice">
Please note that you can also update the order object and update the order and items will be added, updated, or removed from the order as well.
</aside>

## Get All Order Items

Get the all the items for an order.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;/order-items</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->get("orders/736745/order-items");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/736745/order-items"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
```

> Response

```json
{
  "status": "success",
  "execution_time": "0.1505 seconds",
  "total_records": 1,
  "order_items": [
    {
      "id": "47986",
      "name": "Black Shirt",
      "price": 5.5,
      "quantity": 1,
      "weight": 0,
      "code": "",
      "delivery_type": "ship",
      "category_code": "freeshipping",
      "fulfillment_method": "",
      "variation_list": {
        "Size": "Large"
      },
      "metadata": []
    },
    {
      "id": "47987",
      "name": "Green Shirt",
      "price": 2.5,
      "quantity": 1,
      "weight": 0,
      "code": "",
      "delivery_type": "ship",
      "category_code": "freeshipping",
      "fulfillment_method": "",
      "variation_list": {
        "Size": "Large"
      },
      "metadata": []
    }
  ]
}
```


## Get Single Order Item

Get a single items for an order.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>https://app.orderdesk.me/api/v2/order/&lt;order_id&gt;/order-items/&lt;order_item_id&gt;</h6>
  </div>
</div>


```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->get("orders/736745/order-items/47986");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/736745/order-items/47986"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
```

> Response

```json
{
  "status": "success",
  "execution_time": "0.1505 seconds",
  "order_item": {
    "id": "47986",
    "name": "Black Shirt",
    "price": 5.5,
    "quantity": 1,
    "weight": 0,
    "code": "",
    "delivery_type": "ship",
    "category_code": "freeshipping",
    "fulfillment_method": "",
    "variation_list": {
      "Size": "Large"
    },
    "metadata": []
  }
}
```



## Create Order Item

Add a new order item to an existing order. Pass in json for an <a href="#order-item-properties">order_item object</a>.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-post">POST</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;/order-items</h6>
  </div>
</div>

The `order_id` field refers to Order Desk's internal ID.


```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$args = array(
  "name" => "Second Widget",
  "code" => "widget2",
  "price" => 12.99,
  "variation_list" => array(
  	"Size" => "Large",
  ),
);
$result = $od->post("orders/104837/order-items", $args);
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/104837/order-items"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X POST
  -d '{"name": "Second Widget", "code": "widget2", "price": 12.99, "variation_list": ["Size": "Large"]}'


> Response

```json
{
  "status": "success",
  "message": "Order Item Added"
}
```



## Update Order Item

Update an existing order item from an existing order. Pass in json for an <a href="#order-item-properties">order_item object</a>.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-put">PUT</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;/order-items/&lt;id&gt;</h6>
  </div>
</div>

The `order_id` field refers to Order Desk's internal ID.
The `id` field refers to Order Desk's internal ID for the item being updated.



```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$args = array(
  "name" => "Second Widget",
  "code" => "widget2",
  "price" => 12.99,
  "variation_list" => array(
  	"Size" => "Large",
  ),
);
$result = $od->put("orders/104837/order-items/9834738", $args);
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/104837/order-items/9834738"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -H "X-HTTP-Method-Override: PUT"
  -X POST
  -d '{"name": "Second Widget", "code": "widget2", "price": 12.99, "variation_list": ["Size": "Large"]}'


> Response

```json
{
  "status": "success",
  "message": "Order Item Updated"
}
```



## Delete Order Item ID

Use the endpoint below to delete an item from an order.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-delete">DELETE</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;/order-items/&lt;id&gt;</h6>
  </div>
</div>

The `order_id` field refers to Order Desk's internal ID.
The `id` field refers to Order Desk's internal ID for the item being deleted.


```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->delete("orders/183749/order-items/736745");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/183749/order-items/736745"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X DELETE
```


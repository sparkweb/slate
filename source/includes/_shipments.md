# Shipments

## Shipment Properties

Field Name | Description
--------- | -----------
`tracking_number` | The carrier's assigned tracking number. Use `n/a` if no tracking number is applicable.
`carrier_code` | Code like `USPS` or `FedEx` if available.
`shipment_method` | Name of shipping service, example: `First Class International`
`weight` | Final weight of shipment
`cost` | Your cost to send shipment
`status` | The shipment's current status - used by EasyPost webhook
`tracking_url` | If not entered, we will try to guess it based on tracking number format and carrier code


## Get All Order Shipments

Get the all the shipments for an order.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>https://app.orderdesk.me/api/v2/order/&lt;order_id&gt;/shipments</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->get("orders/29491/shipments");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/29491/shipments"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
```

> Response

```json
{
  "status": "success",
  "execution_time": "0.1290 seconds",
  "total_records": 1,
  "shipments": [
    {
      "id": "437",
      "order_id": "29491",
      "store_id": "11",
      "tracking_number": "1Z2398479234",
      "carrier_code": "UPS",
      "shipment_method": "Ground",
      "weight": "3.55",
      "cost": "",
      "status": "",
      "tracking_url": "http://wwwapps.ups.com/WebTracking/track?track=yes&trackNums=1Z2398479234",
      "label_format": "",
      "label_image": "",
      "print_status": "0",
      "order_items": "",
      "cart_shipment_id": "",
      "label_shipment_id": "",
      "date_shipped": "2015-06-29",
      "date_added": "2015-06-29 19:02:50"
    }
  ]
}
```

## Get Single Order Shipment

Get a single shipment for an order.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>https://app.orderdesk.me/api/v2/order/&lt;order_id&gt;/shipments/&lt;shipment_id&gt;</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->get("orders/29491/shipments/437");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/29491/shipments/437"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
```

> Response

```json
{
  "status": "success",
  "execution_time": "0.1472 seconds",
  "shipment": {
    "id": "437",
    "order_id": "29491",
    "store_id": "11",
    "tracking_number": "1Z2398479234",
    "carrier_code": "UPS",
    "shipment_method": "Ground",
    "weight": "3.55",
    "cost": "",
    "status": "",
    "tracking_url": "http://wwwapps.ups.com/WebTracking/track?track=yes&trackNums=1Z2398479234",
    "label_format": "",
    "label_image": "",
    "print_status": "0",
    "order_items": "",
    "cart_shipment_id": "",
    "label_shipment_id": "",
    "date_shipped": "2015-06-29",
    "date_added": "2015-06-29 19:02:50"
  }
}
```

## Create Shipment


### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-post">POST</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;/shipments</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$args = array(
  "tracking_number" => "1Z2398479234",
  "carrier_code" => "UPS",
  "shipment_method" => "Ground",
);
$result = $od->post("orders/29491/shipments", $args);
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/29491"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X POST
  -d '{"tracking_number": "1Z2398479234"}'
```

> Response If Added

```json
{
  "status": "success",
  "message": "Shipment Added",
  "execution_time": "0.1454 seconds"
}
```
> Response If Could Not Be Added Because of Existing Shipment

```json
{
  "status": "error",
  "message": "Shipment Not Added",
  "execution_time": "0.1442 seconds"
}
```


## Delete Shipment

Use the endpoint below to delete a shipment from an order.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-delete">DELETE</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;/shipments/&lt;id&gt;</h6>
  </div>
</div>

The `order_id` field refers to Order Desk's internal ID.
The `id` field refers to Order Desk's internal ID for the shipment being deleted.

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->delete("orders/2154/shipments/736745");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/2154/shipments/736745"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X DELETE
```

> Response

```
{
  "status": "success",
  "message": "Shipment 736745 Deleted",
  "execution_time": "0.1610 seconds"
}
```

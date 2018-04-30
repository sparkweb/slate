# Move Orders

Move orders to a new folder. This can target one order or multiple orders.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-post">POST</i>
    <h6>https://app.orderdesk.me/api/v2/move-orders</h6>
  </div>
</div>

>Folder ID Method

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$args = array(
  "order_id_list" => array(29491, 29490),
  "destination_folder_id" => 9384,
);
$result = $od->post("move-orders", $args);
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/move-orders"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X POST
  -d '{"order_id_list": [29491, 29490], "destination_folder_id": 9384}'
```

> Folder Name Method

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$args = array(
  "order_id_list" => array(29491, 29490),
  "destination_folder_name" => "Prepared",
);
$result = $od->post("move-orders", $args);
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/move-orders"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X POST
  -d '{"order_id_list": [29491, 29490], "destination_folder_name": "Prepared"}'
```

> Response

```json
{
  "status": "success",
  "message": "2 Orders Moved",
  "execution_time": "0.1396 seconds",
  "results": [
    {
      "order_id": 29491,
      "message": "Order Moved to Prepared Folder",
      "original_folder_id": 6587
    },
    {
      "order_id": 29490,
      "message": "Order Moved to Prepared Folder",
      "original_folder_id": 6587
    }
  ]
}
```

Field Name | Type | Description
--------- | ---------------------- | -----------
`order_id_list` | Array | This should be an array of Order Desk's internal ID's
`destination_folder_id` | Integer | This is the folder ID to which the orders should be moved
`destination_folder_name` | String | This is the name of the folder to which the orders should be moved. It must match exactly.

Please note that either `destination_folder_id` or `destination_folder_name` should be used, but not both.

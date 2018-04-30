# Authentication

In order to connect to the Order Desk API, go to the Store Settings and click on the API tab to create an API Key. You’ll be presented with an API Key and Store ID. You’ll need to add both of these details as headers to each request that you make to the API along with the correct content-type request.

### Required Headers

Name | Value
--------- | -------
ORDERDESK-STORE-ID | `your store id`
ORDERDESK-API-KEY | `your api key`
Content-Type | application/json


## Querying the Testing Endpoint

Make sure the connection is successful and return the system time

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>https://app.orderdesk.me/api/v2/test</h6>
	</div>
</div>


```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->get("test");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/test"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
```

> Response:

```json
{
  "status": "success",
  "message": "Connection Successful",
  "current_date_time": "2015-04-14 22:00:10"
}
```

### Returned Fields ###

Attribute | Value
--------- | ----------------------
`status` | success
`message` | Connection Successful
`current_date_time` | `System time in UTC`

# Store Settings

Get the store settings and folder list. This is particularly helpful if you are looking for details about a store's folder structure and need to fetch ID #'s.

<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>https://app.orderdesk.me/api/v2/store</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->get("store");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/store"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
```
> Response:

```json
{
  "status": "success",
  "execution_time": "0.1419 seconds",
  "store": {
    "id": "11",
    "name": "Test Store",
    "settings": {
      "app_version": "2.0",
      "locale_code": "en_US",
      "timezone": "America/Los_Angeles",
      "store_country": "US",
      "store_email": "email@myserver.com",
      "admin_email": "email@myserver.com",
      "normalize_capitalization": "1",
      "normalize_phone_numbers": "0",
      "date_format": "Y-m-d H:i:s",
      "short_date_format": "Y-m-d",
      "orders_per_page": 50,
      "report_frequency": "",
      "dashboard_report_type": "daily",
      "store_url": "http://yoursite.com",
      "custom_css": "",
      "security_po_box_warn": "",
      "security_different_address_warn": "",
      "security_different_country_warn": "",
      "security_quantity_warn": 0,
      "limit_address_field_char_length": 0,
      "country_name_format": "0",
      "all_orders_name": "All Orders",
      "api_key": "yourapikey",
      "all_orders_column_view": [],
      "shipping_methods": [],
      "default_checkout_data_fields": [],
      "smtp_port": "25",
      "smtp_host": "",
      "smtp_username": "",
      "smtp_password": "",
      "smtp_encryption": "",
      "smtp_headers": "",
      "auto_update_stock_count": "",
      "auto_create_inventory_items": "",
      "normalizeCapitalization": 1
    },
    "folders": {
      "21654": "New",
      "21655": "Prepared",
      "21656": "Closed",
      "21657": "Canceled"
    }
  }
}
```

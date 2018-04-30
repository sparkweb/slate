# Orders

## Order Properties
```json
{
  "id": "26211",
  "email": "test@orderdesk.me",
  "shipping_method": "FedEx Home Delivery",
  "quantity_total": 1,
  "weight_total": 1,
  "product_total": 10,
  "shipping_total": 11.17,
  "handling_total": 0.5,
  "tax_total": 1.2,
  "discount_total": 1.7,
  "order_total": 21.17,
  "cc_number_masked": "xxxxxxxxxxxx4242",
  "cc_exp": "02\/2016",
  "processor_response": "Authorize.net Transaction ID: 2221864944",
  "payment_type": "Visa",
  "payment_status": "Approved",
  "processor_balance": 21.17,
  "refund_total": 0.00,
  "customer_id": "5487542",
  "email_count": "3",
  "ip_address": "254.565.44.15",
  "tag_color": "",
  "source_name": "Order Desk",
  "source_id": "412218073",
  "fulfillment_name": "",
  "fulfillment_id": "",
  "tag_name": "success",
  "folder_id": 1,
  "date_added": "2014-10-08 12:10:00",
  "date_updated": "2014-10-09 23:13:47",
  "shipping": {
    "first_name": "Jimmy",
    "last_name": "Dean",
    "company": "",
    "address1": "800 Emmet St",
    "address2": "",
    "address3": "",
    "address4": "",
    "city": "Nashville",
    "state": "TN",
    "postal_code": "55555",
    "country": "US",
    "phone": ""
  },
  "customer": {
    "first_name": "Bingo",
    "last_name": "Little",
    "company": "",
    "address1": "900 Lord Business Ave",
    "address2": "",
    "city": "Knoxville",
    "state": "TN",
    "postal_code": "77777",
    "country": "US",
    "phone": ""
  },
  "return_address": {
    "title": "Acme",
    "name": "Doug Jones",
    "company": "Acme Manufacturing",
    "address1": "817 E Maple Ln",
    "address2": "",
    "city": "Knoxville",
    "state": "TN",
    "postal_code": "55555",
    "country": "US",
    "phone": ""
  },
  "checkout_data": {
    "Gift Message": "Happy Birthday"
  },
  "order_metadata": {
    "fraud_protection_score": 0
  },
  "discount_list": [
    {
      "name": "Discount",
      "code": "MN234DX78",
      "amount": "1.70"
    }
  ],
  "order_notes": [
    {
      "date_added": "2014-10-09 23:12:05",
      "username": "Customer Service Rep",
      "content": "Customer called to change shipping address"
    }
  ],
  "order_items": [
    {
      "id": "42286",
      "name": "Crazy Glue",
      "price": "10",
      "quantity": 1,
      "weight": 1,
      "code": "crzyg-554",
      "delivery_type": "ship",
      "category_code": "DEFAULT",
      "variation_list": {
        "Size": "Small",
        "Color": "Black"
      },
      "metadata": {
        "image": "image_url_here"
      }
    }
  ],
  "order_shipments": [
    {
      "id": "369",
      "order_id": "26211",
      "store_id": "11",
      "tracking_number": "1Z132456789",
      "carrier_code": "",
      "shipment_method": "",
      "weight": "0",
      "cost": "0",
      "status": "",
      "tracking_url": "",
      "label_format": "",
      "label_image": "",
      "order_items": "",
      "print_status": "1",
      "cart_shipment_id": "",
      "date_shipped": "2014-10-09",
      "date_added": "2014-10-09 23:08:49"
    }
  ]
}
```

Every order is returned as a JSON collection.

### Order Properties ###

Attribute | Description
--------- | -----------
`id` | Order Desk's internal ID # <i class="label label-info">read-only</i>
`source_id` | Your order ID. If blank, Order Desk's internal ID will be used <i class="label label-info">read-only</i>
`source_name` | Pick from Available [Source Names](#available-source-names). Defaults to `Order Desk`
`source_id` | The original ID # of the order. If nothing entered, Order Desk's internal ID number will be used
`email` | Customer's email address
`shipping_method` | Name of shipping method selected
`quantity_total` | The total number of all the items in the order <i class="label label-info">read-only</i>
`weight_total` | The total weight of all the items in the order <i class="label label-info">read-only</i>
`product_total` | The total price of all the items in the order <i class="label label-info">read-only</i>
`shipping_total` | The total price of shipping in the order
`handling_total` | The total price of handling in the order
`tax_total` | The total price of tax in the order
`discount_total` | The total price of all the discounts in the order stored as a positive number <i class="label label-info">read-only</i>
`order_total` | The total calculated price of the entire order <i class="label label-info">read-only</i>
`cc_number` | Obfuscated credit card number. Enter only the last four digits
`cc_exp` | Credit card expiration in format `MM/YYYY`
`processor_response` | Gateway transaction ID in format `<gateway_name>: <transaction_id>`
`payment_type` | Visa, MasterCard, PayPal, etc.
`payment_status` | Available options: Approved, Authorized, Captured, Fully Refunded, Partially Refunded, Pending, Rejected, or Voided. Default is Captured
`processor_balance` | The amount that the was charged at the processor. This amount will be decremented when refunds are made. By default it will be set the same as `order_total`
`refund_total` | The amount that jhas been refunded on the order from within Order Desk. This is generally something that will be set internally.
`customer_id` | The customer ID field from the originating shopping cart
`email_count` | The number of orders that match this email address <i class="label label-info">read-only</i>
`ip_address` | The customer's IP address
`tag_color` | Not In Use
`tag_name` | Not In Use
`fulfillment_name` | Once the order has been sent for fulfillment, the name of the fulfillment method is entered here
`fulfillment_id` | The internal ID of the fulfillment service will be saved here for some services
`folder_id` | The ID number of the folder in which the order is stored. If nothing is entered when adding an order, the folder will be the first folder in the list
`date_added` | The order date stored in UTC
`date_updated` | The date that the order was last updated in UTC
`checkout_data` | Array with a list of extra order details in `key => value` format. Used when it may need to be manually edited in Order Desk.
`order_metadata` | Array with a list of extra (hidden) order details in `key => value` format
`shipping` | Array with shipping [address details](#address-properties). If nothing is entered, the `customer` array will be copied to the `shipping` array. A first and last name combination or a company name must be entered to be a valid order.
`customer` | Array with customer [address details](#address-properties). If nothing is entered, the `shipping` array will be copied to the `customer` array. A first and last name combination or a company name must be entered to be a valid order.
`return_address` | Array with [return address details](#return-address-properties). Not required.
`discount_list` | Array with a list of discounts. See [discount properties](#discount-properties) for reference.
`order_notes` | Array with a list of order notes. See [order note properties](#order-note-properties) for reference.
`order_shipments` | Array with a list of order shipments. See order shipments properties for reference.



## Order Item Properties ##

<a href="#order-item-properties">See Reference Here</a>



## Address Properties ##

A valid order requires either the first and last name OR the company name to be entered.

Attribute | Description
--------- | -----------
`first_name` | First Name
`last_name` | Last Name
`company` | Company
`address1` | Street Address 1
`address2` | Street Address 2
`address3` | Street Address 3 (not available for customer address)
`address4` | Street Address 4 (not available for customer address)
`city` | City
`state` | State or Region
`postal_code` | Zip or Postal Code
`country` | Country (either country code or full country name)
`phone` | Phone Number


## Return Address Properties ##

If the order has a custom return address, it will be entered here. This can be set via rule or set when the order is inserted via the API.

Attribute | Description
--------- | -----------
`title` | The Title of the Return Address
`name` | Shipping Name
`company` | Company
`address1` | Street Address 1
`address2` | Street Address 2
`city` | City
`state` | State or Region
`postal_code` | Zip or Postal Code
`country` | Country (either country code or full country name)
`phone` | Phone Number


## Discount Properties ##

Attribute | Description
--------- | -----------
`name` | Name of discount
`code` | Code used for discount <i class="label label-info">optional</i>
`amount` | The discount amount. Discounts should be stored as positive numbers.



## Order Note Properties ##

There is a 2000 character max for all notes, including date and username metadata so keep your notes under 1800 characters to avoid data loss.

Attribute | Description
--------- | -----------
`date_added` | Date that the note was added in UTC
`username` | Name of the person who wrote the note
`content` | Note content


## Get a Single Order

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;</h6>
  </div>
</div>

The `order_id` field refers to Order Desk's internal ID.


```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->get("orders/736745");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/736745"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
```

> Response

```json
{
  "status": "success",
  "message": "Execution took 0.0208 seconds",
  "order": {
    "id": "925086",
    "email": "myemail@server.com",
    "shipping_method": "",
    "quantity_total": 1,
    "weight_total": 2.375,
    "product_total": 19,
    "shipping_total": 0,
    "handling_total": 0,
    "tax_total": 0,
    "discount_total": 0,
    "order_total": 19,
    "cc_number_masked": "xxxxxxxxxxxx4242",
    "cc_exp": "02/2016",
    "processor_response": "Authorize.net Transaction ID:2231994036",
    "payment_type": "Visa",
    "payment_status": "Approved",
    "processor_balance": 19,
    "refund_total": 0,
    "customer_id": "8173875",
    "email_count": "3",
    "ip_address": "181.16.150.12",
    "tag_color": "",
    "source_name": "FoxyCart",
    "source_id": "648714418",
    "fulfillment_name": "",
    "fulfillment_id": "",
    "tag_name": "",
    "folder_id": 64,
    "date_added": "2015-04-15 12:12:10",
    "date_updated": "2015-04-15 15:32:04",
    "shipping":
    {
      "first_name": "Jimmy",
      "last_name": "Dean",
      "company": "",
      "address1": "800 Emmet St",
      "address2": "",
      "address3": "",
      "address4": "",
      "city": "Nashville",
      "state": "TN",
      "postal_code": "55555",
      "country": "US",
      "phone": "208-555-5555"
    },
    "customer":
    {
      "first_name": "Bingo",
      "last_name": "Little",
      "company": "",
      "address1": "900 Lord Business Ave",
      "address2": "",
      "city": "Knoxville",
      "state": "TN",
      "postal_code": "77777",
      "country": "US",
      "phone": "208-555-5555"
    },
    "return_address": {
      "title": "Acme",
      "name": "Doug Jones",
      "company": "Acme Manufacturing",
      "address1": "817 E Maple Ln",
      "address2": "",
      "city": "Knoxville",
      "state": "TN",
      "postal_code": "55555",
      "country": "US",
      "phone": ""
    },
    "checkout_data": {
      "Order Notes": "Please leave by back door"
    },
    "order_metadata": {
      "fraud_protection_score": 0
    },
    "discount_list": [],
    "order_notes": [],
    "order_items": [
      {
        "id": "1670028",
        "name": "Subscription Product",
        "price": 19,
        "quantity": 1,
        "weight": 2.375,
        "code": "126478",
        "delivery_type": "ship",
        "category_code": "DEFAULT",
        "variation_list": [],
        "metadata": {
          "image": "http://img1.wikia.nocookie.net/__cb20130318151721/epicrapbattlesofhistory/images/6/6d/Rick-astley.jpg"
        }
      }
    ],
    "order_shipments": []
  }
}
```


## Get Multiple Orders

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>https://app.orderdesk.me/api/v2/orders</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$args = array(
  "source_name" => "FoxyCart",
  "search_start_date" => "2015-04-15 12:05:06",
  "order_by" => "shipping_last_name",
);
$result = $od->get("orders", $args);
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -d "source_name=FoxyCart&search_start_date=2015-04-15%2012:05:06&order_by=shipping_last_name"
```

> Response

```json
{
  "status": "success",
  "message": "Execution took 0.0208 seconds",
  "total_records": 1,
  "records_returned": 1,
  "offset": 0,
  "limit": 50,
  "orders": [
    {
      "id": "925086",
      "email": "myemail@server.com",
      "shipping_method": "",
      "quantity_total": 1,
      "weight_total": 2.375,
      "product_total": 19,
      "shipping_total": 0,
      "handling_total": 0,
      "tax_total": 0,
      "discount_total": 0,
      "order_total": 19,
      "cc_number_masked": "xxxxxxxxxxxx4242",
      "cc_exp": "02/2016",
      "processor_response": "Authorize.net Transaction ID:2231994036",
      "payment_type": "Visa",
      "payment_status": "Approved",
      "processor_balance": 19,
      "refund_total": 0,
      "customer_id": "8173875",
      "email_count": "3",
      "ip_address": "181.16.150.12",
      "tag_color": "",
      "source_name": "FoxyCart",
      "source_id": "648714418",
      "fulfillment_name": "",
      "fulfillment_id": "",
      "tag_name": "",
      "folder_id": 64,
      "date_added": "2015-04-15 12:12:10",
      "date_updated": "2015-04-15 15:32:04",
      "shipping": {
        "first_name": "Jimmy",
        "last_name": "Dean",
        "company": "",
        "address1": "800 Emmet St",
        "address2": "",
        "address3": "",
        "address4": "",
        "city": "Nashville",
        "state": "TN",
        "postal_code": "55555",
        "country": "US",
        "phone": "208-555-5555"
      },
      "customer": {
        "first_name": "Bingo",
        "last_name": "Little",
        "company": "",
        "address1": "900 Lord Business Ave",
        "address2": "",
        "city": "Knoxville",
        "state": "TN",
        "postal_code": "77777",
        "country": "US",
        "phone": "208-555-5555"
      },
      "return_address": {
        "title": "Acme",
        "name": "Doug Jones",
        "company": "Acme Manufacturing",
        "address1": "817 E Maple Ln",
        "address2": "",
        "city": "Knoxville",
        "state": "TN",
        "postal_code": "55555",
        "country": "US",
        "phone": ""
      },
      "checkout_data": {
        "Order Notes": "Please leave by back door"
      },
      "order_metadata": {
        "fraud_protection_score": 0
      },
      "discount_list": [],
      "order_notes": [],
      "order_items": [
      {
        "id": "1670028",
        "name": "Subscription Product",
        "price": 19,
        "quantity": 1,
        "weight": 2.375,
        "code": "126478",
        "delivery_type": "ship",
        "category_code": "DEFAULT",
        "variation_list": [],
        "metadata": {
          "image": "http://img1.wikia.nocookie.net/__cb20130318151721/epicrapbattlesofhistory/images/6/6d/Rick-astley.jpg"
      }
    }
  ]
}
```


### Query Parameters

To search for a specific order, you can filter your request with the folowing fields in your querystring.

Parameter | Description
--------- | -----------
`folder_id` | Search for orders from a particular folder. For multiple folders, enter multiple ID's separated by a comma: `1004,1009,1010`
`folder_name` | Search for orders from a particular folder. Enter the folder's exact name instead of its ID.
`source_id` | The source id
`source_name` | The source name
`search_start_date` | Start date from when an order was added. Search in local store time.
`search_end_date` | End date from when an order was added. Search in local store time.
`modified_start_date` | Start date from when an order was modified. Search in local store time.
`modified_end_date` | End date from when an order was modified. Search in local store time.
`email` | Search for orders with a particular email address
`customer_id` | Search for orders with a particular customer ID
`customer_first_name` | Search the customer first name field
`customer_last_name` | Search the customer first name field
`customer_company` | Search the customer company field
`customer_address1` | Search the customer address1 field
`shipping_first_name` | Search the shipping first name field
`shipping_last_name` | Search the shipping first name field
`shipping_company` | Search the shipping company field
`shipping_address1` | Search the shipping address1 field
`customer_phone` | Search the customer phone field
`shipping_phone` | Search the shipping phone field
`get_order_history` | Set this to `1` to include order history. This slows down the results considerably so use carefully.
`order_by` | Order the query by an order field. Defaults to `date_added`
`order` | `ASC` or `DESC`, defaults to `DESC`
`limit` | How many orders to return, defaults to `50`, limit of `500`
`offset` | The number of records to offset


## Create an Order

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-post">POST</i>
    <h6>https://app.orderdesk.me/api/v2/orders</h6>
  </div>
</div>

<aside class="notice">
See <a href="#order-properties">Order Properties</a> for details about the order JSON
</aside>

You must include some `order_items` and at least one of the following fields: `customer_first_name`, `customer_last_name`, `customer_company`, `shipping_first_name`, `shipping_last_name`, `shipping_company`.


## Update An Order

You must pass the entire order as any parts left out will be updated as blank. Order items may be passed in as well. If an `id` field is passed with the `order_item` it will be updated. Otherwise it will be added. Shipments may not be modified with this process.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-put">PUT</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;</h6>
  </div>
</div>


<aside class="notice">
See <a href="#order-properties">Order Properties</a> for details about the order JSON
</aside>



## Delete an Order

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-delete">DELETE</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;</h6>
  </div>
</div>

The `order_id` field refers to Order Desk's internal ID.

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$result = $od->delete("orders/736745");
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/736745"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X DELETE
```

## Create an Order History Item

Passing the `source_name` is not required.

### HTTP Request
<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-post">POST</i>
    <h6>https://app.orderdesk.me/api/v2/orders/&lt;order_id&gt;/order-history</h6>
  </div>
</div>

```php
<?php
include "order-desk-api-client.php";
$od = new OrderDeskApiClient($storeid, $apikey);
$args = array(
  "note" => "My New Note",
  "source_name" => "API",
);
$result = $od->post("orders/736745/order-history", $args);
echo "<pre>" . print_r($result, 1) . "</pre>";
?>
```

```shell
curl "https://app.orderdesk.me/api/v2/orders/736745/order-history"
  -H "ORDERDESK-STORE-ID: storeid"
  -H "ORDERDESK-API-KEY: apikey"
  -H "Content-Type: application/json"
  -X POST
  -d '{"note": "My New Note", "source_name": "API"}'
```

> Response

```json
{
  "status": "success",
  "execution_time": "0.1524 seconds",
  "total_records": 1,
  "order": {
  ...
    "order_history": [
      {
        "source_name": "API",
        "note": "My New Note",
        "date_added": "2015-10-28 23:14:30"
      }
    ]
  }
}
```

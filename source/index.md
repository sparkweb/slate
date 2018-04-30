---
title: Order Desk API Reference

language_tabs:
  - php : PHP
  - shell : cURL

toc_footers:
  - <a href='https://help.orderdesk.me/' target='_blank'>Support site</a>
  - <a href='http://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - authentication
  - orders
  - order_items
  - shipments
  - inventory_items
  - orders_move
  - store_settings
  - references

search: true
---

# Introduction

Order Desk provides an API for programatic access to your store’s data.The Order Desk API is a RESTful API that accepts and returns JSON. You can use the API to pull order status, add orders, add shipments, and retrieve inventory items.



## API Usage and Availability

While we endeavor to ensure that the API has 100% uptime, the API access should not be assumed. It’s best to connect to the Order Desk API in a background process on your end and not through a customer-facing interface. For example, don’t import orders into Order Desk and then wait for a response as part of your shopping cart’s order flow. A better method would be to import orders into your order system and then set up a cron job on your end to attempt to import these orders into the Order Desk API in an asynchronous process.




## PHP Client

If you are developing in PHP, we have a [helper client available](https://gist.github.com/sparkweb/c6a5a21ab44a23589b9c).

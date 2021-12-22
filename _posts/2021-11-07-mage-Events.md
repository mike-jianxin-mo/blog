---
title: Magento - Event
author: Mike Mo
date: 2021-11-07
category: Magento
layout: post
---

### All Events
Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/event-list.html

### checkout events

- checkout_cart_add_product_complete
- checkout_cart_update_item_complete
- checkout_cart_product_add_after
- checkout_cart_update_items_before
- checkout_cart_update_items_after
- checkout_cart_save_before
- checkout_cart_save_after
- checkout_cart_product_update_after

### Category: DB or Logic Entity
##### DB(mode)
- sales_order_save_before/after

#####


### Category: Object & Abstract
##### Abstract
- _save_after
- controller_action_predispatch_
- ... 

##### Object
- sales_order_save_after

### Category: Logic
- checkout_cart_save_before

### Category: Process flow
- controller_action_predispatch
- controller_action_predispatch_
- controller_action_layout_render_before
- controller_action_noroute
- controller_front_send_response_before

- sales_quote_add_item
- sales_quote_remove_item
- 
### Category: Action
- catalog_controller_product_view

### Category: General operation
- (collection)_load_after
- (collection)_load_before
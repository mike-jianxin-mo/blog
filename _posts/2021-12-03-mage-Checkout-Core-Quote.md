---
title: Magento - Quote
author: Mike Mo
date: 2021-12-03
category: Magento
layout: post
---

### Quote Vs Cart
The Cart is deprecated
``
@deprecated 100.1.0 Use \Magento\Quote\Model\Quote instead
./vendor/magento/module-checkout/Model/Cart.php
``

### Events
Ref: https://devdocs.magento.com/guides/v2.4/mrg/module-quote.html

The Quote module dispatches the following events:

- sales_quote_address_collection_load_after event in the \Magento\Quote\Model\ResourceModel\Quote\Address\Collection::_afterLoad method. Parameters:
quote_address_collection is a $this object (Magento\Quote\Model\ResourceModel\Quote\Address\Collection class)

- items_additional_data event in the \Magento\Quote\Model\Cart\Totals\ItemConverter::modelToDataObject method. Parameters:
item is a quote_item object (\Magento\Quote\Model\Quote\Item class)
- sales_quote_remove_item event in the \Magento\Quote\Model\Quote::removeItem method. Parameters:
quote_item is a quote_item object (\Magento\Quote\Model\Quote\Item class)
- <strong>sales_quote_add_item</strong> event in the \Magento\Quote\Model\Quote::addItem method. Parameters:
quote_item is a quote_item object (\Magento\Quote\Model\Quote\Item class)
- sales_quote_product_add_after event in the \Magento\Quote\Model\Quote::addProduct method. Parameters:
items is an array with quot_item objects (\Magento\Quote\Model\Quote\Item class)
- sales_quote_merge_before event in the \Magento\Quote\Model\Quote::merge method. Parameters:
quote is a $this object (\Magento\Quote\Model\Quote class)
source is a quote object (\Magento\Quote\Model\Quote class)
- sales_quote_merge_after event in the \Magento\Quote\Model\Quote::merge method. Parameters:
quote is a $this object (\Magento\Quote\Model\Quote class)
source is a quote object (\Magento\Quote\Model\Quote class)
- sales_convert_quote_to_order event in the \Magento\Quote\Model\Quote\Address\ToOrder::convert method. Parameters:
order is an order object (\Magento\Sales\Model\Order class)
quote is a quote object (\Magento\Quote\Model\Quote class)
- sales_quote_item_qty_set_after event in the \Magento\Quote\Model\Quote\Item::setQty method. Parameters:
item is a $this object (\Magento\Quote\Model\Quote\Item class)
- sales_quote_item_set_product event in the \Magento\Quote\Model\Quote\Item::setProduct method. Parameters:
product is a product object (\Magento\Catalog\Model\Product class)
quote_item is a $this object (\Magento\Quote\Model\Quote\Item class)
- sales_quote_payment_import_data_before event in the \Magento\Quote\Model\Quote\Payment::importData method. Parameters:
payment is a $this object (\Magento\Quote\Model\Quote\Payment class)
input is a data object (\Magento\Framework\DataObject class)
- sales_quote_collect_totals_before event in the \Magento\Quote\Model\Quote\TotalsCollector::collect method. Parameters:
quote is a quote object (\Magento\Quote\Model\Quote class)
- sales_quote_collect_totals_after event in the \Magento\Quote\Model\Quote\TotalsCollector::collect method. Parameters:
quote is a quote object (\Magento\Quote\Model\Quote class)
- sales_quote_address_collect_totals_before event in the \Magento\Quote\Model\Quote\TotalsCollector::collectAddressTotals method. Parameters:
quote is a quote object (\Magento\Quote\Model\Quote class)
shipping_assignment is a shipping_assignment object (\Magento\Quote\Model\ShippingAssignment class)
total is a total object (\Magento\Quote\Model\Quote\Address\Total class)
- sales_quote_address_collect_totals_after event in the \Magento\Quote\Model\Quote\TotalsCollector::collectAddressTotals method. Parameters:
quote is a quote object (\Magento\Quote\Model\Quote class)
shipping_assignment is a shipping_assignment object (\Magento\Quote\Model\ShippingAssignment class)
total is a total object (\Magento\Quote\Model\Quote\Address\Total class)
- checkout_submit_before event in the \Magento\Quote\Model\QuoteManagement::placeOrder method. Parameters:
quote is a quote object (\Magento\Quote\Model\Quote class)
- checkout_submit_all_after event in the \Magento\Quote\Model\QuoteManagement::placeOrder method. Parameters:
order is an order object (\Magento\Sales\Model\Order class)
quote is a quote object (\Magento\Quote\Model\Quote class)
- <strong>sales_model_service_quote_submit_before</strong> event in the \Magento\Quote\Model\QuoteManagement::submitQuote method. Parameters:
order is an order object (\Magento\Sales\Model\Order class)
quote is a quote object (\Magento\Quote\Model\Quote class)
- sales_model_service_quote_submit_success event in the \Magento\Quote\Model\QuoteManagement::submitQuote method. Parameters:
order is an order object (\Magento\Sales\Model\Order class)
quote is a quote object (\Magento\Quote\Model\Quote class)
- sales_model_service_quote_submit_failure event in the \Magento\Quote\Model\QuoteManagement::rollbackAddresses method. Parameters:
order is an order object (\Magento\Sales\Model\Order class)
quote is a quote object (\Magento\Quote\Model\Quote class)
exception is an exception object (\Exception class)
- prepare_catalog_product_collection_prices event in the \Magento\Quote\Model\ResourceModel\Quote\Item\Collection::_assignProducts method. Parameters:
collection is a product collection object (\Magento\Quote\Model\ResourceModel\Quote\Item\Collection class)
store_id is a store ID (int type)
- sales_quote_item_collection_products_after_load event in the \Magento\Quote\Model\QuoteManagement::_assignProducts method. Parameters:
collection is a product collection object (\Magento\Catalog\Model\ResourceModel\Product\Collection class)

### Public APIs
<strong>Still have some names with "cart"</strong>
- Data Interfaces
- General
- Guest
- Registered User
- Model


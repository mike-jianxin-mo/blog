---
title: Magento - Address Template
author: Mike Mo
date: 2021-11-12
category: Magento
layout: post
---

### Address Template

Ref: https://magento.stackexchange.com/questions/157951/magento2-change-standard-address-format-on-magento-frontend

##### Sales Document (Admin Settings)
You can modify the template that determines the format of customer billing and shipping addresses that appear on:
- printed invoices, 
- shipments, 
- refunds, 
- the address book of the customer account.

Ref: https://docs.magento.com/user-guide/customers/address-templates.html

Login into Magento Admin > STORES > Configuration > CUSTOMERS > Customer Configuration > Address Templates

enter image description here

You also can find in the config xml: vendor/magento/module-customer/etc/config.xml

[EDIT]

##### Checkout Page
We cannot use this config for billing and shipping format on checkout page. In this case, we need to check the format:

- vendor/magento/module-checkout/view/frontend/web/template/shipping-address/address-renderer/default.html

- vendor/magento/module-checkout/view/frontend/web/template/billing-address/details.html
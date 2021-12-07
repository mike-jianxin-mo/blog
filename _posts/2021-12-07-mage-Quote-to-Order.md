---
title: Magento - Quote to Order
author: Mike Mo
date: 2021-12-07
category: Magento
layout: post
---

### Copy fields
- Ref: 
  - https://devdocs.magento.com/guides/v2.4/ext-best-practices/tutorials/copy-fieldsets.html
  - https://aureatelabs.com/magento-2/what-is-the-purpose-of-extension-attributes-in-magento-2/

- Step 1: Define your attributes
  etc/extension_attributes.xml
  ```
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Api/etc/extension_attributes.xsd">
    <extension_attributes for="Magento\Quote\Api\Data\CartInterface">
        <attribute code="demo" type="string" />
    </extension_attributes>
    <extension_attributes for="Magento\Sales\Api\Data\OrderInterface">
        <attribute code="demo" type="string" />
    </extension_attributes>
    </config>
  ```
  - for - The fully-qualified type name with the namespace that processes the extensions. The value must be a type that implements `ExtensibleDataInterface`. The interface can be in a different module.
  - code - The name of the attribute. The attribute name should be in snake case (the first letter in each word should be in lowercase, with each word separated by an underscore). 
  - type - The data type. This can be a simple data type, such as string or integer, or complex type, such as an interface.
  - NOTE:
  (From: https://aureatelabs.com/magento-2/what-is-the-purpose-of-extension-attributes-in-magento-2/)
  Now clear the var/generation when you run setup:di:compile command, new getter and setter methods will be added in /var/generation/Magento/Checkout/Api/Data/ShippingInformationExtensionInterface.php

- Step 2: Configure the fieldset
  etc/fieldset.xml

- Step 3: Copy the fieldset
  Event: <strong>sales_model_service_quote_submit_before</strong>

  Configuration file:
  etc/events.xml

### Preparation:
Add fields/columns to the quote & sales_order table.


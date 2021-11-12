---
title: Magento - Total - Sales.xml
author: Mike Mo
date: 2021-11-12
category: Magento
layout: post
---

### Total - Sales.xml

sales.xml contains all kind of total objects like discount, subtotal, grandtotal, tax which display on cart page or order details page in admin and many more places. I can say everthing that is related to total in quote or order defines in this file.

You can add your custom total object as well using this file. Check below link for more details

https://magento.stackexchange.com/questions/92774/how-to-add-fee-to-order-totals-in-magento-2


Example of Sales.xml:

```
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Sales:etc/sales.xsd">
    <section name="quote">
        <group name="totals">
            <item name="tax_subtotal" instance="Magento\Tax\Model\Sales\Total\Quote\Subtotal" sort_order="200"/>
            <item name="tax_shipping" instance="Magento\Tax\Model\Sales\Total\Quote\Shipping" sort_order="300"/>
            <item name="tax" instance="Magento\Tax\Model\Sales\Total\Quote\Tax" sort_order="450">
                <renderer name="adminhtml" instance="Magento\Sales\Block\Adminhtml\Order\Create\Totals\Tax"/>
                <renderer name="frontend" instance="Magento\Tax\Block\Checkout\Tax"/>
            </item>
            <item name="subtotal">
                <renderer name="adminhtml" instance="Magento\Sales\Block\Adminhtml\Order\Create\Totals\Subtotal"/>
                <renderer name="frontend" instance="Magento\Tax\Block\Checkout\Subtotal"/>
            </item>
            <item name="shipping">
                <renderer name="adminhtml" instance="Magento\Sales\Block\Adminhtml\Order\Create\Totals\Shipping"/>
                <renderer name="frontend" instance="Magento\Tax\Block\Checkout\Shipping"/>
            </item>
            <item name="discount">
                <renderer name="adminhtml" instance="Magento\Sales\Block\Adminhtml\Order\Create\Totals\Discount"/>
                <renderer name="frontend" instance="Magento\Tax\Block\Checkout\Discount"/>
            </item>
            <item name="grand_total">
                <renderer name="adminhtml" instance="Magento\Sales\Block\Adminhtml\Order\Create\Totals\Grandtotal"/>
                <renderer name="frontend" instance="Magento\Tax\Block\Checkout\Grandtotal"/>
            </item>
        </group>
    </section>
</config>

```
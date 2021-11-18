---
title: Magento - Customer Account Menu Link
author: Mike Mo
date: 2021-11-18
category: Magento
layout: post
---

### Costomer Account Menu Link
Ref: https://blog.magezon.com/add-link-my-account-menu/

##### Loyout Handler
customer_account.xml 

##### Block Name
customer_account_navigation

##### Update Details
- Path
- Navigation
- Code  
    ```
    <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
        <body>
            <referenceBlock name="customer_account_navigation">
                <block class="Magento\Framework\View\Element\Html\Link\Current" name="magezon_tutorial_custom_my_account">
                    <arguments>
                        <argument name="path" xsi:type="string">tutorial/account/custom</argument>
                        <argument name="label" xsi:type="string">My custom</argument>
                        <argument name="sortOrder" xsi:type="number">150</argument>
                        <argument name="navigation" xsi:type="boolean">true</argument>
                    </arguments>
                </block>
            </referenceBlock>
        </body>
    </page>
    ```
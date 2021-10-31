---
title: Magento 2 - Block & Template
author: Mike Mo
date: 2021-10-31
category: Magento
layout: post
---

#### Replace the template file of a block

##### 1. Layout updates - setTemplate

<referenceBlock name="customer_form_register">
    <action method="setTemplate">
        <argument name="template" xsi:type="string">VendorName_ModuleName::form/register.phtml</argument>
    </action>
</referenceBlock>

Also if you are using Enterprise Edition, make sure to put <strong>The core Module</strong> to sequence in your module.xml because it also overrides this template and may override your changes.

##### 2. Copy the template file to theme directly

./app/design/frontend/Tde/tde2020/Magento_Checkout/templates/onepage.phtml
./vendor/magento/module-checkout/view/frontend/templates/onepage.phtml

##### 3. Remove the block then re-add it :)

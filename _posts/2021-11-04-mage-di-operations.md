---
title: Magento - Di operations
author: Mike Mo
date: 2021-11-04
category: Magento
layout: post
---

##### Remove
```
    <body>
        <referenceBlock name="block_name" remove="true"/>
    </body>
```
```
    <remove src="css/js-accordion/jquery.accordion.css" />
```

##### Move
```
        <move element="customer-account-navigation-billing-agreements-link"
              destination="customer_account_navigation"
              after="customer-account-navigation-newsletter-subscriptions-link"/>
```
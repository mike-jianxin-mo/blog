---
title: Magento - Scope
author: Mike Mo
date: 2021-12-10
category: Magento
layout: post
---
Ref: https://amasty.com/knowledge-base/what-is-the-difference-between-magento-2-website-store-and-store-view.html 

Magento 2 has a 4-level hierarchy: Global, Website, Store, and Store View. Let’s consider the difference between them and their opportunities.

### Global
This is the highest level in the Magento pyramid. Here you can set the only 3 options that will be the same for all stores:

- Stock - configure the main product settings;
- Price - define the same price for the products in all stores;
- Buyers - merge all store customer data into one big database for all websites.

### Website
With one Magento base, you can design <strong>various websites URL</strong>, for example, hats.com and pants.com. You can set different payment and shipping methods, goods can have different prices, currencies, and websites; have a separate client base. Also, for each website, you can create multiple stores. But all the information will be gathered in one admin panel.

### Store
It’s possible to create several stores on one Magento 2 website. 
For each store, 
- you can use different products and category structures. 
- But all stores have <strong>the same currency and prices, payment and shipping methods, taxes, stock management system, customer accounts.</strong>

### Store View
And finally, for every store, you can create several store views. Magento store views are usually used for different languages and currencies. All store views have the same categories, but you can specify different product prices. 


Ref: https://magento.stackexchange.com/questions/7393/difference-between-website-stores-and-store-views

Magento 2 has a 4-level hierarchy: Global, Website, Store (Store Group) & Store View.

# For Single site mode
This is the highest level in the Magento pyramid. Here you can set the only 3 options that will be the same for all stores:

- Stock - configure the main product settings.
- Price - define the same price for the products in all stores.
- Buyers - Merge all store customer data into one big database for all websites.

# Multi-Mode
### Global
Global values are values that are out-of-the-box if the user has not specified. These values are usually defined within a modules etc/config.xml.

By default, a vanilla Magento install features:

1. System configurations (dependent on their scope in declarative schema showInDefault, showInWebsite, showInStore) available in Admin > Stores > Configuration.
1. No Products
1. No Customers
1. 1 Root Category + 1 Default Category without any products
1. 1 Tax Rule: "Taxable goods", 3 Tax Zones / Rates: US-CA. A Non-taxable goods class is also available.
1. 1 Website, 1 Store (Store group), 1 Store View.

### Website
With one Magento base, you can design various websites, for example, hats.com and pants.com. The following can be configured per Website:

1. Separate Payment methods.
1. Separate Shipping methods.
1. A totally separate Product base - products are required to be assigned to websites individually. They can have different prices / currencies / attribute values etc.
1. Separate tax classes.
1. Separate (base) currencies.
1. Separate Customer base - It's up to you whether your customers can log in to all shops with the same credentials.
1. System configurations (dependent on their scope in declarative schema showInDefault, showInWebsite, showInStore) available in Admin > Stores > 1. Configuration. Mostly all configurations are configurable at this level.

For each website, you can create multiple stores, but all the information will be gathered in one admin panel.

### Store
It's possible to create several stores on one Magento 2 website. The following can be configured per Store:

1. <strong>Different Root Categories</strong> which allows for different products to be assigned.

The following <strong>CANNOT be configured per Store</strong>:

1. All the stores within one website share the same customer accounts.
1. All stores share Shipping Methods.
1. All stores share Tax Rates / Zones.
1. All stores share Product stock.
1. All stores share Product prices.
1. All currencies are identical for all the stores.
1. System configurations available in Admin > Stores > Configuration.
1. EAV attributes across entities Customer (including Customer Address), Products, Categories cannot be configured on a Store Group level.

### Store View
Finally, for every store, you can create several store views. The following can be configured per Store View:

1. Different languages.
1. Different currencies.
1. Different design themes
1. Certain Product EAV attributes can be different such as name, or tax class (dependent on their is_global / scope / is_user_defined properties).
1. Different Category EAV attributes (such as name, or URL key).
1. System configurations (dependent on their scope in declarative schema showInDefault, showInWebsite, showInStore) available in Admin > Stores > Configuration.

The following <strong>CANNOT be configured per Store View</strong>:

1. All store views within one website share the same customer accounts.
1. All store views share Shipping Methods.
1. All store views share Tax Rates / Zones.
1. All store views share Product stock.
1. All store views share Product prices.
1. All store views share the same Root Category.
1. All currencies are identical for all the store views.
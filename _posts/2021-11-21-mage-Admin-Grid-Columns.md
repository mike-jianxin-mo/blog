---
title: Magento - Admin Grid Columns
author: Mike Mo
date: 2021-11-21
category: Magento
layout: post
---

### The Data Provider Way
#### Joints
- A layout handler, such as sales_order_grid
- Add a column: <strong>columns</strong>
- Add column data:     
  ```Magento\Framework\View\Element\UiComponent\DataProvider\CollectionFactory```

#### Extend UI
- Update the corresponding layout handler
- Extend from the <strong>columns</strong>
  - Key elements:
    - filter
    - dataType

#### Extend Data
- A General Data Extension Point:     
  ```Magento\Framework\View\Element\UiComponent\DataProvider\CollectionFactory```

#### Ref:
https://www.mageworx.com/blog/how-to-add-column-with-filter-to-magento-2-orders-grid/


### The Search Result Plugin Way

#### Joints
- A layout handler, such as sales_order_grid
- Add a columnm with custom class
  - extend: \Magento\Ui\Component\Listing\Columns\Column
  - key function: <strong>prepareDataSource</strong>
  In prepareDataSource function, we get the current order id. Using this order id we are querying our custom module database table to fetch the appropriate short_name.
- Add filter after plugin:
  - plugined class: Magento\Framework\View\Element\UiComponent\DataProvider\Reporting
  - change the afterSearch function
    
#### Ref:
- https://www.codextblog.com/magento-2/how-to-add-a-custom-column-in-order-grid-in-magento-2/
- https://magento.stackexchange.com/questions/134754/magento-2-how-to-add-a-new-column-to-orders-grid


### The VirtualType Way
The grid columns are defined in a virtual Magento\Sales\Model\ResourceModel\Order\Grid class in the Magento_Sales dependency injection (di.xml) file. You can study the file to see how to select columns and join data from other tables.


#### Joints
- A layout handler, such as sales_order_grid
- Add a column: <strong>columns</strong>
- Add column value to the Grid Data a virtualType
    ```
    <?xml version="1.0"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
        <virtualType name="Magento\Sales\Model\ResourceModel\Order\Grid">
            <arguments>
                <argument name="columns" xsi:type="array">
                    <item name="coupon_code" xsi:type="string">sales_order.coupon_code</item>
                </argument>
            </arguments>
        </virtualType>
        <virtualType name="Magento\SalesArchive\Model\ResourceModel\Order\Grid">
            <arguments>
                <argument name="columns" xsi:type="array">
                    <item name="coupon_code" xsi:type="string">sales_order.coupon_code</item>
                </argument>
            </arguments>
        </virtualType>
    </config>
    ```
#### Ref:
- https://magento.stackexchange.com/questions/134754/magento-2-how-to-add-a-new-column-to-orders-grid

### The VirtualType Way 2: Data from another table

Ref: 
https://magento.stackexchange.com/questions/126534/add-custom-column-to-customer-admin-grid/126849

### PS. Grid with arbitrary colleciton
- Define the datasource
```
 <virtualType name="DevGridCategoryCollection" type="Dev\Grid\Ui\DataProvider\Category\Listing\Collection">
   <arguments>
     <argument name="mainTable" xsi:type="string">catalog_category_entity</argument>
     <argument name="resourceModel" xsi:type="string">Dev\Grid\Model\ResourceModel\Category</argument>
   </arguments>
 </virtualType>
```
- Setup the select statement
```
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

namespace Dev\Grid\Ui\DataProvider\Category\Listing;

use Magento\Framework\View\Element\UiComponent\DataProvider\SearchResult;

class Collection extends SearchResult
{
    /**
     * Override _initSelect to add custom columns
     *
     * @return void
     */
    protected function _initSelect()
    {
        $this->addFilterToMap('entity_id', 'main_table.entity_id');
        $this->addFilterToMap('name', 'devgridname.value');
        parent::_initSelect();
    }
}
```

Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/admin-grid.html

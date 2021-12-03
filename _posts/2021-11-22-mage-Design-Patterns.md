---
title: Magento - Design Pattern
author: Mike Mo
date: 2021-11-22
category: Magento
layout: post
---

### Event-Observer Pattern
There two types of events triggerred by system.
One is the system events, the other is the model specific events.

<strong> Eg. Model Save</strong>
- System events
  - model_save_after
  - model_save_commit_after
  - model_save_before
- Model specific events
  - < eventPrefix >_save_after
  - < eventPrefix >_save_commit_after
  - < eventPrefix >_save_before
  
### Object Pool Pattern
Ref: https://webkul.com/blog/magento2-object-pool-pattern/
Router
```
  <type name="Magento\Framework\App\RouterList">
      <arguments>
          <argument name="routerList" xsi:type="array">
              <item name="customrouter" xsi:type="array">
                  <item name="class" xsi:type="string">Vendor\Module\Controller\CustomRouter</item>
                  <item name="disable" xsi:type="boolean">false</item>
                  <item name="sortOrder" xsi:type="string">22</item>
              </item>
          </argument>
      </arguments>
  </type>
```
Command (CommandListInterface):
```
    <type name="Magento\Framework\Console\CommandList">
        <arguments>
            <argument name="commands" xsi:type="array">
                <item name="enable_all_phone_cases" xsi:type="object">Abc\Catalog\Console\EnableMobileViewFunc</item>
            </argument>

            <argument name="commands" xsi:type="array">
                <item name="adding_flat_fee_options" xsi:type="object">Abc\Catalog\Console\PatternOptionOperationCommands\FlatFeeOptions</item>
            </argument>

        </arguments>
    </type>
```
Admin Grid: A Collection Pool.
```
    <virtualType name="Tde\CorNikon\Model\ResourceModel\CorNikonRequest\Grid\Collection" type="Magento\Framework\View\Element\UiComponent\DataProvider\SearchResult">
        <arguments>
            <argument name="mainTable" xsi:type="string">tde_nikon_request</argument>
            <argument name="resourceModel" xsi:type="string">Tde\CorNikon\Model\ResourceModel\CorNikonRequest</argument>
        </arguments>
    </virtualType>
    <!-- an Object Pool of Collections -->
    <type name="Magento\Framework\View\Element\UiComponent\DataProvider\CollectionFactory">
        <arguments>
            <argument name="collections" xsi:type="array">
                <item name="cornikon_requests_listing_data_source" xsi:type="string">Tde\CorNikon\Model\ResourceModel\CorNikonRequest\Grid\Collection</item>
            </argument>
        </arguments>
    </type>
```
### Proxy Pattern
Ref: https://webkul.com/blog/magento2-proxy-design-pattern-code-generation/

### Service Contract
Ref: https://webkul.com/blog/magento2-service-contract/

### Repository Pattern
Ref: https://webkul.com/blog/magento2-repository-design-pattern/

### Dependency Inject
Ref: https://webkul.com/blog/dependency-injection/


### Modifier


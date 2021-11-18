---
title: Magento - DB: The Material View
author: Mike Mo
date: 2021-11-17
category: Magento
layout: post
---

### The Material View


##### mview.xml
Define the class used to handle the database column updates.

```
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Mview/etc/mview.xsd">
    <view id="amasty_feed_entity" class="Amasty\Feed\Model\Indexer\Feed\FeedRuleIndexer" group="indexer">
        <subscriptions>
            <table name="amasty_feed_entity" entity_column="entity_id" />
        </subscriptions>
    </view>
    <view id="amasty_feed_product" class="Amasty\Feed\Model\Indexer\Product\ProductFeedIndexer" group="indexer">
        <subscriptions>
            <table name="catalog_product_entity" entity_column="entity_id" />
            <table name="catalog_product_entity_datetime" entity_column="entity_id" />
            <table name="catalog_product_entity_decimal" entity_column="entity_id" />
            <table name="catalog_product_entity_gallery" entity_column="entity_id" />
            <table name="catalog_product_entity_int" entity_column="entity_id" />
            <table name="catalog_product_entity_media_gallery_value" entity_column="entity_id" />
            <table name="catalog_product_entity_text" entity_column="entity_id" />
            <table name="catalog_product_entity_tier_price" entity_column="entity_id" />
            <table name="catalog_product_entity_varchar" entity_column="entity_id" />
            <table name="catalog_category_product" entity_column="product_id" />
        </subscriptions>
    </view>
</config>

```

Ref: https://magento.stackexchange.com/questions/117030/what-is-mview-in-magento-2

---
title: Magento - Indexer
author: Mike Mo
date: 2021-12-15
category: Magento
layout: post
---

### Ref
Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html

### Class
Implementation Interfaces
```
\Magento\Framework\Indexer\ActionInterface
```
```
\Magento\Framework\Mview\ActionInterface
```

### Order of indexers
Ref: https://magento.stackexchange.com/questions/5038/order-of-indexing

The indexing order when reindexing all processes is defined by Mage_Index_Model_Indexer::_runAll().
This method uses the depends property of each process to check which other processes have to run before itself can do it's work.

The getDepends() method of the index/process uses the configuration node global/index/indexer/[process-code]/depends to determine it's dependencies.

To have the *_flat indexer processes run before the catalog_url reindexing, it should be enough to add a dependency as follows:
```
<catalog_url>
    <model>catalog/indexer_url</model>
    <depends>
        <catalog_product_flat/>
        <catalog_category_flat/>
    </depends>
</catalog_url>
```
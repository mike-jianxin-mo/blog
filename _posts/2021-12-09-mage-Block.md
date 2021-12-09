---
title: Magento - Block
author: Mike Mo
date: 2021-12-09
category: Magento
layout: post
---

### Main Class
```
Magento\Framework\View\Element\AbstractBlock
```

### Main function
```
render()
```

### Process
- Create
  ```
  /** @var \Magento\Framework\Pricing\Render\RendererPool $rendererPool */
        $rendererPool = $this->priceLayout->getBlock('render.product.prices');
  ```
- Set Template
    ```
    $renderBlock->setTemplate($this->getRenderBlockTemplate($type, $priceCode));
    ```
- to Html
    ```
    $priceRender->toHtml()
    ```


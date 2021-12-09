---
title: Magento - A Layout Joint, Render price
author: Mike Mo
date: 2021-12-09
category: Magento
layout: post
---

Ref:https://belvg.com/blog/the-functionality-and-basic-concepts-of-price-generation-in-magento-2.html

### Layout Joint
Use block/template as a block arguments, not as child block. 
Argumentsare are in pair, including:
- A block class, althought it is not named with block, but it is deritive from the AbstractBlock class
- A template.

### Example: the price render method
- Joint Point: 
  - Handler: catalog_product_prices.xml
  - Name: render.product.prices

Block Name: ```render.product.prices```
```
<block class="Magento\Framework\Pricing\Render\RendererPool" name="render.product.prices">
    <arguments>
        <argument name="default" xsi:type="array">
            <item name="default_render_class" xsi:type="string">Magento\Catalog\Pricing\Render\PriceBox</item>
            <item name="default_render_template" xsi:type="string">Magento_Catalog::product/price/default.phtml</item>
            <item name="default_amount_render_class" xsi:type="string">Magento\Framework\Pricing\Render\Amount</item>
            <item name="default_amount_render_template" xsi:type="string">Magento_Catalog::product/price/amount/default.phtml</item>
            <item name="prices" xsi:type="array">
                <item name="special_price" xsi:typex="array">
                    <item name="render_template" xsi:type="string">Magento_Catalog::product/price/special_price.phtml</item>
                </item>
                <item name="tier_price" xsi:type="array">
                    <item name="render_template" xsi:type="string">Magento_Catalog::product/price/tier_prices.phtml</item>
                </item>
                <item name="final_price" xsi:type="array">
                    <item name="render_class" xsi:type="string">Magento\Catalog\Pricing\Render\FinalPriceBox</item>
                    <item name="render_template" xsi:type="string">Magento_Catalog::product/price/final_price.phtml</item>
                </item>
                <item name="custom_option_price" xsi:type="array">
                    <item name="amount_render_template" xsi:type="string">Magento_Catalog::product/price/amount/default.phtml</item>
                </item>
                <item name="configured_price" xsi:type="array">
                    <item name="render_class" xsi:type="string">Magento\Catalog\Pricing\Render\ConfiguredPriceBox</item>
                    <item name="render_template" xsi:type="string">Magento_Catalog::product/price/configured_price.phtml</item>
                </item>
            </item>
            <!--<item name="adjustments" xsi:type="array"></item>-->
        </argument>
    </arguments>
</block>
```

### Usage
In the <strong>render</strong> function, init the Join block and get the toHtml() function.
- Layout settings
```
<block class="Dotdigitalgroup\Email\Block\Recommended\Wishlistproducts" name="ddg.wishlist.upsell.container" template="Dotdigitalgroup_Email::product/list.phtml" cacheable="false">
    <block class="Magento\Framework\Pricing\Render" name="ddg.product.price.render.default">
        <arguments>
            <argument name="price_render_handle" xsi:type="string">catalog_product_prices</argument>
            <argument name="use_link_for_as_low_as" xsi:type="boolean">true</argument>
        </arguments>
    </block>
</block>
```

- Class Magento\Framework\Pricing\Render
```
    public function render($priceCode, SaleableInterface $saleableItem, array $arguments = [])
    {
        $useArguments = array_replace($this->_data, $arguments);

        /** @var \Magento\Framework\Pricing\Render\RendererPool $rendererPool */
        $rendererPool = $this->priceLayout->getBlock('render.product.prices');
        ... ...

        // obtain concrete Price Render
        $priceRender = $rendererPool->createPriceRender($priceCode, $saleableItem, $useArguments);
        return $priceRender->toHtml();
    }
```

### Real render block & template
Magento\Catalog\Pricing\Render\FinalPriceBox
Magento_Catalog::product/price/final_price.phtml

---
title: Magento - Checkout Cart Item
author: Mike Mo
date: 2021-11-18
category: Magento
layout: post
---

### Layout Handler
<strong>checkout_item_renderers.xml</strong>

### Injection
- Example
  - vendor/magento/module-multishipping/view/frontend/layout/multishipping_checkout_addresses.xml
  - vendor/magento/module-multishipping/view/frontend/layout/multishipping_checkout_shipping.xml
  
- Injection Point
    ```
    <block class="Magento\Framework\View\Element\RendererList" name="checkout.cart.item.renderers" as="renderer.list"/>
    ```

- Injection approach
  
  ./vendor/magento/module-checkout/view/frontend/layout/checkout_cart_item_renderers.xml
  
  ```
  <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
        <update handle="checkout_item_price_renderers"/>
        <body>
            <referenceBlock name="checkout.cart.item.renderers">
                <block class="Magento\Checkout\Block\Cart\Item\Renderer" name="checkout.cart.item.renderers.default" as="default" template="Magento_Checkout::cart/item/default.phtml">
                    <block class="Magento\Checkout\Block\Cart\Item\Renderer\Actions" name="checkout.cart.item.renderers.default.actions" as="actions">
                        <block class="Magento\Checkout\Block\Cart\Item\Renderer\Actions\Edit" name="checkout.cart.item.renderers.default.actions.edit" template="Magento_Checkout::cart/item/renderer/actions/edit.phtml"/>
                        <block class="Magento\Checkout\Block\Cart\Item\Renderer\Actions\Remove" name="checkout.cart.item.renderers.default.actions.remove" template="Magento_Checkout::cart/item/renderer/actions/remove.phtml"/>
                    </block>
                </block>
                <block class="Magento\Checkout\Block\Cart\Item\Renderer" name="checkout.cart.item.renderers.simple" as="simple" template="Magento_Checkout::cart/item/default.phtml">
                    <block class="Magento\Checkout\Block\Cart\Item\Renderer\Actions" name="checkout.cart.item.renderers.simple.actions" as="actions">
                        <block class="Magento\Checkout\Block\Cart\Item\Renderer\Actions\Edit" name="checkout.cart.item.renderers.simple.actions.edit" template="Magento_Checkout::cart/item/renderer/actions/edit.phtml"/>
                        <block class="Magento\Checkout\Block\Cart\Item\Renderer\Actions\Remove" name="checkout.cart.item.renderers.simple.actions.remove" template="Magento_Checkout::cart/item/renderer/actions/remove.phtml"/>
                    </block>
                </block>
            </referenceBlock>
        </body>
    </page>

  ```
### Main Block
- Magento\Framework\View\Element\RendererList
- Notes:
  - main function: getRenderer
  - Data: array, rendererTemplates=[]
  - <strong>Joint key: Type</strong>
- Codes
  
```
class RendererList extends AbstractBlock
{
    /**
     * Renderer templates cache
     *
     * @var array
     */
    protected $rendererTemplates = [];

    /**
     * Retrieve renderer by code
     *
     * @param string $type
     * @param string $default
     * @param string $rendererTemplate
     * @return bool|AbstractBlock
     * @throws \RuntimeException
     */
    public function getRenderer($type, $default = null, $rendererTemplate = null)
    {
        /** @var \Magento\Framework\View\Element\Template $renderer */
        $renderer = $this->getChildBlock($type) ?: $this->getChildBlock($default);
        if (!$renderer instanceof BlockInterface) {
            throw new \RuntimeException('Renderer for type "' . $type . '" does not exist.');
        }
        $renderer->setRenderedBlock($this);

        if (!isset($this->rendererTemplates[$type])) {
            $this->rendererTemplates[$type] = $renderer->getTemplate();
        } else {
            $renderer->setTemplate($this->rendererTemplates[$type]);
        }

        if ($rendererTemplate) {
            $renderer->setTemplate($rendererTemplate);
        }
        return $renderer;
    }
}
```

### Parts
Define the renders for different product type, the type name is defined in the as attribute of the block.

Example: vendor/magento/module-checkout/Block/Cart/Item/Renderer.php

```
<block class="Magento\Checkout\Block\Cart\Item\Renderer" name="checkout.cart.item.renderers.simple" as="simple" template="Magento_Checkout::cart/item/default.phtml">
    <block class="Magento\Checkout\Block\Cart\Item\Renderer\Actions" name="checkout.cart.item.renderers.simple.actions" as="actions">
        <block class="Magento\Checkout\Block\Cart\Item\Renderer\Actions\Edit" name="checkout.cart.item.renderers.simple.actions.edit" template="Magento_Checkout::cart/item/renderer/actions/edit.phtml"/>
        <block class="Magento\Checkout\Block\Cart\Item\Renderer\Actions\Remove" name="checkout.cart.item.renderers.simple.actions.remove" template="Magento_Checkout::cart/item/renderer/actions/remove.phtml"/>
    </block>
</block>
```

### Extend Parts
Extend the actions section with a frontend JS feature.

Example: add giftcard message to each quote item.
vendor/magento/module-gift-message/view/frontend/layout/checkout_cart_item_renderers.xml


# Recap
- Blocks are parts.
- RendererList is a general design pattern in Magento.
- Joints are defined in a layout handler
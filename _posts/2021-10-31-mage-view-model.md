---
title: Magento 2 - View Model
author: Mike Mo
date: 2021-11-01
category: Magento
layout: post
---

##### Definition

A view model is an abstraction of the view exposing public properties and commands. It allows developers to offload features and business logic from block classes into separate classes that are easier to maintain, test, and reuse.

##### When to use

- Use this approach anytime you need to inject functionality into template files and your code <strong>does not need to be backwards compatible with Magento</strong>.

- <strong>Replace the helper functions</strong>
The use of helpers in templates is discouraged. It is recommended to use view models instead.

##### How to write view models

1. XML definition
   - New block
   ```
   <block name="examplecorp.new.viewmodel" template="ExampleCorp_Catalog::example.phtml">
    <arguments>
        <argument name="view_model" xsi:type="object">ExampleCorp\Catalog\ViewModel\MyNewViewModel</argument>
    </arguments>
    </block>
    ```

    - Existing(core) block
    ```
    <referenceBlock name="checkout.cart.item.renderers.default">
        <arguments>
            <argument name="view_model" xsi:type="object">ExampleCorp\Catalog\ViewModel\MyNewViewModel</argument>
        </arguments>
    </referenceBlock>
    ```

2. Codes
    <strong> \Magento\Framework\View\Element\Block\ArgumentInterface</strong>
   ```
    namespace ExampleCorp\Catalog\ViewModel;

    class MyNewViewModel implements \Magento\Framework\View\Element\Block\ArgumentInterface
    {
        public function getTitle()
        {
        return 'Hello World';
        }
    }
   ```

3. Usage
    ```
    /** @var $viewModel /Magento/Catalog/ViewModel/Product/Listing/PreparePostData */
    $viewModel = $block->getViewModel();
    $postArray = $viewModel->getPostData(
        $block->escapeUrl($block->getAddToCartUrl($_item)),
        ['product' => $_item->getEntityId()]
    );
    ```

4. Notes
    If the ViewModel does not be defined as the default name, for example, you have multiple view models for one template, then you need to use the following:

    ``` 

    <block class="Magento\Catalog\Block\Product\ListProduct" name="category.products.list" as="product_list" template="Magento_Catalog::product/list.phtml">

            ... ...

            <arguments>
                <argument
                    name="whole_promotion_price_suffix"
                    xsi:type="object">Abc\Catalog\ViewModel\WholeSitePromotionPriceUpdate</argument>
            </arguments>
    </block>

    /**
     * @var Abc\Catalog\ViewModel\WholeSitePromotionPriceUpdate $wholeSitePromotionData
     */
    $wholeSitePromotionData = $block->getData('whole_promotion_price_suffix');
    ```
    <strong>$block->getData('whole_promotion_price_suffix')</strong>

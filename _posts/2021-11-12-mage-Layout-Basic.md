---
title: Magento - UI: The Layout, Block, and Template
author: Mike Mo
date: 2021-11-12
category: Magento
layout: post
---

### Understanding Layout
Layout means page layout, it is used for the result page class.

### Layout activive 
- Header
  default_head_blocks

- Page Layout
  -   To make layout changes available on every page, modify the default.xml file.
  - To add layout changes to a specific page, use a layout file that corresponds to the page’s path. For example, changes to the app/code/Vendor/Module/view/frontend/layout/catalog_product_view.xml page are loaded on the product details page.

### The default page structure: Default.xml
- Basic Layout file: default.xml
  To make layout changes available on every page, modify the default.xml file.
  
  All the global layout updates should be put here. Such as the Facebook pixel, Google Tag Manager, ... ...

- This is a 3columns layout.
  ```
  <page layout="3columns" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <update handle="default_head_blocks"/>
    <body>
  ```

### layout elements
- container
  Containers in a container
  ```
    <?xml version="1.0"?>
    <layout xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_layout.xsd">

        <referenceContainer name="page.wrapper">
            <container name="some.container" as="someContainer" label="Some Container" htmlTag="div" htmlClass="some-container" />
        </referenceContainer>
    </layout>

  ```
  - action
    The <action> instruction is deprecated. If the method implementation allows, use the <argument> for <block> or <referenceBlock> to access the block public API.

    This means that the setTemplate is no longer exist.

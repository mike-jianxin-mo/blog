---
title: Magento - UI: The Layout, Block, and Template
author: Mike Mo
date: 2021-11-12
category: Magento
layout: post
---

### Understanding Layout
Layout means page layout, it is used for the result page class.

### The default page structure: Default.xml
- Basic Layout file: default.xml
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
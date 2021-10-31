---
title: Magento 2 - Add a new laoyout
author: Mike Mo
date: 2021-10-31
category: Magento
layout: post
---

#### Add a 4columns layout

Ref: https://magento.stackexchange.com/questions/197784/how-to-create-a-new-page-layout-with-4-columns

##### 1. Register a new page structure

Custom_Theme/layouts.xml

Declare the layout in VENDOR/THEME/Magento_Theme/layouts.xml

<?xml version="1.0" encoding="UTF-8"?>

<page_layouts xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="urn:magento:framework:View/PageLayout/etc/layouts.xsd">
<layout id="4columns">
<label translate="true">4 columns</label>
</layout>
</page_layouts>

##### 2. The new page layout

Custom_Theme/page_layout/4columns.xml

##### 3. CSS

- Header
  Custom_Theme/layout/default_head_blocks.xml

- Css file
  Custom_Theme/layout/default_head_blocks.xml

##### 4. Column Block

A Template Block

- Layout container
  <container name="column4" htmlTag="div" htmlClass="column-float-left" after="-">
  <block class="Magento\Framework\View\Element\Template" name="test" template="Magento_Theme::lorem.phtml" />
  </container>

- Block template
  Custom_Theme/templates/lorem.phtml

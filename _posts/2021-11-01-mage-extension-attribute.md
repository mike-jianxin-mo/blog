---
title: Magento 2 - Extension Attribute
author: Mike Mo
date: 2021-11-01
category: Magento
layout: post
---

### Introduction
Third-party developers <strong>cannot change the API Data interfaces defined in the Magento Core code</strong>. However, most of these entities have a feature called <strong>extension attributes</strong>. 

Check the interface for the methods getExtensionAttributes() and setExtensionAttributes() to determine if they are available for the entity.

Example: <strong>Product Enitty</strong>

- Product Response
    ```
    <product>
        <id>1</id>
        <sku>some-sku</sku>
        <custom_attributes><!-- Custom Attributes Data --></custom_attributes>
        <extension_attributes><!-- Here should we add extension attributes data --></extension_attributes>
    </product>

    ```

- Product List Response
    ```
    <products>
        <item>
            <id>1</id>
            <sku>some-sku</sku>
            <custom_attributes><!-- Custom Attributes Data --></custom_attributes>
            <extension_attributes><!-- Here should we add extension attributes data --></extension_attributes>
        </item>
        <item>
            <id>2</id>
            <sku>some-sku-2</sku>
            <custom_attributes><!-- Custom Attributes Data --></custom_attributes>
            <extension_attributes><!-- Here should we add extension attributes data --></extension_attributes>
        </item>
    </products>

    ```

### Extensive Attribute VS EAV Attribute
Custom attributes are the attributes added to describe an entity, such as product attributes, customer attributes etc. These are a subset of EAV attributes.

Extension attributes on the other hand are generally used for more complex data types such as adding additional complex data into an entity from a custom external table.

### Read 
Extensive attributes can be auto loaded, if it has been defined in the extensive_attribute.xml.

### Save/Update: Use with Plugin
In order to add extension attributes, we need to use an after plugin on Product Repository. The plugin should be declared for the methods: save, get and getList.

- After Get
```
public function afterGet
(
    \Magento\Catalog\Api\ProductRepositoryInterface $subject,
    \Magento\Catalog\Api\Data\ProductInterface $entity
) {
    $ourCustomData = $this->customDataRepository->get($entity->getId());

    $extensionAttributes = $entity->getExtensionAttributes(); /** get current extension attributes from entity **/
    $extensionAttributes->setOurCustomData($ourCustomData);
    $entity->setExtensionAttributes($extensionAttributes);

    return $entity;
}
```

### With ACL 
[Extensive Attribute with ACL](2021-11-28-mage-ACL.md)

### Use with extensionActions


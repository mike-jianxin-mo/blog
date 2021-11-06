---
title: Magento - EAV Vs Extension Attributes
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

### EAV and Extension attributes

Ref: https://devdocs.magento.com/guides/v2.3/extension-dev-guide/attributes.html

There are two types of attributes you can use to extend Magento functionality:

- Custom and Entity-Attribute-Value (EAV) attributes—Custom attributes are those added on behalf of a merchant. For example, a merchant might need to add attributes to describe products, such as shape or volume. A merchant can add these attributes in the Admin panel. See the merchant documentation for information about managing custom attributes.
<br>
    Custom attributes are a subset of EAV attributes. Objects that use EAV attributes typically store values in several MySQL tables. The Customer and Catalog modules are the primary models that use EAV attributes. Other modules, such as ConfigurableProduct, GiftMessage, and Tax, use the EAV functionality for Catalog.

<br>

- Extension attributes. Extension attributes are new in Magento 2. They are used to extend functionality and often use more complex data types than custom attributes. These attributes do not appear in the Admin.



##### Extension Attributes
Ref: https://devdocs.magento.com/guides/v2.3/extension-dev-guide/attributes.html#extension

###### Declare extension attributes
You must create a <strong> <Module>/etc/extension_attributes.xml</strong> file to define a module’s extension attributes:
```
<config>
    <extension_attributes for="Path\To\Interface">
        <attribute code="name_of_attribute" type="datatype">
           <resources>
              <resource ref="permission"/>
           </resources>
           <join reference_table="" reference_field="" join_on_field="">
              <field>fieldname</field>
           </join>
        </attribute>
    </extension_attributes>
</config>
```

###### Extension via codes:
Ref: https://magento.stackexchange.com/questions/113447/how-to-use-extension-attributes-in-magento2
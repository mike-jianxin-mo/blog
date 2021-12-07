---
title: Magento - XML & Arguments
author: Mike Mo
date: 2021-12-07
category: Magento
layout: post
---

### Constructor
The argument element in the XML settings in Magento will affect the constructor function. It is a powerful tool to customise system.

### Exmplate, the argument of a block (argument Vs action)
We can investigate this via the argument settings of the block elements in layout files.

Ref: https://magento.stackexchange.com/questions/86188/magento-2-changing-a-blocks-template

To understand the difference between <arguments> and <action> you must understand how the constructors of Magento 2 objects work. 
If you override a constructor in Magento, you'll always get a $data-parameter which is an array. 

This is the data as provided in the XML files and translated to the internal <strong>$_data-array</strong> of \Magento\Framework\DataObject:
```
<referenceBlock name="catalog.topnav">
    <arguments>
        <argument name="template" xsi:type="string">Foo_Bar::buzz.phtml</argument>
    </arguments>
</referenceBlock>    

...

public function __construct(array $data = [])
{
    // $_data is populated with the arguments from XML:
    // so $_data['template'] is now 'Foo_Bar::buzz.phtml'
    $this->_data = $data;
}
```

However, in the case of a template, if setTemplate() is used in the pseudo constructor (_construct(), single underscore), this means that the $data is overridden, no matter if it's set in the XML.

```
public function _construct()
{
    $this->setTemplate('foo/bar.phtml');
}
```
Note: It is the <strong>_constructor</strong> not the <strong>__constructor</strong>



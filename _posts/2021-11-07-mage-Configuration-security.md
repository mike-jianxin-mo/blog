---
title: Magento - Configuration Security
author: Mike Mo
date: 2021-11-07
category: Magento
layout: post
---

### Configuration security

Ref: https://magento.stackexchange.com/questions/125127/how-can-i-decrypt-an-encrypted-configuration-value

\Magento\Framework\App\Config\ScopeConfigInterface::getValue will return the decrypted value. When ScopeConfigInterface::getValue returns an encrypted value, the configuration option is setup incorrectly. A correct implementation of an encrypted configuration value is:

    ```
    Vendor/Module/etc/adminhtml/system.xml
    ```

Here we add an <strong>obscure</strong> configuration value in the path payment/webpay/keyid the critical things here is ensuring the field has <strong>type="obscure"</strong> and uses <strong>Magento\Config\Model\Config\Backend\Encrypted</strong> for the backend_model. This is how Magento knows to use a masked form field and encrypt any user input on save.
<strong>Vendor/Module/etc/adminhtml/system.xml </strong>
```
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <section id="payment">
            <group id="webpay">
                <field id="keyid" translate="label" type="obscure" sortOrder="100" showInDefault="1" showInWebsite="1" showInStore="0">
                    <label>Key Id</label>
                    <backend_model>Magento\Config\Model\Config\Backend\Encrypted</backend_model>
                </field>
            </group>
        </section>
    </system>
</config>
```

<strong>Vendor/Module/etc/config.xml</strong>
Adding backend_model="Magento\Config\Model\Config\Backend\Encrypted" here tells Magento the config value should be decrypted when retrieved with ScopeConfigInterface::getValue
```
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <payment>
            <webpay>
                <keyid backend_model="Magento\Config\Model\Config\Backend\Encrypted" />
            </webpay>
        </payment>
    </default>
</config>
```

<strong>Vendor/Module/etc/di.xml</strong>
This adds the configuration path to the sensitive array and prevents the path's value from being included when dumping the store configuration.
```
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Config\Model\Config\TypePool">
        <arguments>
            <argument name="sensitive" xsi:type="array">
                <item name="payment/webpay/keyid" xsi:type="string">1</item>
            </argument>
        </arguments>
    </type>
</config>
```
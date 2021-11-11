---
title: Magento - T
author: Mike Mo
date: 2021-11-07
category: Magento
layout: post
---

### Typepool

##### Sensitive & Environment

Use the following guidelines to determine which settings to designate as sensitive, system-specific, or both.

Magento stores these settings in < Magento root dir >/app/etc/env.php. Do not include this file in source control.

###### Sensitive values
Sensitive configuration values hold restricted or confidential information.

Examples of sensitive information include:

- Keys (such as API keys)
- Usernames and passwords
- E-mail addresses
- Any personally identifiable information (e.g., address, phone number, date of birth, government identification number, etc.)

###### Environment or system-specific values
Environment or system-specific values are unique to the system where Magento is deployed.

Examples of environment or system-specific values include:

- URLs
- IP addresses
- Ports
- Hostnames
- Domain names
- Paths (e.g., custom paths, proxy host, proxy port)
- “modes” (e.g, sandbox mode, debug mode, test mode)
- SSL (only for non-payment)
- E-mail recipients
- Administrative settings between systems (e.g., password expiration limits)

##### Example
```
<type name="Magento\Config\Model\Config\TypePool">
   <arguments>
      <argument name="environment" xsi:type="array">
         <item name="catalog/search/searchengine/port" xsi:type="string">1</item>
      </argument>
   </arguments>
</type>

<type name="Magento\Config\Model\Config\TypePool">
   <arguments>
      <argument name="sensitive" xsi:type="array">
         <item name="payment/test/password" xsi:type="string">1</item>
      </argument>
   </arguments>
</type>
```

```
bin/magento app:config:dump
```
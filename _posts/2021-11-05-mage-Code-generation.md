---
title: Magento - Code Generation
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

### Code Generation
Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/code-generation.html

##### When 
Provided the Magento application is <strong>not set for production mode</strong>, <strong>code is generated when the Magento application cannot find a class when executing code.</strong>


- A Factory class creates instances of a type. See Instantiating objects with factories for more information. Factories are directly referenced within application code.

- You can designate a Proxy to be generated for a type in order to ensure the type is not instantiated until it is needed. See Proxies for more information. Proxies are directly referenced within dependency injection configuration.

- Interceptor classes are automatically generated to facilitate Magento’s plugin system. An interceptor class extends a type and is returned by the Object Manager to allow multiple plugin classes to inject logic into different methods. Interceptors work behind the scenes and are not directly referenced in application code.
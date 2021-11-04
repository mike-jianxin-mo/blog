---
title: Magento - Type Vs Virtual Type
author: Mike Mo
date: 2021-10-17
category: Magento
layout: post
---

##### Type Vs Virtual Type
Ref: 
- https://magento.stackexchange.com/questions/33103/what-is-the-difference-between-type-and-virtualtype (Great!)
- https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html

##### Virtual Type Definition
Virtual types are a way to inject different dependencies into existing classes without affecting other classes.

Type argument would make it so that all instances of the injected class have a namespace of 'core'. Using a virtual type allows for the equivalent of a sub-class to be created, where only the sub-class has the altered argument values

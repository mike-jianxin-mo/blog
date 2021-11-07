---
title: Magento - Event & Observer
author: Mike Mo
date: 2021-11-07
category: Magento
layout: post
---

### Event & Observer

Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/events-and-observers.html

##### Configuration file
```
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Event/etc/events.xsd">
    <event name="my_module_event_after">
        <observer name="my_module_event_after_observer" instance="MyCompany\MyModule\Observer\MyEvent"/>
    </event>
</config>
```

##### Custom Events
EventManager
```
use Magento\Framework\Event\ManagerInterface as EventManager;

$this->eventManager->dispatch('my_module_event_before');

// More code that sets $eventData...
$this->eventManager->dispatch('my_module_event_after', ['myEventData' => $eventData]);
```

##### Event Area

##### Observer

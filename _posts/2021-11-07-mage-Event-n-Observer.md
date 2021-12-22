---
title: Magento - Event & Observer
author: Mike Mo
date: 2021-11-07
category: Magento
layout: post
---

Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/events-and-observers.html

### Configuration file
```
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Event/etc/events.xsd">
    <event name="my_module_event_after">
        <observer name="my_module_event_after_observer" instance="MyCompany\MyModule\Observer\MyEvent"/>
    </event>
</config>
```
##### Parameters
- instance
- disable
- name
  
### Custom Events
EventManager
```
use Magento\Framework\Event\ManagerInterface as EventManager;

$this->eventManager->dispatch('my_module_event_before');

// More code that sets $eventData...
$this->eventManager->dispatch('my_module_event_after', ['myEventData' => $eventData]);
```

### Event Area & File Location
|  AREA	| FILE LOCATION	| DESCRIPTION | 
|  global	| <module-dir>/etc/events.xml	| Observer will be executed in all areas: adminhtml, crontab, frontend, graphql, webapi_rest, webapi_soap. | 
|  adminhtml	| <module-dir>/etc/adminhtml/events.xml	| Observer will be executed in the adminhtml area only. | 
|  crontab	| <module-dir>/etc/crontab/events.xml	| Observer will be executed in the crontab area only. | 
|  frontend	| <module-dir>/etc/frontend/events.xml	| Observer will be executed in the frontend area only. | 
|  graphql	| <module-dir>/etc/graphql/events.xml	| Observer will be executed in the graphql area only. | 
|  webapi_rest	| <module-dir>/etc/webapi_rest/events.xml	| Observer will be executed in the webapi_rest area only. | 
|  webapi_soap	| <module-dir>/etc/webapi_soap/events.xml	| Observer will be executed in the webapi_soap area only. | 

### Observer
Class:
```
Magento\Framework\Event\ObserverInterface;
```

```
Magento\Framework\Event\ManagerInterface
```

### Best Practise

- Avoid cyclical event loops
Cyclical event loops occur when your observer calls the method of an object that dispatches an event that triggers a chain of events that ends up dispatching that same initial event that executes your observer in a recurring manner. Make sure your observer is not dispatching an event that it immediately listens to or will listen to in the chain of events that follows.


- <strong>Do not rely on invocation order</strong>
Your observer should not make assumptions about the order in which it will be invoked nor should it rely on the execution of another observer. Observers listening to the same event may be invoked in any order when that event is dispatched.


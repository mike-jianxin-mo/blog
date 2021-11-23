---
title: Magento - Event Joints
author: Mike Mo
date: 2021-11-22
category: Magento
layout: post
---

### Model
Ref: https://www.mageplaza.com/magento-2-module-development/magento-2-events.html

Event name: controller_action_predispatch
File: vendor/magento/framework/App/Action/Action.php

	$this->_eventManager->dispatch('controller_action_predispatch', $eventParameters);

Event name: controller_action_predispatch_
File: vendor/magento/framework/App/Action/Action.php

	$this->_eventManager->dispatch('controller_action_predispatch_' . $request->getRouteName(), $eventParameters);

Event name: controller_action_predispatch_
File: vendor/magento/framework/App/Action/Action.php

	$this->_eventManager->dispatch(
	    'controller_action_predispatch_' . $request->getFullActionName(),
	    $eventParameters
	);

Event name: controller_action_postdispatch_
File: vendor/magento/framework/App/Action/Action.php

	$this->_eventManager->dispatch(
	  'controller_action_postdispatch_' . $request->getFullActionName(),
	    $eventParameters
	);

Event name: controller_action_postdispatch_
File: vendor/magento/framework/App/Action/Action.php

	$this->_eventManager->dispatch(
	       'controller_action_postdispatch_' . $request->getRouteName(),
	       $eventParameters
	);

Event name: controller_action_postdispatch
File: vendor/magento/framework/App/Action/Action.php

	$this->_eventManager->dispatch('controller_action_postdispatch', $eventParameters);


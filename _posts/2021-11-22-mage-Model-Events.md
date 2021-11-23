---
title: Magento - Event Joints
author: Mike Mo
date: 2021-11-22
category: Magento
layout: post
---

### Model
Ref: https://www.mageplaza.com/magento-2-module-development/magento-2-events.html

Event name: model_load_before
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch('model_load_before', $params);

Event name: _load_before
File: vendor/magento/framework/Model/AbstractModel.php

	 $this->_eventManager->dispatch($this->_eventPrefix . '_load_before', $params);

Event name: model_load_after
File: vendor/magento/framework/Model/AbstractModel.php

	 $this->_eventManager->dispatch('model_load_after', ['object' => $this]);

Event name: _load_after
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch($this->_eventPrefix . '_load_after', $this->_getEventData());

Event name: model_save_commit_after
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch('model_save_commit_after', ['object' => $this]);

Event name: _save_commit_after
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch($this->_eventPrefix . '_save_commit_after', $this->_getEventData());

Event name: model_save_before
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch('model_save_before', ['object' => $this]);

Event name: _save_before
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch($this->_eventPrefix . '_save_before', $this->_getEventData());

Event name: model_save_after
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch('model_save_after', ['object' => $this]);

Event name: clean_cache_by_tags
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch('clean_cache_by_tags', ['object' => $this]);

Event name: _save_after
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch($this->_eventPrefix . '_save_after', $this->_getEventData());

Event name: model_delete_before
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch('model_delete_before', ['object' => $this]);

Event name: _delete_before
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch($this->_eventPrefix . '_delete_before', $this->_getEventData());

Event name: model_delete_after
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch('model_delete_after', ['object' => $this]);

Event name: clean_cache_by_tags
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch('clean_cache_by_tags', ['object' => $this]);

Event name: _delete_after
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch($this->_eventPrefix . '_delete_after', $this->_getEventData());

Event name: model_delete_commit_after
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch('model_delete_commit_after', ['object' => $this]);

Event name: _delete_commit_after
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch($this->_eventPrefix . '_delete_commit_after', $this->_getEventData());

Event name: _clear
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch($this->_eventPrefix . '_clear', $this->_getEventData());

Event name: _clear
File: vendor/magento/framework/Model/AbstractModel.php

	$this->_eventManager->dispatch($this->_eventPrefix . '_clear', $this->_getEventData());



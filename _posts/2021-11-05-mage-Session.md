---
title: Magento - Session operations
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

### Session models

##### Session Class
Ref: https://magento.stackexchange.com/questions/94265/how-to-set-retrieve-and-unset-session-variables-in-magento-2

```
1)  \Magento\Catalog\Model\Session //vendor/magento/module-catalog/Model/Session.php

2) \Magento\Newsletter\Model\Session //vendor/magento/module-newsletter/Model/Session.php

3) \Magento\Persistent\Model\Session //vendor/magento/module-persistent/Model/Session.php

4) \Magento\Customer\Model\Session //vendor/magento/module-customer/Model/Session.php

5) \Magento\Backend\Model\Session //vendor/magento/module-backend/Model/Session.php

6) \Magento\Checkout\Model\Session //vendor/magento/module-checkout/Model/Session.php
```

##### Data Persistor
Ref: https://magento.stackexchange.com/questions/214379/what-is-data-persistor

\Magento\Framework\App\Request\DataPersistor

SessionManagerInterface

---
title: Magento - Controller's Result Page
author: Mike Mo
date: 2021-11-11
category: Magento
layout: post
---

### Controller result page

##### Template

Change the root.template file of the controller result page!

Ref: https://magento.stackexchange.com/questions/206602/how-to-override-root-phtml-template-in-my-custom-theme-for-product-view-page

di.xml
```
<type name="Magento\Framework\View\Result\Page">
    <arguments>
        <argument name="layoutReaderPool" xsi:type="object">pageConfigRenderPool</argument>
        <argument name="generatorPool" xsi:type="object">pageLayoutGeneratorPool</argument>
        <argument name="template" xsi:type="string">Magento_Theme::root.phtml</argument>
    </arguments>
</type>
```

File: 
<strong>./vendor/magento/module-theme/view/base/templates/root.phtml</strong>

```
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */
?>
<!doctype html>
<html <?= /* @noEscape */ $htmlAttributes ?>>
    <head <?= /* @noEscape */ $headAttributes ?>>
        <?= /* @noEscape */ $requireJs ?>
        <?= /* @noEscape */ $headContent ?>
        <?= /* @noEscape */ $headAdditional ?>
    </head>
    <body data-container="body"
          data-mage-init='{"loaderAjax": {}, "loader": { "icon": "<?= /* @noEscape */ $loaderIcon ?>"}}'
        <?= /* @noEscape */ $bodyAttributes ?>>
        <?= /* @noEscape */ $layoutContent ?>
    </body>
</html>
```

##### Factory
Ref: https://magento.stackexchange.com/questions/240856/what-is-the-use-of-pagefactory-in-magento-2

\Magento\Framework\View\Result\Page - actually renders HTML \Magento\Framework\Controller\Result\Redirect - redirects to another page \Magento\Framework\Controller\Result\Forward - forwards to another action (internal redirect) \Magento\Framework\Controller\Result\Json - returns a JSON object. \Magento\Framework\Controller\Result\Raw - returns whatever you tell it to return (string).


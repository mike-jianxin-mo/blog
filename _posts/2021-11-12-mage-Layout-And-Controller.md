---
title: Magento - UI: The Layout & Controller
author: Mike Mo
date: 2021-11-12
category: Magento
layout: post
---

### Origin: A return type of the controller object

- <strong>\Magento\Framework\View\Result\Page - actually renders HTML </strong>
- \Magento\Framework\Controller\Result\Redirect - redirects to another page
- \Magento\Framework\Controller\Result\Forward - forwards to another action (internal redirect) 
- \Magento\Framework\Controller\Result\Json - returns a JSON object.
- \Magento\Framework\Controller\Result\Raw - returns whatever you tell it to return (string).

Ref: https://magento.stackexchange.com/questions/240856/what-is-the-use-of-pagefactory-in-magento-2

### The Root template
- Definition Location
  - app/etc/di.xml
  - magnto2-base/app/etc/di.xml
  - module-backend/etc/adminhmtl/di.xml
- Links with the Result Page
  ```
    <type name="Magento\Framework\View\Result\Page">
        <arguments>
            <argument name="layoutReaderPool" xsi:type="object">pageConfigRenderPool</argument>
            <argument name="generatorPool" xsi:type="object">pageLayoutGeneratorPool</argument>
            <argument name="template" xsi:type="string">Magento_Theme::root.phtml</argument>
        </arguments>
    </type>
  ```
  - Content
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

### The starting points of the page layout
  I grep the container named root in the layout files. I found many results, and I think this is the root layout settings for the pages. Because in these files there is no referenceContainer settings.
  - Page Layout
    The layout files according to the controler/routes.
  ```
  grep -r 'container name="root"' .
./app/design/adminhtml/Magento/backend/IWD_OrderManager/layout/iwdordermanager_warehouses_product_grid.xml:    <container name="root" label="Root">
./app/code/Plumrocket/Newsletterpopup/view/frontend/layout/prnewsletterpopup_index_snapshot.xml:        <container name="root">
./app/code/Ves/Blog/view/adminhtml/layout/vesblog_category_posts.xml:    <container name="root" label="Root">
./app/code/Ves/Blog/view/adminhtml/layout/vesblog_category_postgrid.xml:    <container name="root" label="Root">
./app/code/Ves/Blog/view/adminhtml/layout/vesblog_post_relatedproducts.xml:    <container name="root" label="Root">
./app/code/Ves/Blog/view/adminhtml/layout/vesblog_post_comments.xml:    <container name="root" label="Root">
./app/code/Ves/Blog/view/adminhtml/layout/vesblog_post_related.xml:    <container name="root" label="Root">
./app/code/Ves/Blog/view/adminhtml/layout/vesblog_post_relatedproductsgrid.xml:    <container name="root" label="Root">
./app/code/Ves/Blog/view/adminhtml/layout/vesblog_post_commentgrid.xml:    <container name="root" label="Root">
./app/code/Ves/Blog/view/adminhtml/layout/vesblog_post_relatedgrid.xml:    <container name="root" label="Root">
./app/code/Xtento/TrackingImport/view/adminhtml/layout/xtento_trackingimport_source_grid.xml:    <container name="root" label="Root">
./app/code/Xtento/TrackingImport/view/adminhtml/layout/xtento_trackingimport_profile_source.xml:    <container name="root" label="Root">
./app/code/Xtento/TrackingImport/view/adminhtml/layout/xtento_trackingimport_profile_log.xml:    <container name="root" label="Root">
./app/code/Xtento/TrackingImport/view/adminhtml/layout/xtento_trackingimport_log_grid.xml:    <container name="root" label="Root">
./app/code/Mageplaza/CustomForm/view/adminhtml/layout/mpcustomform_form_responsesdetail.xml:    <container name="root" label="Root">
./app/code/Magedelight/Storepickup/view/adminhtml/layout/storepickupadmin_tag_taggrid.xml:<container name="root" label="Root">
./app/code/Magedelight/Storepickup/view/adminhtml/layout/storepickupadmin_tag_taggrid.xml:<container name="root" label="Root">
./app/code/Magedelight/Storepickup/view/adminhtml/layout/storepickupadmin_storeinfo_products.xml:    <container name="root" label="Root">
./app/code/Magedelight/Storepickup/view/adminhtml/layout/storepickupadmin_tag_storegrid.xml:<container name="root" label="Root">
./app/code/Magedelight/Storepickup/view/adminhtml/layout/storepickupadmin_tag_storegrid.xml:<container name="root" label="Root">
./app/code/Amasty/ShopbyBase/view/adminhtml/layout/amshopby_option_option_settings.xml:    <container name="root">
./app/code/Amasty/Feed/view/adminhtml/layout/amfeed_category_grid.xml:    <container name="root">
./app/code/Amasty/ShopbyPage/view/adminhtml/layout/amasty_shopbypage_page_selection.xml:    <container name="root" label="Root">
./dev/tests/integration/testsuite/Magento/Framework/View/_files/layout_directives_test/sort_after_previous.xml:    <container name="root" label="Root">
./dev/tests/integration/testsuite/Magento/Framework/View/_files/layout_directives_test/sort_before_after.xml:    <container name="root" label="Root">
./dev/tests/integration/testsuite/Magento/Framework/View/_files/layout_directives_test/sort_after_after.xml:    <container name="root" label="Root">
./dev/tests/integration/testsuite/Magento/Framework/View/_files/layout_directives_test/sort_before_before.xml:    <container name="root" label="Root">
./vendor/magento/module-theme/view/adminhtml/layout/adminhtml_system_design_theme_grid.xml:    <container name="root">
./vendor/magento/module-theme/view/adminhtml/layout/adminhtml_system_design_wysiwyg_files_contents.xml:    <container name="root">
./vendor/magento/module-theme/view/adminhtml/page_layout/admin-1column.xml:    <container name="root">
./vendor/magento/module-theme/view/adminhtml/page_layout/admin-2columns-left.xml:    <container name="root">
./vendor/magento/module-theme/view/adminhtml/page_layout/admin-empty.xml:    <container name="root">
./vendor/magento/module-theme/view/adminhtml/page_layout/admin-login.xml:    <container name="root" htmlTag="section" htmlClass="page-wrapper">
./vendor/magento/module-theme/view/base/page_layout/empty.xml:    <container name="root">
./vendor/magento/module-review/view/frontend/layout/review_product_listajax.xml:    <container name="root">
./vendor/magento/module-review/view/adminhtml/layout/review_product_reviews_grid.xml:    <container name="root" label="Root">
./vendor/magento/module-paypal/view/frontend/layout/paypal_payflow_cancelpayment.xml:    <container name="root">
./vendor/magento/module-paypal/view/frontend/layout/paypal_payflowadvanced_returnurl.xml:    <container name="root">
./vendor/magento/module-paypal/view/frontend/layout/paypal_payflow_form.xml:    <container name="root">
... ...
  ```

### Layout handles - The basic sections of pages
A layout handle is a uniquely identified set of layout instructions that serves as a name of a layout file.

There are three kinds of layout handles:

- page-type layout handles – Synonyms of the page type identifiers. Correspond to “full action names” of controller actions, for example, catalog_product_view.
- page layout handles – Identifiers of specific pages. Correspond to controller actions with parameters that identify specific pages, for example, catalog_product_view_type_simple_id_128 or for a CMS page, cms_page_view_id_home.xml.
- arbitrary handles - Do not correspond to any page type, but other handles use them by including.


### Organiser of the Layout Handlers
- <strong>update</strong>
  The specified handle is “included” and executed recursively.
  This is the key to combine all parts of the layout files together.

### The Organised Examples of the main layouts
- Definition
  layout\ <strong>layouts.xml</strong>
- Relations:
  <strong> empty.xml --> 1column.xml --> 2clumns-left.xml --> 2column-right.xml </strong>
- Layout details:
  - empty.xml
    ./vendor/magento/module-theme/view/base/page_layout/empty.xml
    ```
      <layout xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_layout.xsd">
          <container name="root">
              <container name="after.body.start" as="after.body.start" before="-" label="Page Top"/>
              <container name="page.wrapper" as="page_wrapper" htmlTag="div" htmlClass="page-wrapper">
                  <container name="global.notices" as="global_notices" before="-"/>
                  <container name="main.content" htmlTag="main" htmlId="maincontent" htmlClass="page-main">
                      <container name="columns.top" label="Before Main Columns"/>
                      <container name="columns" htmlTag="div" htmlClass="columns">
                          <container name="main" label="Main Content Container" htmlTag="div" htmlClass="column main"/>
                      </container>
                  </container>
                  <container name="page.bottom.container" as="page_bottom_container" label="Before Page Footer Container" after="main.content" htmlTag="div" htmlClass="page-bottom"/>
                  <container name="before.body.end" as="before_body_end" after="-" label="Page Bottom"/>
              </container>
          </container>
      </layout>
    ```

  - 1column.xml
    The 1column layout is based on the empty layout.
    ./vendor/magento/module-theme/view/frontend/page_layout/1column.xml
    ```
    <layout xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_layout.xsd">
      <update handle="empty"/>
      <referenceContainer name="page.wrapper">
          <container name="header.container" as="header_container" label="Page Header Container" htmlTag="header" htmlClass="page-header" before="main.content"/>
          <container name="page.top" as="page_top" label="After Page Header" after="header.container"/>
          <container name="footer-container" as="footer" before="before.body.end" label="Page Footer Container" htmlTag="footer" htmlClass="page-footer"/>
      </referenceContainer>
    </layout>
    ```
  - 2columns-left.xml
    The 2columns-left layout is based on the 1column layout.
    ./vendor/magento/module-theme/view/frontend/page_layout/2columns-left.xml
    ```
    <layout xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_layout.xsd">
      <update handle="1column"/>
      <referenceContainer name="columns">
          <container name="div.sidebar.main" htmlTag="div" htmlClass="sidebar sidebar-main" after="main">
              <container name="sidebar.main" as="sidebar_main" label="Sidebar Main"/>
          </container>
          <container name="div.sidebar.additional" htmlTag="div" htmlClass="sidebar sidebar-additional" after="div.sidebar.main">
              <container name="sidebar.additional" as="sidebar_additional" label="Sidebar Additional"/>
          </container>
      </referenceContainer>
    </layout>
    ```
    
  - 2columns-right.xml
    ./vendor/magento/module-theme/view/frontend/page_layout/2columns-right.xml
    ```
    <layout xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_layout.xsd">
      <update handle="2columns-left"/>
    </layout>
    ```
    

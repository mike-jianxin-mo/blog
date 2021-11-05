---
title: Magento - Web API Alias
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

### Web API

###### Alias of the webapi

You can configure REST endpoints in your module to use custom routes (aliases) for URLs instead of the default URLs. For example, you can define the alias createWidget to represent POST V1/widgets. However, you cannot create an alias for a route that contains one or more variables, such as PUT V1/widgets/:widgetId.

To define custom routes, create an etc/webapi_async.xml file in your module that contains the following structure:

Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/webapi/custom-routes.html

<strong>etc/webapi_async.xml</strong>

```
<services xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_WebapiAsync:etc/webapi_async.xsd">
    <route url="V1/widgets" method="POST" alias="createWidget" />
    <route url="async/bulk/V1/widget" method="PUT" alias="asyncBulkUpdateWidgets"/>
    .........
</services>

```
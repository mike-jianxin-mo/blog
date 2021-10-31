---
title: Magento 2 - Rewrite controler with route
author: Mike Mo
date: 2021-10-31
category: Magento
layout: post
---

#### Use Route to rewrite controller

Magento provide the attribute before/after to config the module sort order which define what module controller will be find first. This is the logic for the controller rewrite.

For example, if we want to rewrite the controller customer/account/login, we will define more route in the routes.xml like this:

<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/etc/routes.xsd">
   <!--Use router 'standard' for frontend route-->
   <router id="standard">
       <route id="customer">
           <module name="Vendor_Module" before="Magento_Customer" />
       </route>
   </router>
</config>

Add the controller file: app/code/Vendor/Module/Controller/Account/Login.php

So the frontController will find the Login action in our module first, if it’s found, it will run, and the Login action of Magento_Customer will not be run. Then we are successful rewrite a controller.

Ref: https://www.mageplaza.com/magento-2-module-development/magento-2-routing.html

###### Use route to rewrite controller

In this path, we will see how to rewrite a controller with router. As above path, you can see each route will have an id attribute to identify. So what happen if we define 2 route with the same id attribute?

The answer is that the controller action will be find in both of that modules. Magento system provide the attribute before/after to config the module sort order which define what module controller will be find first. This’s the logic for the controller rewrite.

For example, if we want to rewrite the controller customer/account/login, we will define more route in the route.xml like this:

File: app/code/Mageplaza/HelloWorld/etc/frontend/routes.xml

<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/etc/routes.xsd">
   <!--Use router 'standard' for frontend route-->
   <router id="standard">
        <!--Define a custom route with id and frontName-->
        <route frontName="helloworld" id="helloworld">
            <!--The module which this route match to-->
            <module name="Mageplaza_HelloWorld"/>
        </route>
       <route id="customer">
           <module name="Mageplaza_HelloWorld" before="Magento_Customer" />
       </route>
   </router>
</config>
And the controller file: app/code/Mageplaza/HelloWorld/Controller/Account/Login.php

So the frontController will find the Login action in our module first, if it’s found, it will run and the Login action of Magento_Customer will not be run. We are successful rewrite a controller.

You can also use this to have a second module with the same router as another module. For example, with above declare, you can use route ‘customer’ for your controller action. If you have controller ‘Blog’ and action ‘Index.php’ you can use this url:

http://example.com/customer/blog/index
If you got this error message: Exception printing is disabled by default for security reasons, this topic may help.

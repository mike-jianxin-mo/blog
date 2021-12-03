---
title: Magento - Usage Pattern
author: Mike Mo
date: 2021-11-24
category: Magento
layout: post
---

### Plugin
- Fallback of the systems
  - After plugin can be used to solve such problem.
    The VAT calculator... 

### Virtual Types + Object Pool
- Create Virtual types and inject them into an Object Pool
  The admin grid data source pool and the virtual collection objects.

### Controller Return
A page factory is used for different type of returns.

Types:

- \Magento\Framework\Controller\ResultFactory::TYPE_JSON
- \Magento\Framework\Controller\ResultFactory::TYPE_RAW
- \Magento\Framework\Controller\ResultFactory::TYPE_REDIRECT
- \Magento\Framework\Controller\ResultFactory::TYPE_FORWARD
- \Magento\Framework\Controller\ResultFactory::TYPE_LAYOUT
- \Magento\Framework\Controller\ResultFactory::TYPE_PAGE

Classes:
- JSON Result (\Magento\Framework\Controller\Result\Json) allows you to return a response in JSON format. It can be used in API or AJAX requests.
- Page Result (\Magento\Framework\View\Result\Page) is the most common type of response. By returning this object, the controller starts the standard page rendering based on the corresponding XML layout handle.
- Raw Result (\Magento\Framework\Controller\Result\Raw) is used if you want to return a string to the browser without using Magento layout and view rendering.
- Forward Result (\Magento\Framework\Controller\Result\Forward) allows to call another method/controller without changing the URL or redirecting.
- Redirect Result (\Magento\Framework\Controller\Result\Redirect) is used when a user needs to be redirected to a different URL.
- 
Notes:
- Layout and Page
The last two is to simply use xml layout handling to render the contents. The only difference is that layout will not have a default layout handle so you will need to assign layout handles and Page will assign the default and controler specific handles. As expected Page extends the Layout object since there only difference is the fact that layout assumes no layout handlers to begin with.

Ref:
- https://edmondscommerce.github.io/magento-2-controller-output-types/
- https://belvg.com/blog/controllers-routers-and-responses-in-magento-2.html

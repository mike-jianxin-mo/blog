---
title: Magento - Ajax & CSRF
author: Mike Mo
date: 2021-11-11
category: Magento
layout: post
---

### Ajax & CSRF

##### Bypass/Workaround
Ref: https://magento.stackexchange.com/questions/278749/how-to-bypass-csrf-validation-for-certain-requests

Extend core function and change the validation functions

##### Add CSRF token to Ajax header

- ###### generate the token from backend
Ref: https://stackoverflow.com/questions/45470802/how-to-pass-along-csrf-token-in-an-ajax-post-request-for-a-form


- ###### fetch token from cookie
    ```
    // add form key
    var formKey = $.cookie("form_key");
    ```
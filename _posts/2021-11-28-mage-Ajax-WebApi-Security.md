---
title: Magento - Ajax/Webapi Security
author: Mike Mo
date: 2021-11-28
category: Magento
layout: post
---

### Form key in Ajax call
Magento 2 adds the form key and the isAjax by using jQuery's beforeSend handler. to remove it override the beforeSend handler with and empty function for example. You can also put the form_key in the url to prevent csrf:
```
echo $block->getUrl('destination/path/index', ['form_key' => $block->getFormKey()]);
```

```
jQuery.ajax({
    url: destinationUrl,
    method: 'post',
    data: JSON.stringify(data),
    contentType: 'application/json; charset=UTF-8',
    showLoader: true,
    beforeSend: function(xhr){
        //Empty to remove magento's default handler
    }
}).done(function (resp) {
    //handle success scenario
}).fail(function (resp) {
    //handle failure scenario
});
```

### Ref:
https://magento.stackexchange.com/questions/120887/magento-2-automatically-appends-form-key-at-the-end-of-my-ajax-call

### Other security settings
- Maximum parameter inputs
- Maximum page size
- Default page size
Ref: https://devdocs.magento.com/guides/v2.4/get-started/api-security.html

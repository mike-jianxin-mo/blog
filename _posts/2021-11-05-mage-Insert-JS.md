---
title: Magento - Insert Js to CMS
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

### Insert Js to CMS

##### Via admin
Insert Js
```
Admin > Content > Elements > Pages > Design > Layout Update XML
```

```
<head>
    <link src="js/custom.js"/>
</head>
```

##### Via block template
```
Admin > Content > Elements > Pages > Content

{{block class="Magento\Framework\View\Element\Template"  name="test_file" template="Magento_Theme::test.phtml"}}
```
Template content
```
<script type="text/x-magento-init">
{
      ".Your_class/#Your_id": {
              "https://www.example.com/demo/pub/static/frontend/{Vendor_name}/{theme}/en_US/js/custom.js": {}
       }
}
</script>
```

##### Directly
```
<script>
    require([
        'jquery',
        'VendorName_ModuleName/js/js_file_name'
    ], function ($, script) {
        //Your code here
        //alert('Here');
    });
</script> <br/> <hr/> <br/> You can add for any CMS Pages (from admin) a template file in `Layout Update XML`

```
Or
```
var config = {
    map: {
        '*': {
            custom_js: 'VendorName_ModuleName/js/js_file_name'
        }
    }
}; In a template you can call it:

<script>
    require([
        'jquery',
        'custom_js'
    ], function ($, script) {
        //Your code here
        //alert('Here');
    });
</script> <br/>
```
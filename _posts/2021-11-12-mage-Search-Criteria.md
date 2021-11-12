---
title: Magento - Rest Search Endpoint: Search Criteria
author: Mike Mo
date: 2021-11-12
category: Magento
layout: post
---

### Search Criteria

##### Example functions

Ref: https://devdocs.magento.com/guides/v2.4/rest/performing-searches.html
The document is wrong, it uses 'searchCriteria', with this a "field error" will return.

Use <strong>'criteria' NOT 'searchCriteria'</strong>

```
function checkPostCode($) {
    var itemMessageEl = $('#postcode-popup-message');
    var form = $("#tde_express_postcode");
    var payload = {postData: getPopFormData(form)};
    if (!payload.postData.zone_name ||
        !payload.postData.postcode
    ) {
        itemMessageEl.html('<p style="color: red">Please fill in the required fields.</p>');
        return false;
    }

    // get request version from document, which is wrong!
    //  searchCriteria[filterGroups][0][filters][0][field]=updated_at&searchCriteria[filterGroups][0][filters][0][value]=2021-11-11 23:54:29&
    //  searchCriteria[filterGroups][0][filters][0][conditionType]=from&searchCriteria[filterGroups][1][filters][0][field]=updated_at&
    //  searchCriteria[filterGroups][1][filters][0][value]=2021-11-11 23:55:29&searchCriteria[filterGroups][1][filters][0][conditionType]=to&
    //  searchCriteria[currentPage]=1&searchCriteria[pageSize]=10

    var searchString =  'criteria[filterGroups][0][filters][0][field]=postcode' +
                        '&criteria[filterGroups][0][filters][0][value]=' + payload.postData.postcode +
                        '&criteria[filterGroups][0][filters][0][conditionType]=eq' +
                        '&criteria[filterGroups][1][filters][0][field]=zone_name' +
                        '&criteria[filterGroups][1][filters][0][value]=' + payload.postData.zone_name +
                        '&criteria[filterGroups][1][filters][0][conditionType]=eq' +
                        '&criteria[currentPage]=1&criteria[pageSize]=10'

    $.ajax({
        url: '/rest/V1/check_post_code?' + searchString,
        // data: JSON.stringify(searchCriteria),
        global: false,
        contentType: 'application/json',
        type: 'GET',
        async: true,
        beforeSend: function(xhr){
            //Empty to remove magento's default handler, to remove the form_key which will be appened
            // at the end of the payload.
        }
    }).done(function (response) {
        result = true;
        if (response.error) {
            itemMessageEl.html('<p style="color: red">Item not found failure.</p>');
        }else {
            // check response
            if (!response.items || response.items.length === 0) {
                itemMessageEl.html('<p style="color: red">Sorry, your area is not in the express shipping area.</p>');
            }
            itemMessageEl.html('<p style="color: green">Your address is in the Express shipping area.</p>');
        }
    }).fail(function (response) {
        itemMessageEl.html('<p style="color: red">Area not found.</p>');
    });
    return false;
}
```

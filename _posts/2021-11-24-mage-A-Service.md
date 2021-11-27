---
title: Magento - Template
author: Mike Mo
date: 2021-11-24
category: Magento
layout: post
---

### Form Validation
Ref:
- https://magento.stackexchange.com/questions/95171/magento-2-form-validation 
- https://inchoo.net/magento-2/validate-custom-form-in-magento-2/

```
<label for="email">Email:</label>
<input type="text" id="email" name="email" value=""  placeholder="Email" data-validate='{"required":true, "email":true}'/>
```

```
<label for="phone">Phone:</label>
<input type="text" id="phone" name="phone" value=""  placeholder="Phone Number" required="true"/>
```

```
<script type="text/x-magento-init">
    {
        "#nikon_corporate_request": {
            "validation": {}
        }
    }
</script>
```

### Filter/Builder
Use addFilter
```
    $this->searchCriteriaBuilder->addFilter('nikon_code', $nikonCode);

    $searchCriteria = $this->searchCriteriaBuilder->create();
    $searchResults = $this->nikonCodeRepository->getList($searchCriteria);

    return $searchResults->getItems();
```


Use addFilters
```
public function getProducts()
{
    $filters[] = $this->filterBuilder
        ->setField('sku')
        ->setConditionType('eq')
        ->setValue('something')
        ->create();
    $this->searchCriteriaBuilder->addFilters($filters);

    $searchCriteria = $this->searchCriteriaBuilder->create();
    $searchResults = $this->productRepository->getList($searchCriteria);
    return $searchResults->getItems();
}
```

### The return data structure of getList()
A item of the getList()->getItems() function.
```
{"nikon codes":"array (
  0 =>
  array (
    'id' => '1',
    'nikon_code' => '123',
    'type' => 'bag',
    'bag_number' => '1',
  ),
)"} []
```

### Redirect
```
$this->_redirect('*/*/success');
return;

$this->_redirect('*/*/index');
return;
```

### Debug
show all
```
ini_set('display_errors', 1);
ini_set('display_startup_errors', 1);
error_reporting(E_ALL);
```
show error details
```
$e->getMessage();

$e->getTraceAsString();
```
add message to log
```
\Magento\Framework\App\ObjectManager::getInstance()->get('Psr\Log\LoggerInterface')->debug(__FILE__ . ' LINE ' . __LINE__, ['nikon codes' => var_export($nikonCodes, true)]);
```

### Exception
```
throw new \Exception();
```

```
try{ 
    ... ...
} catch (\Exception $e) {
    $this->messageManager->addErrorMessage(
        __('We can\'t process your request right now.')
    );

//            $resultRedirect = $this->resultFactory->create(\Magento\Framework\Controller\ResultFactory::TYPE_REDIRECT);
//            $resultRedirect->setUrl($this->_redirect->getRefererUrl());
    $this->_redirect('*/*/index');
    return;
}
```

### Server side checking
```
    private function validatePostRequest($post) {
        $error = false;
        if (!\Zend_Validate::is(trim($post['first_name']), 'NotEmpty')) {
            $error = true;
        }
        if (!\Zend_Validate::is(trim($post['last_name']), 'NotEmpty')) {
            $error = true;
        }
        if (!\Zend_Validate::is(trim($post['nikon_code']), 'NotEmpty')) {
            $error = true;
        }
        if (!\Zend_Validate::is(trim($post['strap_option']), 'NotEmpty')) {
            $error = true;
        }
        if (!\Zend_Validate::is(trim($post['monogram_font']), 'NotEmpty')) {
            $error = true;
        }
        if (!\Zend_Validate::is(trim($post['monogram_color']), 'NotEmpty')) {
            $error = true;
        }
        if (!\Zend_Validate::is(trim($post['email']), 'EmailAddress')) {
            $error = true;
        }
        if (!\Zend_Validate::is(trim($post['phone']), 'NotEmpty')) {
            $error = true;
        }
        if (!\Zend_Validate::is(trim($post['address']), 'NotEmpty')) {
            $error = true;
        }
        if ($error) {
            throw new \Exception();
        }

        return $error;
    }
```

### Admin Grid

### Admin Form


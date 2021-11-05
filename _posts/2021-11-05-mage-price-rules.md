---
title: Magento - Custom Price Rules
author: Mike Mo
date: 2021-11-05
category: Magento
layout: post
---

##### Add a custom Condition in Admin

- Add an observer for the <strong>salesrule_rule_condition_combine</strong> event
  Ref: https://magently.com/blog/magento-2-custom-sales-rule-condition/





##### Add a custom Action in Admin
- Add an action option
  Ref: 
  - https://newbedev.com/in-magento-2-how-to-add-custom-options-in-action-apply-field-in-cart-price-rule-form-in-admin
  - https://magento.stackexchange.com/questions/284785/in-magento-2-how-to-add-custom-options-in-action-apply-field-in-cart-price-rule


- Create a new action form
  <strong>catalog_rule_form.xml</strong>
  Ref: https://stackoverflow.com/questions/58168197/magento-2-custom-action-for-catalog-rule


##### Implement the real discount functions

- The discount functions are implemented as Classes. The locations are
    ```
    Magento\SalesRule\Model\Rule\Action\Discount\ToFixed
    Magento\SalesRule\Model\Rule\Action\Discount\BuyXGetY
    Magento\SalesRule\Model\Rule\Action\Discount\ByPercent
    ```

    All these classes are implemented the AbstractDiscount interface and implement the <strong>calcualte</strong> function
    ```
    Magento\SalesRule\Model\Rule\Action\Discount\AbstractDiscount
    ```

- All these discount implement class are picked in a Factory Class from an assocated array
    Magento\SalesRule\Model\Rule\Action\Discount\CalculationFactory

    ```
    protected $classByType = [
        \Magento\SalesRule\Model\Rule::TO_PERCENT_ACTION =>
            \Magento\SalesRule\Model\Rule\Action\Discount\ToPercent::class,
        \Magento\SalesRule\Model\Rule::BY_PERCENT_ACTION =>
            \Magento\SalesRule\Model\Rule\Action\Discount\ByPercent::class,
        \Magento\SalesRule\Model\Rule::TO_FIXED_ACTION => \Magento\SalesRule\Model\Rule\Action\Discount\ToFixed::class,
        \Magento\SalesRule\Model\Rule::BY_FIXED_ACTION => \Magento\SalesRule\Model\Rule\Action\Discount\ByFixed::class,
        \Magento\SalesRule\Model\Rule::CART_FIXED_ACTION =>
            \Magento\SalesRule\Model\Rule\Action\Discount\CartFixed::class,
        \Magento\SalesRule\Model\Rule::BUY_X_GET_Y_ACTION =>
            \Magento\SalesRule\Model\Rule\Action\Discount\BuyXGetY::class,
    ];
    ```

    And a simple create function:
    ```
    public function create($type)
    {
        if (!isset($this->classByType[$type])) {
            throw new \InvalidArgumentException($type . ' is unknown type');
        }

        return $this->_objectManager->create($this->classByType[$type]);
    }
    ```

- Rules are used in the calculation of the discounts
    ```
    Magento\SalesRule\Model\Rules
    ```
    It keeps the rule settings.






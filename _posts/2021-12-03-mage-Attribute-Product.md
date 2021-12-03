---
title: Magento - Product Attribute
author: Mike Mo
date: 2021-12-03
category: Magento
layout: post
---

### Setup Parameters
Ref: https://devdocs.magento.com/videos/fundamentals/add-new-product-attribute/
For now, we’ll just quickly go through most important ones:

- group: Means that we add an attribute to the attribute group “General”, which is present in all attribute sets.
- type: varchar means that the values will be stored in the catalog_eav_varchar table.
- label: A label of the attribute (that is, how it will be rendered in the backend and on the frontend).
- <strong>source/frontend/backend</strong>: Special classes associated with the attribute:
    - source model: provides a list of options
      - Extend: ```Magento\Eav\Model\Entity\Attribute\Source\AbstractSource;```
      - Methods:
        ```
        namespace Learning\ClothingMaterial\Model\Attribute\Source;

        use Magento\Eav\Model\Entity\Attribute\Source\AbstractSource;

        class Material extends AbstractSource
        {
            /**
            * Get all options
            * @return array
            */
            public function getAllOptions()
            {
                if (!$this->_options) {
                    $this->_options = [
                        ['label' => __('Cotton'), 'value' => 'cotton'],
                        ['label' => __('Leather'), 'value' => 'leather'],
                        ['label' => __('Silk'), 'value' => 'silk'],
                        ['label' => __('Denim'), 'value' => 'denim'],
                        ['label' => __('Fur'), 'value' => 'fur'],
                        ['label' => __('Wool'), 'value' => 'wool'],
                    ];
                }
                return $this->_options;
            }
        ```

    - frontend: defines how it should be rendered on the frontend
      - Extend: ``` Magento\Eav\Model\Entity\Attribute\Frontend\AbstractFrontend```
      - Methods:
        ```
        namespace Learning\ClothingMaterial\Model\Attribute\Frontend;

        use Magento\Eav\Model\Entity\Attribute\Frontend\AbstractFrontend;
        use Magento\Framework\DataObject;

        class Material extends AbstractFrontend
        {
            public function getValue(DataObject $object)
            {
                $value = $object->getData($this->getAttribute()->getAttributeCode());
                return "<b>$value</b>";
            }
        }
        ```

    - backend: allows you to perform certain actions when an attribute is loaded or saved. In our example, it will be validation.
      - Extend: ``` Magento\Eav\Model\Entity\Attribute\Backend\AbstractBackend;```
      - Methods:
        The backend model may have <strong>validate, beforeSave, afterSave, and afterLoad methods</strong> that allow the execution of some code at the moment an attribute is saved or loaded. The backend model is what makes attribute management a really powerful method of customization.

- Global: defines the scope of its values (global, website, or store)
- visible_on_front: A flag that defines whether an attribute should be shown on the “More Information” tab on the frontend
- is_html_allowed_on_front: Defines whether an attribute value may contain HTML

### Database tables
- eav_attribute
- catalog_eav_attribute
- customer_eav_attribute
- 

### Product Attribute Option Creation
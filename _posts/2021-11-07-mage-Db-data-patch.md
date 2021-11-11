---
title: Magento - DB: Data Patch
author: Mike Mo
date: 2021-11-07
category: Magento
layout: post
---

### Data Patch
With version 2.3, aside from InstallData and UpdateData classes, Magento introduced data patches, a new way for modules to apply data changes.


##### Location
```
Setup/Patch/Data
```

##### Execution Order

-  After executing the db_schema.xml
    Magento prioritizes the declarative schema approach and executes updates from the db_schema.xml before the data and schema patches.

    Ref: 
    - https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/data-patches.html
    - https://store.magenest.com/blog/apply-data-patch-in-magento-2/

- Dependences
  Using the dependecies to replace the previous module related version control system.
    ```
    public static function getDependencies()
    {
        return [
            \SomeVendor\SomeModule\Setup\Patch\Data\SomePatch::class
        ];
    }
    ```

- Revert 
    ```
    bin/magento module:uninstall --non-composer Vendor_ModuleName

    bin/magento module:uninstall Vendor_ModuleName
    ```

##### Parent classes
    use Magento\Framework\Setup\Patch\DataPatchInterface;
    use Magento\Framework\Setup\Patch\PatchRevertableInterface;

    class DummyPatch
        implements DataPatchInterface,
        PatchRevertableInterface {...}

##### Old Way 
    PatchVersionInterface

    
  
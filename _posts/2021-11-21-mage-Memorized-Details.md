---
title: Magento - Memorized Details
author: Mike Mo
date: 2021-11-21
category: Magento
layout: post
---
### Configuration Files
[Configuration file list](2021-11-21-mage-Configuration-Files.md)

- [Controller]()
- [Controller Return]()
- [PLugin Requirements]()
- [router]()
- [area]()
- [product types]()

### UI
- root.phtml
- layouts.xml
- view/frontend/page_layout/xxx.xml


### Service Contract
- SearchCriteriaBuilder


### Data Patch
- \Magento\Framework\Setup\Patch\PatchVersionInterface
- Optionally, if you plan to enable rollback for your patch during module uninstallation, then you must implement \Magento\Framework\Setup\Patch\PatchRevertableInterface.
- A data patch is a class that contains data modification instructions. It is defined in a <Vendor>/<Module_Name>/Setup/Patch/Data/<Patch_Name>.php file and implements \Magento\Framework\Setup\Patch\DataPatchInterface.
- A schema patch contains custom schema modification instructions. These modifications can be complex. It is defined in a <Vendor>/<Module_Name>/Setup/Patch/Schema/<Patch_Name>.php file and implements \Magento\Framework\Setup\Patch\SchemaPatchInterface.
- Unlike the declarative schema approach, patches will only be applied once. A list of applied patches is stored in the patch_list database table. An unapplied patch will be applied when running the setup:upgrade from the Magento CLI.
- Magento prioritizes the declarative schema approach and executes updates from the db_schema.xml before the data and schema patches.
  
Ref:
https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/data-patches.html

### Router
Ref: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/routing.html

- Note: the route Id in routes.xml is the route name listed bellow.
frontend area routers:

- NAME	SORT ORDER	DESCRIPTION
robots	10	Matches request to the robots.txt file
urlrewrite	20	Matches requests with URL defined in the database
standard	30	The standard router
cms	60	Matches requests for CMS pages
default	100	The default router


- adminhtml area routers:

NAME	SORT ORDER	DESCRIPTION
admin	10	Matches requests in the Magento admin area
default	100	The default router for the admin area

- extend point
  ```
    \Magento\Framework\App\RouterList
  ```
  
### Command Line

extend point 
```
Magento\Framework\Console\CommandListInterface
Magento\Framework\Console\CommandList
```

### Customer Configuration Used in Form
```
used_in_forms
```
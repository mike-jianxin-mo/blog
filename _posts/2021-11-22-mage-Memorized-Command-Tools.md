---
title: Magento - Command Tools
author: Mike Mo
date: 2021-11-22
category: Magento
layout: post
---

### CI commands
- Static File Generation
  - bin/magento setup:static-content:deploy --jobs=2
    jobs:
    Enable parallel processing using the specified number of jobs. The default is 0 (do not run in parallel processes). Default value is 0.
  - Ref: https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-static-view.html


- DB schema whitelist
  - command
    ```
    php bin/magento setup:db-declaration:generate-whitelist --module-name=YourModule_Name
    ```
  - issues, such as the whitelist file doesn't generated
    https://magento.stackexchange.com/questions/255583/magento-2-is-not-generating-the-db-schema-whitelist-json-file-via-cli

    Quotes:
    Whenever the db_whitelist_schema.json file is not created automatically when running the bin/magento setup:db-declaration:generate-whitelist --module-name=Vendor_Modulename command you can safely assume there’s an error in the etc/db_schema.xml file of your module.

    Since the terminal won’t return an error msg to help you fix the issue, you can resort to the following hack to discover the missing piece in your db_schema file.
    ... ...
  
---
title: Magento 2 - Difference between _save_after and _commit_after
author: Mike Mo
date: 2021-10-17
category: Markdown
layout: post
---

#### _save_after Vs _commit_after

- The category (and all other objects) are saved inside a transaction. The event catalog_category_save_after is triggered inside the transaction. So any error that might appear in the observers of this event will trigger a rollback.
Saving happens in a MySQL transaction and the save_after event is triggered before the transaction is committed, so that you can do additional updates in the database within the same transaction.

- The event catalog_category_save_commit_after is triggered after the transaction is commit-ed. So any error inside the observers for this event will not trigger a rollback for the category save.
  The save_commit_after event is triggered after the transaction has been committed, i.e. when the changes were written to the database.

- Also, on save_commit_after, the _hasDataChanges property already has been reset to false, so your check would not work. On the other hand, if there were no changes, both events would not even be triggered, because Mage_Core_Model_Abstract::save() does nothing if there were no data changes:

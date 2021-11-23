---
title: Magento - Design Pattern
author: Mike Mo
date: 2021-11-22
category: Magento
layout: post
---

### Event-Observer Pattern
There two types of events triggerred by system.
One is the system events, the other is the model specific events.

<strong> Eg. Model Save</strong>
- System events
  - model_save_after
  - model_save_commit_after
  - model_save_before
- Model specific events
  - < eventPrefix >_save_after
  - < eventPrefix >_save_commit_after
  - < eventPrefix >_save_before
  
### Object Pool Pattern

### Modifier


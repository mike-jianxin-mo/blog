---
title: Magento - Exame Questions
author: Mike Mo
date: 2021-12-21
category: Magento
layout: post
---

I passed the Expert certification exame yesterday, now I wrote down some questions that I encounter during the test.

### Command
- How to upgrade a magento version. Plz show the command line list.
  - compose command & upgrade command
- How to get varnish settings via command line
  
### Attribute
- How to create an attribute ONLY for bundle product
  - specify in setup script, with a bundle limit?
  - by backend mode?
- How to make a custom attribute editable in backend
  - System or Not
  - Backend model
  - use_in_form

### Price
- How to calculate the price of a complicated product settings, when adding it to cart.
  - base price: 200
  - special price: 210
  - tier price: 3 for 315
  - catalog price rule: 20% off
- What is the final price
  
### Checkout
- Add an attribute to quote
  - in the request_option_info 
  - additional field

### Admin Form
- Find out an issue with a field settings 
  - the data provider
  - or missing the field in the data API interfadce

### UI
- The template & instances relationship in <strong>layout</strong>.xml
  - multi instances to one template?
  - multi instances to multi templates?
  - ... ...
- Cache in the frontend with sections.xml
  - keep data in the fontend local storage, to avoid useless request.

### Product Type
- Choose product type
  - color, size, number can be customise
    - grouped product?
    - bundle product?

### Category
- The filter of a category is missing, possible reasons
  - filter settings 
  - including the product of child category
  - does not have products with filter attribute
  
### Router
- special URL structure
- parent class RouterList

### Event
- limit of the control in controller when adding an item to cart.

### Basic Pricipal
- The order of preference among modules.

### Payment
- What is Vault?
  
### Cache
- Cachable flag
  
### account section
- Add a new account link
  
### Layout handler
- Which layout handler will be applied
  

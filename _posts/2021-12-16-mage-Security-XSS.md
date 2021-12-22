---
title: Magento - Security XSS
author: Mike Mo
date: 2021-12-16
category: Magento
layout: post
---

### XSS
Cross-site scripting, or XSS, is a security vulnerability that can be found in web applications. This vulnerability allows attackers to inject malicious code/styles into a web page viewed by users. Magento extension developers should be aware of these vulnerabilities to avoid introducing them in their code.

### Types 
There are three main types of XSS vulnerabilities:

- Persisted XSS - In this type of vulnerability, the source of unvalidated data comes from the database or Backend permanent store.
- Reflected (non-persistent) XSS - This type of vulnerability occurs when data provided by a web client is used immediately by server-side scripts to parse and display a page to a user without properly sanitizing the request.
- DOM XSS - For this vulnerability, the malicious data does not touch the web server. Rather, it is being reflected by the JavaScript code, fully on the client side.

### Functions

##### escapeHtml

##### escapeJs
  - Case: All JavaScript inside attributes must be escaped by escapeJs before escapeHtmlAttr:

    Escaper method: escapeJS
    ```
    <div
        onclick="<?= $escaper->escapeHtmlAttr('handler("' . $escaper->escapeJs($aString) . '", ' . $escaper->escapeJs($aVar) .')') ?>">
        My DIV
    </div>
    ```
  - Case: JavaScript string that must not contain JS/HTML

    Escaper method: escapeJS
    ```
    <script>
        let phrase = "Hi, my name is <?= $escaper->escapeJs($myName) ?>";
        //Do not use HTMl context methods like escapeUrl
        let redirectUrl = "<?= $escaper->escapeJs($myUrl) ?>";
        location.href = redirectUrl;
    </script>
    ```

  - Case: JavaScript variable that must not contain JS/HTML

    Escaper method: escapeJS
    ```
    <script>
        let <?= $escaper->escapeJs($dynamicVariable) ?> = <?= $myJson ?>;
        settings.<?= $escaper->escapeJs($myProperty) ?> = true;
    </script>
    ```

### Ref:
https://devdocs.magento.com/guides/v2.4/extension-dev-guide/xss-protection.html

---
layout: default
title: SuiteCRM Campaigns Module - Description In-Line Edit Issue
description: About 99point99 CRM
keywords: Suitecrm7, Suitecrm8, Suitecrm, Suitecrm campaign description inline edit, suitecrm campaign description not editable, suitecrm campaign module error
---
# Fixing Description Field In-line Edit Issue in the Campaigns Module of SuiteCRM

When working with the Campaigns module in SuiteCRM, you may encounter some challenges while customizing or extending its functionality. In this post, I’ll walk you through two specific issues I resolved, along with the changes that helped me fix them. These solutions will save you time and effort if you’re tackling similar problems.

Issue 1: Making the Description Field Editable

The description field ("content" for the Campaigns module) was not displaying the pencil icon for inline editing. To make this field editable, I modified the vardefs.php file located at:

**modules/Campaigns/vardefs.php**

## Solution

Add the 'inline_edit' => true parameter to the definition of the content field. The updated configuration looks like this:
```php
'content' => array(
    'name' => 'content',
    'vname' => 'LBL_CAMPAIGN_CONTENT',
    'type' => 'text',
    'comment' => 'The campaign description',
    'inline_edit' => true,
),
```
Once this change is saved, the pencil icon for inline editing will appear for the description field in the Campaigns module.

Issue 2: Resolving the 'setSelectionRange is not a function' Error

While working with the Campaigns module, you might encounter the following JavaScript error:

setSelectionRange is not a function

Identifying the Cause

The root cause of this error is the id="content" attribute. This ID is used by multiple HTML tags, creating conflicts. Specifically, the issue arises in the getInputValue function, which attempts to retrieve the value of the content field.

Solution

To resolve this, I updated the getInputValue function (lines 444–45) to explicitly look for the textarea element within the EditView form. The modified code is as follows:
```php
default:
    if ($('#EditView').find("#" + field).val().length > 0) {
        return $('#EditView').find("#" + field).val();
    }
```
This change ensures that the content field is correctly identified and processed within the context of the EditView form, eliminating the error.

Additionally, I commented out the problematic code at line 183 to prevent further conflicts. Ensure that these updates do not interfere with other functionality in the module.

Screenshots/References

Making the Description Field Editable

File: modules/Campaigns/vardefs.php

Key Change: 'inline_edit' => true

Fixing the 'setSelectionRange is not a function' Error

File: include/InlineEditing/inlineEditing.js

Key Change: Use $('#EditView').find("#" + field) to fetch the textarea element.

## Conclusion

These changes resolved the issues and improved the usability of the Campaigns module in SuiteCRM. Whether you're customizing SuiteCRM for your business needs or working on a client project, these steps will help streamline your workflow and eliminate common errors.

If you encounter any additional issues, feel free to share them in the comments below!

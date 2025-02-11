---
title: Custom Form Validation | Commerce Frontend Development
description: View code samples for creating custom form validations for Adobe Commerce and Magento Open Source themes.
contributor_name: Atwix
contributor_link: https://www.atwix.com/
---

# Custom form validation

This tutorial shows you how to create custom form validations, using the `mage/validation` library, before submitting it to the server.
This allows the customer to enforce data validation rules before submission, which improves the user experience and user interface accessibility.

## Initiating validation

There are several ways to initiate form validation as described in [Initializing JavaScript](https://devdocs.magento.com/guides/v2.4/javascript-dev-guide/javascript/js_init.html) topic.

### Using the `data-mage-init` attribute

```html
<form id="my-form" data-mage-init='{"validation": {}}'>
    ...
</form>
```

### Using the `text/x-magento-init` script type tag

```html
<script type="text/x-magento-init">
    {
        "#my-form": {
            "validation": {}
        }
    }
</script>
```

## Form validation rules

All available validation rules may be found in [validation/rules.js](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Ui/view/base/web/js/lib/validation/rules.js).

Additionally, you may also use any available [jQuery validation rules](https://jqueryvalidation.org/documentation/#link-list-of-built-in-validation-methods).

## Defining validation rules

There are couple of ways to define validation rules for a form field.

### As a `data-validate` attribute

```html
<input id="field-1" ... data-validate='{"required":true}'/>
```

### As a `data-validate` attribute with arguments

```html
<input id="field-1" ... data-validate='{"required":true, "minlength":10}'/>
```

### As an attribute

```html
<input id="field-1" ... required="true"/>
```

### As an attribute with arguments

```html
<input id="field-1" ... required="true" minlength="15"/>
```

### As a class name

```html
<input id="field-1" ... class="input-text required-entry"/>
```

### As a class name with arguments

```html
<input id="field-1" ... class="input-text required-entry" minlength="15"/>
```

### Using `data-mage-init`

```html
<form ... data-mage-init='{"validation": {"rules": {"field-1": {"required":true}}}}'>
    ...
</form>
```

### Using `data-mage-init` with arguments

```html
<form ... data-mage-init='{"validation": {"rules": {"field-1": {"required":true, "minlength":20}}}}'>
    ...
</form>
```

## Examples

### Adding the validation for a form

Here are examples of all available ways of validating the form fields.

```html
<form class="form" id="my-form" method="post" data-mage-init='{"validation":{"rules": {"field-4": {"required":true}}}}'>
    <fieldset class="fieldset">
        <div class="field name required">
            <label class="label" for="field-1"><span>Field 1 (using data-validate)</span></label>
            <div class="control">
                <input name="field-1" id="field-1" title="Field 1" value=""  class="input-text" type="text" data-validate='{"required":true, "url": true}'/>
            </div>
        </div>
        <div class="field name required">
            <label class="label" for="field-2"><span>Field 2 (using attribute)</span></label>
            <div class="control">
                <input name="field-2" id="field-2" title="Field 2" value="" class="input-text" type="text" required="true"/>
            </div>
        </div>
        <div class="field name required">
            <label class="label" for="field-3"><span>Field 3 (using classname)</span></label>
            <div class="control">
                <input name="field-3" id="field-3" title="Field 3" value="" type="text" class="input-text required-entry"/>
            </div>
        </div>
        <div class="field name required">
            <label class="label" for="field-4"><span>Field 4 (using data-mage-init)</span></label>
            <div class="control">
                <input name="field-4" id="field-4" title="Field 4" value="" class="input-text" type="text"/>
            </div>
        </div>
    </fieldset>
    <div class="actions-toolbar">
        <div class="primary">
            <button type="submit" title="Submit" class="action submit primary">
                <span>Submit</span>
            </button>
        </div>
    </div>
</form>
```

### Result

As a result, the form gets validated before sending data to the server for processing.

![Validated Form Example](../../_images/frontend/form-validation-result.png)

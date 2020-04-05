---
description: The domain configuration is the basis for creating the domain artifacts
---

# Configuring the domain

Within this folder `src/domains/General/Category` created previously \(see [Domains](../como-utilizar/domain.md)\) we will create the `settings.js` of the`Category`entity. The final path to this file will then be `src/domains/General/Category/settings.js`. [Settings File](../como-utilizar/settings.md) are documents that aggregate basic domain configuration properties.

Within this file we will export the 3 consts commonly used by it: `path`, `domain` and `resource`.

{% code title="src/domains/General/Category/settings.js" %}
```javascript
/**
 * @type {string}
 */
export const path = '/dashboard/general/category'

/**
 * @type {string}
 */
export const domain = 'general.category'

/**
 * @type {string}
 */
export const resource = '/general/category'
```
{% endcode %}

In [`path`](../como-utilizar/settings.md#path) we will inform the base URL of the domain screens that we are configuring, to see more about it check the [Settings](../como-utilizar/settings.md#path) page.

The [`domain`](../como-utilizar/settings.md#domain)property, in turn, has the value `general.category` because the path to the domain is `src/domains/General/Category` and it will be used to recover some resources needed in the construction of the screens.

Finally, in[`resource`](../como-utilizar/settings.md#resource), the value`/general/category` was used to compose the requests that will be made to the APIs used.

{% page-ref page="criando-o-service.md" %}


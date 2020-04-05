---
description: >-
  Front-end applications needing to communicate with services that deliver data
  and generally these services use HTTP
---

# Preparing API access

Following our example, let's create a folder called`Schema`inside`src/domains/General/Category`. Within this folder, create a file called`CategoryService.js`, with a`src/domains/General/Category/Schema/CategoryService.js` path at the end.

{% hint style="info" %}
These paths may vary according to the needs of each one and are here only as a suggestion. With a little experience it is possible to understand what is being done and use it as you see fit
{% endhint %}

The content of this document will be a class similar to the excerpt below. When extending the`Rest`class, the`CategoryService`class inherits all of its behavior. These behaviors include methods that create, read, update and delete resources from the`Category`entity.

{% code title="CategoryService.js" %}
```javascript
import Rest from 'src/app/Services/Rest'
import { resource } from 'src/domains/General/Category/settings'

/**
 * @class {CategoryService}
 */
export default class CategoryService extends Rest {
  /**
   * @type {string}
   */
  resource = resource
}
```
{% endcode %}

Note the use of the`resource`property that is imported from settings.js. To know more details about [`Services`](../como-utilizar/service.md)within the project visit this [page](../como-utilizar/service.md).

{% hint style="warning" %}
There is no class to consume resources using [`GraphQL`](https://graphql.org)`,`but the logic is basically the same and with some knowledge of JavaScript it is possible to create an abstraction for this type of service as well.
{% endhint %}

This class will be used next to provide access to the entity's endpoints, let's move on to the next step.

{% page-ref page="definindo-o-schema.md" %}


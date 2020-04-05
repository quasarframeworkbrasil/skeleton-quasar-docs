---
description: >-
  Schemas are grouping of resources that will be used to provide behaviors and
  states for business rules
---

# Defining the schema

## Creating the Schema

To create a`schema`for the`Category`entity, we will create a`CategorySchema.js` file within the domain's`Schema`folder \(`src/domains/General/Category/Schema/CategorySchema.js`\) This file should extend the`Schema`class. The initial result will be a document like the one below.

{% code title="src/domains/General/Category/Schema/CategorySchema.js" %}
```javascript
import Schema from 'src/app/Agnostic/Schema'

/**
 * @class {CategorySchema}
 */
export default class CategorySchema extends Schema {
  construct () {
  }
}
```
{% endcode %}

## Importing resources

This definition is the most basic that we can do for this class because the`construct`method must be implemented even in this first version. In addition to this method, we will make some more configurations, informing the class structure the properties: `domain`, `path` and `service`.

{% code title="src/domains/General/Category/Schema/CategorySchema.js" %}
```javascript
import Schema from 'src/app/Agnostic/Schema'
import Service from 'src/domains/General/Category/Schema/CategoryService'
import { path, domain } from 'src/domains/General/Category/settings'

/**
 * @class {CategorySchema}
 */
export default class CategorySchema extends Schema {
  /**
   * @type {string}
   */
  static domain = domain

  /**
   * @type {string}
   */
  static path = path

  /**
   * @type {Rest}
   */
  service = Service

  /**
   * Configure schema
   */
  construct () {
  }
}
```
{% endcode %}

The static domain and path properties are imported from the`settings.js` that we defined in [Configuring the domain](configurando-o-dominio.md)  and the`service`property is the`CategoryService.js` file that we created in [Preparing access to the API](criando-o-service.md).

## Creating the`name`field

With our schema started we will configure the fields that will be used by the entity. For this we will use the`addField`method that must be called within the`construct`.

{% code title="src/domains/General/Category/Schema/CategorySchema.js" %}
```javascript
// ...

/**
 * @class {CategorySchema}
 */
export default class CategorySchema extends Schema {
  // ...

  /**
   * Configure schema
   */
  construct () {
    this.addField('name')
  }
}
```
{% endcode %}

In the code snippet above we declare that our`schema`will work with the`name`field. By default, a created field is not displayed in the`table`and is displayed on the`form`with a width that occupies 100% of the line in a text field. The`primaryKey`field is loaded implicitly in all children of`Schema`. Therefore, our class is mapping two fields: `id` and `name`. Later on we will see the settings of the fields and everything we can do with them, in addition to other configurable features in our[`schema`](../como-utilizar/schema.md).

In the next step we will see how to add some routes so that we can see our screen being rendered.

{% page-ref page="criando-as-views.md" %}


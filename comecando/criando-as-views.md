---
description: >-
  With the schema and settings defined we can proceed to the next step which is
  to create the views responsible for rendering the screens
---

# Creating the views

The standard presentation components are relatively simple and do not need a very extensive implementation.

The suggestion of the structure is to place the views of the`Category`entity of the`General`domain within the`Dashboard`module inside a folder with the path `src/views/dashboard/general/category`. After creating this directory we can create the two views that are necessary to maintain the operations of creating, viewing, editing, deleting and searching the records of this entity: `CategoryForm.vue` and `CategoryTable.vue`. Below we can see examples of implementation of the two.

{% code title="src/views/dashboard/general/category/CategoryForm.vue" %}
```markup
<template>
  <SchemaForm v-bind="bind" />
</template>

<script type="text/javascript">
import View from 'src/app/Agnostic/Adapters/View'
import Schema from 'src/domains/General/Category/Schema/CategorySchema'

/**
 * @typedef {CategoryForm}
 */
export default {
  /**
   * extend adapter to load schema components with schemas
   */
  extends: View,
  /**
   * @type {string}
   */
  name: 'CategoryForm',
  /**
   * schema that has the entity's definitions and business rules
   */
  schema: Schema
}
</script>

<style
  lang="stylus"
  rel="stylesheet/stylus"
>
</style>
```
{% endcode %}

This`form`will be responsible for defining the display of the entity's data. It is possible to notice that the `Category schema`is imported to configure the component.

{% code title="src/views/dashboard/general/category/CategoryTable.vue" %}
```markup
<template>
  <SchemaTable v-bind="bind" />
</template>

<script type="text/javascript">
import View from 'src/app/Agnostic/Adapters/View'
import Schema from 'src/domains/General/Category/Schema/CategorySchema'

/**
 * @typedef {CategoryTable}
 */
export default {
  /**
   * extend adapter to load schema components with schemas
   */
  extends: View,
  /**
   * @type {string}
   */
  name: 'CategoryTable',
  /**
   * schema that has the entity's definitions and business rules
   */
  schema: Schema
}
</script>

<style
  lang="stylus"
  rel="stylesheet/stylus"
>
</style>
```
{% endcode %}

The above component is the`table`that will be used to display the records that will be consumed by the service we create. As in the`form`, the`schema`plays an important role in this component.

Now that we have created the`domain`\(and configured\), the`service`, the`schema`and the`views`, we will create the routes to be able to see the components being displayed.

{% page-ref page="adicionando-as-rotas.md" %}


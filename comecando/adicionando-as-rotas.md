---
description: Routes allow us to access the defined resources
---

# Adding routes

To create the basic routes we will add a new file to the domain we are working on called`routes.js`. This file will import auxiliary functions for creating routes and the`domain`and`path`values of the previously created file.

{% code title="src/domains/General/Category/routes.js" %}
```javascript
import { crud, group } from 'src/app/Util/routing'
import { domain, path } from './settings'

/**
 * @returns {Array<RouteConfig>}
 */
export default () => {
  // index
  const index = () => import('src/modules/Group.vue')
  // table
  const table = () => import('src/views/dashboard/general/category/CategoryTable')
  // form
  const form = () => import('src/views/dashboard/general/category/CategoryForm')

  const children = crud(domain, path, table, form)
  const meta = { namespace: domain, scope: 'group' }
  return [
    group(path, index, children, meta)
  ]
}
```
{% endcode %}

It is possible to notice that the auxiliary functions play a fundamental role in this file. They will use the components we create and create all 5 routes that will be responsible for designing the screens.

{% hint style="info" %}
This file must always return an `array`so that it can be registered in the module's`routeFile`in which it will be used, to see more about route manipulation check the [Routes](../como-utilizar/trabalhando-com-rotas.md) page
{% endhint %}

After creating the route file, we must register it in the most appropriate aggregation`routeFile`. In our case it is`src/modules/Dashboard/router/routeFile.js` and this will vary according to the organization created for the project. We can create other modules or files to aggregate other files in other domains.

After adding the routes we created, the`routeFile`will look similar to the excerpt below.

```javascript
import { group, redirect, route } from 'src/app/Util/routing'

import { index, layout, notFound } from './components'
import { updateTransition } from './middleware'

// ...

// general
import category from 'src/domains/General/Category/routes'

// ...

/**
 * @var {string}
 */
export const dashboard = '/dashboard/home'

/**
 * @param {AppRouter} router
 */
export default (router) => {
  //
  const routes = [
    // spread category dom
    ...category(),
    // ...
  ]
  // ...
}
```

After everything we've done so far, you can see the screens that have been pre-configured. The next step in the tutorial is to see this result and understand the concepts of how to work with it.

{% page-ref page="trabalhando-com-as-telas.md" %}


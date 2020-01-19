---
description: As rotas permitem que possamos acessar os recursos definidos
---

# Adicionando as rotas

Para criar as rotas básicas vamos adicionar um novo arquivo no domínio no qual estamos trabalhando chamado `routes.js`. Este arquivo irá importar funções auxiliares para criação de rotas e os valores de `domain` e de `path` do arquivo criado anteriormente.

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

É possível perceber que as funções auxiliares tem papel fundamental neste arquivo. São elas que vão usar os componentes que criamos e criar todas as 5 rotas que serão responsáveis por desenhar as telas.

{% hint style="info" %}
Este arquivo deve sempre retornar um `array` para que ele possa ser registrado no `routeFile` do módulo no qual será usado, para ver mais sobre a manipulação de rotas confira a página [Routes](../como-utilizar/trabalhando-com-rotas.md)
{% endhint %}

Depois de criarmos o arquivo de rotas devemos registrar ele no `routeFile` de agregação mais apropriado. No nosso caso é o `src/modules/Dashboard/router/routeFile.js` e isso vai variar de acordo com a organização criada para o projeto. Podemos criar outros módulos ou arquivos para agregar outros arquivos em outros domínios.

Depois de adicionar as rotas que criamos o `routeFile` ficará semelhante ao trecho abaixo.

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

Depois dessas alterações todas já será possível ver as telas que foram pré-configuradas.

{% page-ref page="brincando-com-as-telas.md" %}




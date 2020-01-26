---
description: Cada módulo é um ponto de partida de central para uma estrutura do projeto
---

# Modules

Os módulos possuem os recursos base para renderizar a estrutura que será usada para montar todas as suas telas filhas. Para isso serão configurados componentes para fazer a apresentação, rotas, gerenciadores de estado e etc. A aplicação já possui dois módulos criados: Auth e Dashboard.

![](../.gitbook/assets/image%20%2829%29.png)

## Módulo Auth

Este módulo está destinado à dar suporte às telas que são acessadas sem ter uma sessão definida. Estamos falando de telas como a que é usada pra informar usuário e senha para iniciar uma sessão, a que é usada para criar um usuário ou ainda para alterar a senha que foi perdida. Nesse caso iríamos adicionar tudo o que fosse base para essas telas e então iríamos prosseguir com a construção de seus `Services`, `Schema` e `Views`. Inicialmente ele possui as pastas abaixo, mas pode ser alterado livremente com a finalidade de implementar todos os recursos que o projeto demandar.

### store

Gerencia apenas dois estados: `token` e `user`. O estado user é explorado com `getters` para compor informações das telas de outros módulos, por exemplo.

### helper

Possui funções que são usadas para validar permissão e permitir acesso à recursos como rotas e menus.

### router

Possui apenas a rota da tela de login, mas pode ser incrementado para abrigar os recursos que forem criados para administrar o acesso do usuário que não possui uma sessão.

## Módulo Dashboard

Os recursos necessários para configurar o painel de controle, que é a área protegida da aplicação ficarão nesse módulo. Ele conta com as pastas:

### store

Gerencia `transition`, `report`, `title` que são relacionados à interface.

### router

Integra todas as rotas de dominios que são usados para criar telas para o módulo.

### components

Possui componentes para renderizar o menu superior direito e o menu lateral  esquerdo \(drawer\).

## Criando um novo módulo

Não há um padrão exato para a criação de um módulo. Provavelmente ele terá pelo menos um componente para renderizar a tela e um conjunto de rotas para tornar possível seu carregamento. Uma entrada no gerenciador de estados também pode ser necessária.

### Rotas

Para registrar as rotas do seu módulo basta criar um `routeFile` que exporta uma função que receba o `router` como argumento, importar a mesma no `src/router/index.js` e adicionar uma linha para executar esta função lá. Dentro do `routeFile` é possível adicionar `routes` e `middlewares`.

{% code title="src/router/index.js" %}
```javascript
// ...
import myModuleRouteFile from 'src/modules/MyModule/router/routeFile'
// ...

  // create router
  $router = new AppRouter(options)

  // ...

  // inject router on auth module
  authRouteFile($router)
  // inject router on dashboard module
  dashboardRouteFile($router)
  // inject router on MyModule module
  myModuleRouteFile($router)
```
{% endcode %}

### Gerenciamento de Estado

Para registrar a uma `store` que tenha sido criada pelo módulo basta ir até a `store` principal em `src/store/index.js`, importar e registrar como um módulo.

{% code title="src/store/index.js" %}
```javascript
// ...
import myModule from 'src/modules/MyModule/store'
// ...

  // create store
  $store = new Vuex.Store({
    modules: {
      app,
      auth, // register auth router
      dashboard, // register dashboard router
      myModule // register the new module MyModule
    },
    // enable strict mode (adds overhead!)
    // for dev mode only
    strict: process.env.DEV
  })
```
{% endcode %}




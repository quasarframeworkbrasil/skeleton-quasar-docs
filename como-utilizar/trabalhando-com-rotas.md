---
description: >-
  Vamos entender como é feita a composição de rotas para o VueRouter  no
  Skeleton, já que a mesma é feita de forma diferente do padrão que se costuma
  ver em projetos Quasar ou Vue
---

# Routes

Em `src/router/index.js` fica a criação do roteador da aplicação. Há alguns detalhes um pouco diferentes do padrão que o template do [Quasar](https://quasar.dev) entrega. Vamos ver um sobre essas diferenças à seguir.

## Uso do AppRouter

Logo do começo do `index.js` será possível ver que há um import para um arquivo chamado `AppRouter.` Isto será visto em um trecho parecido com o trecho abaixo.

![](https://github.com/quasarframeworkbrasil/skeleton-quasar-docs/tree/837016d4104c9c9d353b7091e5fbb7e128181839/.gitbook/assets/image-12.png)

Este arquivo é uma classe que estende o `VueRouter` permitindo modificar, aprimorar e adicionar comportamentos ao roteador.

![](https://github.com/quasarframeworkbrasil/skeleton-quasar-docs/tree/837016d4104c9c9d353b7091e5fbb7e128181839/.gitbook/assets/image-5.png)

## Injeção do `Router`

Além de configurar dois `middleware` base também há a configuração das rotas. Esta configuração é feita de uma forma diferente, ao invés de "puxar" as rotas e adicioná-las como argumento na construção do `router` são importadas funções \(também chamadas de `RouteFile`\) que recebem o `$router` como argumento para que cada módulo seja responsável por adicionar suas rotas.

![](https://github.com/quasarframeworkbrasil/skeleton-quasar-docs/tree/837016d4104c9c9d353b7091e5fbb7e128181839/.gitbook/assets/image-6.png)

Esta mudança permite que os módulos tenham mais independência sobre as configurações que podem fazer no projeto. Logo, ao invés de ter apenas um `beforeEach`, por exemplo, teremos vários `middleware` deste tipo distribuídos pelo projeto.

## Auth `RouteFile`

O `RouteFile` do `module` Auth fica em `src/modules/Auth/router/routeFile.js` e é bem simples, tendo apenas uma rota. Como falado à pouco ele recebe o router como parâmetro e utiliza o método `addRoutes` para adicionar as rotas. No caso estão sendo usados helpers `route` e `group` para criar as rotas. Estas funções constroem objetos compatíveis com a [RouteConfig](https://router.vuejs.org/api/#routes) que são as estruturas tradicionais de rotas.

![](https://github.com/quasarframeworkbrasil/skeleton-quasar-docs/tree/837016d4104c9c9d353b7091e5fbb7e128181839/.gitbook/assets/image-8.png)

## Dashboard `RouteFile`

Alocado em `src/modules/Dashboard/router/routeFile.js` a composição de rotas do `Dashboard` será bem mais extensa que a do `Auth`. Este `module` irá abrigar todo "painel de controle", por isso ao invés de definir todas as rotas nele mesmo são feitos imports de outros arquivos de rota. As demais rotas ficam junto do domínio do Schema e devem exportar sempre arrays. Para poder acessar os recursos que serão criados será preciso registar as rotas que criarmos nesse arquivo, por isso ele será lembrado mais pra frente.

![](https://github.com/quasarframeworkbrasil/skeleton-quasar-docs/tree/837016d4104c9c9d353b7091e5fbb7e128181839/.gitbook/assets/image-22.png)

## Arquivos de Rotas

Um arquivo de rotas precisa simplesmente exportar uma função que retorne um array de rotas como a imagem abaixo.

![](https://github.com/quasarframeworkbrasil/skeleton-quasar-docs/tree/837016d4104c9c9d353b7091e5fbb7e128181839/.gitbook/assets/image-13.png)

### Criando Rotas de CRUD

Quando se está criando uma quantidade grande de telas é comum repetir diversas vezes vários trechos e configurações. Para acelerar a criação é possível usar alguns helpers para a criação de rotas para CRUD, como pode ser visto no exemplo abaixo.

![](https://github.com/quasarframeworkbrasil/skeleton-quasar-docs/tree/837016d4104c9c9d353b7091e5fbb7e128181839/.gitbook/assets/image-33.png)

Este trecho acima cria um conjunto de 5 rotas devidamente configuradas. Para utilizar alguns recursos que estão pré-configurados no projeto é preciso configurar alguns detalhes no meta das rotas. A função `crud` já resolve isso e introduz o `scope` e o `namespace` no [`meta`](https://router.vuejs.org/guide/advanced/meta.html) das rotas, permitindo que sejam passadas configurações adicionais. O exemplo a seguir é um trecho do arquivo [`src/app/Util/routing.js`](https://github.com/quasarframeworkbrasil/skeleton/blob/master/src/app/Util/routing.js#L53).

![Trecho da fun&#xE7;&#xE3;o crud de src/app/Util/routing](https://github.com/quasarframeworkbrasil/skeleton-quasar-docs/tree/837016d4104c9c9d353b7091e5fbb7e128181839/.gitbook/assets/image-14.png)


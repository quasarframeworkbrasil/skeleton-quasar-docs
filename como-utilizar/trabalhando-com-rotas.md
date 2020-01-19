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

![](../.gitbook/assets/image%20%2810%29.png)

Este arquivo é uma classe que estende o `VueRouter` permitindo modificar, aprimorar e adicionar comportamentos ao roteador.

![](../.gitbook/assets/image%20%284%29.png)

## Injeção do `Router`

Além de configurar dois `middleware` base também há a configuração das rotas. Esta configuração é feita de uma forma diferente, ao invés de "puxar" as rotas e adicioná-las como argumento na construção do `router` são importadas funções \(também chamadas de `RouteFile`\) que recebem o `$router` como argumento para que cada módulo seja responsável por adicionar suas rotas.

![](../.gitbook/assets/image%20%285%29.png)

Esta mudança permite que os módulos tenham mais independência sobre as configurações que podem fazer no projeto. Logo, ao invés de ter apenas um `beforeEach`, por exemplo, teremos vários `middleware` deste tipo distribuídos pelo projeto.

## Auth `RouteFile`

O `RouteFile` do `module` Auth fica em `src/modules/Auth/router/routeFile.js` e é bem simples, tendo apenas uma rota. Como falado à pouco ele recebe o router como parâmetro e utiliza o método `addRoutes` para adicionar as rotas. No caso estão sendo usados helpers `route` e `group` para criar as rotas. Estas funções constroem objetos compatíveis com a [RouteConfig](https://router.vuejs.org/api/#routes) que são as estruturas tradicionais de rotas.

![](../.gitbook/assets/image%20%286%29.png)

## Dashboard `RouteFile`

Alocado em `src/modules/Dashboard/router/routeFile.js` a composição de rotas do `Dashboard` será bem mais extensa que a do `Auth`. Este `module` irá abrigar todo "painel de controle", por isso ao invés de definir todas as rotas nele mesmo são feitos imports de outros arquivos de rota. As demais rotas ficam junto do domínio do Schema e devem exportar sempre arrays. Para poder acessar os recursos que serão criados será preciso registar as rotas que criarmos nesse arquivo, por isso ele será lembrado mais pra frente.

![](../.gitbook/assets/image%20%2818%29.png)




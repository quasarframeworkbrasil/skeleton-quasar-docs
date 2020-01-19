---
description: >-
  As aplicações front-end precisando se comunicar com serviços que proveem dados
  e geralmente esses serviços usam HTTP
---

# Preparando o acesso à API

Seguindo com nosso exemplo, vamos criar dentro de `src/domains/Admin/Action` uma pasta chamada `Schema`. Dentro desta pasta crie um arquivo chamado `ActionService.js`, tendo no final um caminho `src/domains/Admin/Action/Schema/ActionService.js`. 

{% hint style="info" %}
Estes caminhos podem variar de acordo com as necessidades de cada um e estão aqui apenas como sugestão. Com um pouco de experiência é possível compreender o que está sendo feito e usar da forma que julgar conveniente
{% endhint %}

O conteúdo desse documento será uma classe semelhante a imagem abaixo. Ao estender a class `Rest` a class `ActionService` herda todos os comportamentos dela. Estes comportamentos englobam métodos que fazem a criação, leitura, atualização e deleção de recursos da entidade `Action`.

![](../.gitbook/assets/image%20%289%29.png)

Note o uso da propriedade `resource` que é importada do `settings.js`. Para conhecer mais detalhes sobre [`Services`](../como-utilizar/service.md) dentro do projeto acesse [esta página](../como-utilizar/service.md).

{% hint style="warning" %}
Não há uma classe para consumir recursos usando [`GraphQL`](https://graphql.org), mas a lógica é basicamente a mesma e com algum conhecimento de JavaScript é possível criar uma abstração também para este tipo de serviço
{% endhint %}

Esta classe será usada a seguir para prover acesso aos endpoints da entidade, vamos seguir para o próximo passo.

{% page-ref page="definindo-o-schema.md" %}


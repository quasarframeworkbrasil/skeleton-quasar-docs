# Preparando o acesso à API

Seguindo com nosso exemplo, vamos criar dentro de `src/domains/Admin/Action` uma pasta chamada `Schema`. Dentro desta pasta crie um arquivo chamado `ActionService.js`, tendo no final um caminho `src/domains/Admin/Action/Schema/ActionService.js`. 

{% hint style="info" %}
Estes caminhos podem variar de acordo com as necessidades de cada um e estão aqui apenas como sugestão. Com um pouco de experiência é possível compreender o que está sendo feito e usar da forma que julgar conveniente
{% endhint %}

O conteúdo desse documento será algo como

![](../.gitbook/assets/image%20%288%29.png)

Note o uso da propriedade `resource` que é importada do `settings.js`.

Esta classe será usada posteriormente para prover acesso aos endpoints da entidade.

{% page-ref page="definindo-o-schema.md" %}


---
description: A configuração o domínio é a base para a criação dos artefatos do domínio
---

# Configurando o domínio

Dentro desta pasta `src/domains/Admin/Action`  criada anteriormente \(veja [Domain](../como-utilizar/domain.md)\) iremos criar o `settings.js` da entidade `Action`. O caminho final desse arquivo então será `src/domains/Admin/Action/settings.js`. 

Dentro deste arquivo vamos exportar as 3 consts comumente usados por ele: `path`, `domain` e `resource`. 

![Exemplo de arquivo settings.js para a entidade Admin\Action](../.gitbook/assets/image%20%2820%29.png)

Em [`path`](../como-utilizar/settings.md#path) vamos informar a URL base das telas do domínio que estamos configurando, para ver mais sobre isso confira a página [Settings](../como-utilizar/settings.md#path).

A propriedade [`domain`](../como-utilizar/settings.md#domain) caso está com o valor `admin.action` por o caminho `src/domains/Admin/Action`.

Por fim em [`resource`](../como-utilizar/settings.md#resource), foi utilizado o valor `/admin/action` que será usado para compor as requisições que serão feitas às APIs utilizadas.

{% page-ref page="criando-o-service.md" %}


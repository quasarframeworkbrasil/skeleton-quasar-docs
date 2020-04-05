---
description: A configuração o domínio é a base para a criação dos artefatos do domínio
---

# Configurando o domínio

Dentro desta pasta `src/domains/General/Category` criada anteriormente \(veja [Domain](../como-utilizar/domain.md)\) iremos criar o `settings.js` da entidade `Category`. O caminho final desse arquivo então será `src/domains/General/Category/settings.js`. Os [Settings File](../como-utilizar/settings.md) são documentos que agregam propriedades básicas de configuração do domínio.

Dentro deste arquivo vamos exportar as 3 consts comumente usados por ele: `path`, `domain` e `resource`.

{% code title="src/domains/General/Category/settings.js" %}
```javascript
/**
 * @type {string}
 */
export const path = '/dashboard/general/category'

/**
 * @type {string}
 */
export const domain = 'general.category'

/**
 * @type {string}
 */
export const resource = '/general/category'
```
{% endcode %}

Em [`path`](../como-utilizar/settings.md#path) vamos informar a URL base das telas do domínio que estamos configurando, para ver mais sobre isso confira a página [Settings](../como-utilizar/settings.md#path).

A propriedade [`domain`](../como-utilizar/settings.md#domain), por sua vez, está com o valor `general.category` porque o caminho para o domínio é `src/domains/General/Category` e o mesmo será usado para recuperar alguns recursos necessários nas construções das telas.

Por fim em [`resource`](../como-utilizar/settings.md#resource), foi utilizado o valor `/general/category` que será usado para compor as requisições que serão feitas às APIs utilizadas.

{% page-ref page="criando-o-service.md" %}


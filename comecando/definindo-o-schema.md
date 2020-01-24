---
description: >-
  Os schema são agrupamento de recursos que serão usados para prover
  comportamentos e estados para as regras de negócio
---

# Definindo o schema

### Criando o Schema

Para criar um `schema` para a entidade `Category` criaremos dentro da pasta `Schema` do domínio um arquivo `CategorySchema.js` \(`src/domains/General/Category/Schema/CategorySchema.js`\). Este arquivo deverá estender a classe `Schema`. O resultado inicial será um documento como o do trecho a seguir.

{% code title="src/domains/General/Category/Schema/CategorySchema.js" %}
```javascript
import Schema from 'src/app/Agnostic/Schema'

/**
 * @class {CategorySchema}
 */
export default class CategorySchema extends Schema {
  construct () {
  }
}

```
{% endcode %}

### Importando Recursos

Esta definição é a mais básica que podemos fazer para esta classe porque o método `construct` deve ser implementado mesmo nessa primeira versão. Além desse método vamos fazer mais algumas configurações, informando na estrutura da classe as propriedades: `domain`, `path` e `service`. 

{% code title="src/domains/General/Category/Schema/CategorySchema.js" %}
```javascript
import Schema from 'src/app/Agnostic/Schema'
import Service from 'src/domains/General/Category/Schema/CategoryService'
import { path, domain } from 'src/domains/General/Category/settings'

/**
 * @class {CategorySchema}
 */
export default class CategorySchema extends Schema {
  /**
   * @type {string}
   */
  static domain = domain

  /**
   * @type {string}
   */
  static path = path

  /**
   * @type {Rest}
   */
  service = Service

  /**
   * Configure schema
   */
  construct () {
  }
}

```
{% endcode %}

As propriedades estáticas `domain` e `path` são importados do `settings.js` que definimos em [Configurando o domínio](configurando-o-dominio.md) e a propriedade `service` é o arquivo `CategoryService.js` que criamos em [Preparando o acesso à API](criando-o-service.md).

### Criando o Campo `name`

Com o nosso schema inciado vamos configurar os campos que serão usados pela entidade. Para isso vamos usar o método `addField` que deve ser chamado dentro do `construct`.

{% code title="src/domains/General/Category/Schema/CategorySchema.js" %}
```javascript
// ...

/**
 * @class {CategorySchema}
 */
export default class CategorySchema extends Schema {
  // ...

  /**
   * Configure schema
   */
  construct () {
    this.addField('name')
  }
}

```
{% endcode %}

No trecho de código acima declaramos que o nosso `schema` irá trabalhar com o campo `name`.  Por padrão um campo criado não é exibido na `table` e é exibido no `form` com uma largura que ocupa 100% da linha num campo de texto. O campo `primaryKey` é carregado de forma implícita em todos os filhos de `Schema`. Portanto, nossa classe está mapeando dois campos: `id` e `name`. Mais adiante veremos as configurações dos campos e tudo que podemos fazer com eles, além de outros recursos configuráveis nos nossos [`schema`](../como-utilizar/schema.md).

No próximo passo veremos como adicionar algumas rotas para podermos ver nossa tela sendo renderizada.

{% page-ref page="criando-as-views.md" %}




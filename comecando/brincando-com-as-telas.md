---
description: >-
  Neste passo já temos artefatos suficientes para ver algum resultado sendo
  renderizado, vamos brincar com eles agora
---

# Brincando com as telas

## Acessando as telas

Se acessarmos [http://localhost:8080/\#/dashboard/general/category](http://localhost:8080/#/dashboard/general/category) será possível ver a tela que exibe a table da entidade `Category` que criamos \(imaginando que não foi feita nenhuma alteração nas configurações padrão do projeto\). A seguir uma imagem do resultado de abrir o link acima.

![](../.gitbook/assets/image%20%2824%29.png)

Como podemos ver a tela ficou vazia, além disso foi gerado um erro no console.

![](../.gitbook/assets/image%20%2826%29.png)

A tela está vazia porque o nosso campo ainda está visível na `table` \(além de não ter `label` definido\) e não temos uma `API` para ser consumida.

## Configurando o `schema`

Os `schema` são estruturas que possuem diversos recursos para serem configurados, vamos configurar alguns a seguir. Para ver todas as configurações do `schema` vá até a página do [Schema](../como-utilizar/schema.md).

### Arquivo de Internacionalização

Para carregar os textos dos campos são usados arquivos isolados com as mensagens que serão escritas. Crie um arquivo com o nome `pt-br.js` na pasta do domínio \(`src/domains/General/Category/pt-br.js`\) com as mensagens básicas necessárias.

{% code title="src/domains/General/Category/pt-br.js" %}
```javascript
import { SCOPES } from 'src/app/Agnostic/enum'

/**
 */
export default {
  routes: {
    group: {
      crumb: 'Categorias'
    },
    [SCOPES.SCOPE_INDEX]: {
      title: 'Categorias'
    },
    [SCOPES.SCOPE_TRASH]: {
      title: 'Lixeira das Categorias',
      crumb: 'Lixeira'
    },
    [SCOPES.SCOPE_ADD]: {
      title: 'Criar Categoria',
      crumb: 'Criar'
    },
    [SCOPES.SCOPE_VIEW]: {
      title: 'Visualizar Categoria',
      crumb: 'Visualizar'
    },
    [SCOPES.SCOPE_EDIT]: {
      title: 'Editar Categoria',
      crumb: 'Editar'
    }
  },
  print: {
    title: 'Impressão de Categoria'
  },
  fields: {
    name: 'Nome'
  }
}

```
{% endcode %}

Estamos usando esse nome por conta da configuração que está no `.env`.

```bash
# the messages group of language to use
VUE_APP_LOCALE="pt-br"
```

Depois de criar o arquivo precisamos registrar ele no arquivo de mensagens no diretório `lang/`. Para isso podemos acessar `src/lang/pt-br/domains.js` e adicionar o mesmo lá. O resultado será algo parecido com o trecho abaixo.

{% code title="src/lang/pt-br/domains.js" %}
```javascript
// ...

// domain/General
import category from 'src/domains/General/Category/pt-br'

// ...

/**
 */
export default {
  // ...
  general: {
    category
  },
  // ...
}

```
{% endcode %}

### Exibindo o campo na `table`




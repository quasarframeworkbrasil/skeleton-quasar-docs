---
description: >-
  Neste passo já temos artefatos suficientes para ver algum resultado sendo
  renderizado, vamos ver como trabalhar com eles agora
---

# Começando com as telas

## Acessando as telas

Se acessarmos [`http://localhost:8080/#/dashboard/general/category`](http://localhost:8080/#/dashboard/general/category) será possível ver a tela que exibe a table da entidade `Category` que criamos \(imaginando que não foi feita nenhuma alteração nas configurações padrão do projeto\). A seguir uma imagem do resultado de abrir o link acima.

![](../.gitbook/assets/image%20%2827%29.png)

Como podemos ver a tela ficou vazia, além disso foi gerado um erro no console.

![](../.gitbook/assets/image%20%2829%29.png)

A tela está vazia porque o nosso campo ainda está visível na `table` \(além de não ter `label` definido\) e não temos uma `API` para ser consumida. Vamos ver sobre como melhorar isso nos tópicos a seguir.

## Configurando o `schema`

Os `schema` são estruturas que possuem diversos recursos para serem configurados, vamos configurar alguns a seguir. Para ver todas as configurações do `schema` vá até a página do [Schema](../como-utilizar/schema.md).

### Arquivo de Internacionalização

Para carregar os textos dos campos são usados arquivos isolados com as mensagens que serão escritas. Crie um arquivo com o nome `pt-br.js` na pasta do domínio \(`src/domains/General/Category/pt-br.js`\) com as mensagens básicas necessárias. Note que estamos utilizando uma propriedade chamada `SCOPES` para definir algumas propriedades, veja mais sobre isso [aqui](../como-utilizar/scopes-e-positions.md).

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

### Trabalhando com a `table`

Para exibir um campo na `table` podemos chamar o método `fieldTableShow`.

{% code title="src/domains/General/Category/Schema/CategorySchema.js" %}
```javascript
 // ...
   /**
   * Configure schema
   */
   construct () {
    this.addField('name')
      .fieldTableShow()
   }
 // ...
```
{% endcode %}

Com a internacionalização definida e o campo configurado para ser visível podemos ver que a tela da aplicação agora mostra o campo "Nome".

![](../.gitbook/assets/image%20%283%29.png)

A table possui um campo de pesquisa, para colocar o campo para aparecer lá podemos usar o método `fieldTableWhere`.

{% code title="src/domains/General/Category/Schema/CategorySchema.js" %}
```javascript
// ...
   /**
   * Configure schema
   */
   construct () {
    this.addField('name')
      .fieldTableShow()
      .fieldTableWhere()
   }
 // ...
```
{% endcode %}

O resultado será algo como a imagem abaixo.

![](../.gitbook/assets/image%20%2826%29.png)

Para simular um conjunto de dados na `table` podemos modificar o `CategoryService` para gerar dados `fake`. Abaixo um exemplo de como ficaria uma sobrescrita do método `paginate` para gerar dados para mostrar dados falsos e popular a lista de registros. Num ambiente real é feita a adaptação do sistema de `fetch records` para lidar com as repostas da API que é consumida. 

{% code title="src/domains/General/Category/Schema/CategoryService.js" %}
```javascript
import Rest from 'src/app/Services/Rest'
import { resource } from 'src/domains/General/Category/settings'
import { get, uuid, promisify } from 'src/app/Util/general'

/**
 * @class {CategoryService}
 */
export default class CategoryService extends Rest {
  /**
   * @type {string}
   */
  resource = resource

  /**
   * @param {Record<string, string | number>} parameters
   * @param {Array<string>} [filters] = []
   * @param {boolean} [trash] = false
   * @returns {Promise<any>}
   */
  paginate (parameters, filters, trash = false) {
    const { pagination } = parameters

    const rowsPerPage = get(pagination, 'rowsPerPage', this.size)
    const sortBy = get(pagination, 'sortBy')
    const descending = get(pagination, 'descending')
    const page = get(pagination, 'page', 1)

    const rowsNumber = 32
    const pagesNumber = Math.ceil(rowsNumber / rowsPerPage)
    let length = rowsPerPage
    if (page === pagesNumber) {
      length = rowsNumber % (pagesNumber - 1)
    } else if (page > pagesNumber) {
      length = 0
    }

    const generator = (value, index) => {
      const counter = (page - 1) * rowsPerPage + index + 1
      return {
        id: uuid(),
        name: `Name fake ${counter}`
      }
    }

    return promisify({
      rowsPerPage: rowsPerPage,
      rowsNumber: rowsNumber,
      pagesNumber: pagesNumber,
      sortBy: sortBy,
      descending: descending,
      page: page,
      rows: Array.from({ length }, generator)
    })
  }
}
```
{% endcode %}

Então agora podemos ver os dados sendo exibidos na tela.

![](../.gitbook/assets/image%20%2816%29.png)

Para saber mais sobre como configurar a parte de comunicação acesse a página [Project Settings](../como-utilizar/project-settings.md).

### Trabalhando com o `form`

O mesma `schema` que vimos que pode configurar a `table` também será responsável pelas definições dos `forms`.

{% page-ref page="proximos-passos.md" %}




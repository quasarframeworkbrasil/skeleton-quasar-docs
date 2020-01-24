---
description: >-
  Neste passo já temos artefatos suficientes para ver algum resultado sendo
  renderizado, vamos ver como trabalhar com eles agora
---

# Trabalhando com as telas

## Acessando as telas

Se acessarmos [`http://localhost:8080/#/dashboard/general/category`](http://localhost:8080/#/dashboard/general/category) será possível ver a tela que exibe a `table` da entidade `Category` que criamos \(imaginando que não foi feita nenhuma alteração no que vem por padrão de configuração no projeto\). A seguir uma imagem do resultado que pode ser visto após abrir o link acima.

![](../.gitbook/assets/image%20%2828%29.png)

Como podemos ver, a tela ficou vazia e foi gerado um erro no console.

![](../.gitbook/assets/image%20%2830%29.png)

A tela está vazia porque o nosso campo ainda está visível na `table` \(além de não ter `label` definido\) e não temos uma `API` para ser consumida. Veremos como melhorar isto nos tópicos a seguir.

É possível perceber que vários recursos já são criados por padrão, botões, campo de pesquisa e uma pesquisa avançada lateral vem por padrão quando criamos uma `table` usando o componente que vem incorporado ao projeto. Mais abaixo veremos detalhes sobre eles. Caso ainda tenha dúvida vá até a sessão [Conceitos](../como-utilizar/).

## Configurando o `schema`

Os `schemes` são estruturas que possuem diversos recursos para serem configurados, vamos configurar alguns a seguir. Para ver todas as configurações do `schema` vá até a página do [Schema](../como-utilizar/schema.md).

### Arquivo de Internacionalização

Para carregar os textos dos campos são usados arquivos isolados com as mensagens que serão escritas. Crie um arquivo com o nome `pt-br.js` na pasta do domínio \(`src/domains/General/Category/pt-br.js`\) com as mensagens básicas necessárias. Note que estamos utilizando uma propriedade chamada `SCOPES` para definir algumas propriedades, veja mais sobre isto [aqui](../como-utilizar/scopes-e-positions.md).

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

Como visto mais acima a tabela que lista os registros de Category está disponível na URL [`http://localhost:8080/#/dashboard/general/category`](http://localhost:8080/#/dashboard/general/category).

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

![](../.gitbook/assets/image%20%2827%29.png)

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

O mesmo `schema` que vimos que pode configurar a `table` também será responsável pelas definições dos `forms`. Podemos visualizar o form que cria um registro em  [`http://localhost:8080/#/dashboard/general/category/add`](http://localhost:8080/#/dashboard/general/category/add).

![](../.gitbook/assets/image%20%2821%29.png)

O campo Nome está sendo exibido porque toda vez que a gente usa o `addField`, diferentemente da `table` o `form` por padrão vai exibir o campo. Para ocultar o campo precisamos usar o método `fieldFormHidden`. O campo de texto é exibido porque por esse é o componente padrão para um campo que é adicionado. O método `fieldIsInput` é um método que é chamado implicitamente quando nenhum componente é definido.

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
      .fieldFormHidden()
  }
// ...
```
{% endcode %}

É possível passar um argumento `boolean` para o método `fieldFormHidden` para determinar se ele será `hidden` ou não, o padrão é verdadeiro. Seguindo com as possibilidades podemos definir que o campo deve receber o foco no carregamento, sua largura ou se ele é obrigatório ou não.

{% code title="src/domains/General/Category/Schema/CategorySchema.js" %}
```javascript

/**
 * Configure schema
 */
construct () {
  this.addField('name')
    .fieldTableShow()
    .fieldTableWhere()
    .fieldFormAutofocus()
    .fieldFormWidth(50)
    .validationRequired()
}
```
{% endcode %}

As mudanças acima farão com que o form fique dessa forma.

![](../.gitbook/assets/image%20%2838%29.png)

Dentre os detalhes temos que o parâmetro `width` do método `fieldFormWidth` corresponde à largura do campo na tela e pode receber valores entre 1 e 100 que correspondem a porcentagem da linha que será ocupada pelo campo. O padrão para essa propriedade é 100 e é por isto que na primeira vez que o form foi aberto o campo estava ocupando a linha toda e na imagem acima ocupa apenas metade dela. O método `validationRequired`, por sua vez, torna o campo obrigatório. Se clicarmos no botão _SALVAR_, o resultado será a imagem a seguir.

![](../.gitbook/assets/image%20%2841%29.png)

A lib de validação base que é usada é o Vuelidate, logo todas as definições de validação disponíveis na lib estão disponíveis no schema.

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
      .fieldFormAutofocus()
      .validationRequired()
      .validationMinLength()
  }
// ...
```
{% endcode %}

Com o trecho acima conseguimos algo como o que pode ser visto abaixo.

![](../.gitbook/assets/image%20%2831%29.png)

Seguindo essa mesma dinâmica podemos adicionar mais campos e configurar eles usando os métodos disponíveis na classe `Schema` ou simplesmente criando nossos próprios métodos.

{% page-ref page="proximos-passos.md" %}




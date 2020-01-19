---
description: >-
  Com o schema e o settings definidos podemos seguir para o próximo passo que é
  criar as views responsáveis por renderizar as telas
---

# Criando as views

Os componentes de apresentação padrão são relativamente simples e não precisam de uma implementação muita extensa.

A sugestão da estrutura é colocar as views da entidade `Category`, do domínio `General` dentro módulo `Dashboard` dentro de uma pasta com o caminho`src/views/dashboard/general/category`. Depois de criar esse diretório podemos criar as duas views que são necessárias para manter as operações de criar, visualizar, editar, apagar e pesquisar os registros desta entidade: `CategoryForm.vue` e `CategoryTable.vue`. A seguir exemplos de implementação dos dois.

{% code title="src/views/dashboard/general/category/CategoryForm.vue" %}
```markup
<template>
  <SchemaForm v-bind="bind" />
</template>

<script type="text/javascript">
import View from 'src/app/Agnostic/Adapters/View'
import Schema from 'src/domains/General/Category/Schema/CategorySchema'

/**
 */
export default {
  /**
   */
  extends: View,
  /**
   */
  name: 'CategoryForm',
  /**
   */
  schema: Schema
}
</script>

<style
  lang="stylus"
  rel="stylesheet/stylus"
>
</style>

```
{% endcode %}

{% code title="src/views/dashboard/general/category/CategoryTable.vue" %}
```markup
<template>
  <SchemaTable v-bind="bind" />
</template>

<script type="text/javascript">
import View from 'src/app/Agnostic/Adapters/View'
import Schema from 'src/domains/General/Category/Schema/CategorySchema'

/**
 */
export default {
  /**
   */
  extends: View,
  /**
   */
  name: 'CategoryTable',
  /**
   */
  schema: Schema
}
</script>

<style
  lang="stylus"
  rel="stylesheet/stylus"
>
</style>

```
{% endcode %}

Agora que já criamos o `domain` \(e configuramos\), o `service`, o `schema` e as `views` vamos criar as rotas para poder ver os componentes sendo exibidos.

{% page-ref page="adicionando-rotas.md" %}


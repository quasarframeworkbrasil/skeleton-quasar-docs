---
description: >-
  Para cada entidade criamos um arquivo chamado settings.js para agrupar
  propriedades básicas do domínio dela
---

# Settings File

## `path`

Esta propriedade irá indicar qual será a rota base que será usada nas rotas que serão criadas para acessar as telas deste domínio.

## `domain`

É uma string com o caminho à partir da pasta `domains/` usando [`kabeb-case`](https://en.toolpage.org/tool/kebabcase) para os nomes das pastas e ponto \(`.`\) como separador de nível. Para uma entidade em `src/domain/Venda/Pedido` teremos `venda.pedido`. Para nomes compostos como `Venda/PedidoItem` teremos `venda.pedido-item`, substituindo a letra maiúscula no meio por hyphen \(`-`\) seguido da mesma letra que estava maiúscula por sua versão minúscula.

## `resource`

O `resource` é o endpoint base da entidade na `API RESTful` que será consumida. Pode ser algo como `/posts` ou `blog/posts` e será a parte final da URL que será usada para compor as requisições que serão feitas para gerenciar os recursos. Se a API estiver montada em cima de `http://localhost:8000` \(nos arquivos `.env` este será o valor da variável `VUE_APP_REST_BASE_URL`\) a URL final será `http://localhost:8000/posts` ou `http://localhost:8000/blog/posts`, de acordo com os exemplos citados acima. Em cima dessa URL serão aplicados os verbos `GET`, `POST`, `PUT`, `PATCH` e `DELETE`.


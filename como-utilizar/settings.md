---
description: >-
  Para cada entidade criamos um arquivo chamado settings.js para agrupar
  propriedades básicas do domínio dela
---

# Settings

### `path`

Esta propriedade irá indicar qual será a rota base que será usada nas rotas que serão criadas para acessar as telas deste domínio.

### `domain`

É uma string com o caminho à partir da pasta `domains/` usando [`kabeb-case`](https://en.toolpage.org/tool/kebabcase) para os nomes das pastas e ponto \(`.`\) como separador de nível. No nosso caso está `admin.action` por o caminho `src/domains/Admin/Action`. Se fosse algo como `src/domains/Cadastro/Cliente` seria `cadastro.cliente`. Para nomes compostos como `Venda/PedidoItem`  ficaria `venda.pedido-item`, substituindo a letra maiúscula no meio por hyphen \(`-`\) seguido da mesma letra que estava maiúscula por sua versão minúscula.

### `resource`

O `resource` é o endpoint base da entidade na `API RESTful` que será consumida. No exemplo o valor utilizado foi `/admin/action` e será a parte final da URL que será usada para compor as requisições que serão feitas para gerenciar os recursos.


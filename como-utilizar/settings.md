---
description: >-
  Para cada entidade criamos um arquivo chamado settings.js para agrupar
  propriedades básicas do domínio dela
---

# Settings

## O Arquivo `settings.js` 

Dentro desta pasta `src/domains/Admin/Action`  criada anteriormente \(veja [Domain](domain.md)\) iremos criar o `settings.js` da entidade `Action`. O caminho final desse arquivo então será `src/domains/Admin/Action/settings.js`. 

Dentro deste arquivo iremos exportar 3 consts: `path`, `domain` e `resource`. Geralmente será um padrão para todos os arquivos desse tipo e veremos mais pra frente que os demais artefatos irão importar essas configurações.

![Exemplo de arquivo settings.js para a entidade Admin\Action](../.gitbook/assets/image%20%2818%29.png)

### `path`

Esta propriedade irá indicar qual será a rota base que será usada nas rotas que serão criadas para acessar as telas deste domínio.

### `domain`

É uma string com o caminho à partir da pasta `domains/` usando [`kabeb-case`](https://en.toolpage.org/tool/kebabcase) para os nomes das pastas e ponto \(`.`\) como separador de nível. No nosso caso está `admin.action` por o caminho `src/domains/Admin/Action`. Se fosse algo como `src/domains/Cadastro/Cliente` seria `cadastro.cliente`. Para nomes compostos como `Venda/PedidoItem`  ficaria `venda.pedido-item`, substituindo a letra maiúscula no meio por hyphen \(`-`\) seguido da mesma letra que estava maiúscula por sua versão minúscula.

### `resource`

O `resource` é o endpoint base da entidade na `API RESTful` que será consumida. No exemplo o valor utilizado foi `/admin/action` e será a parte final da URL que será usada para compor as requisições que serão feitas para gerenciar os recursos.


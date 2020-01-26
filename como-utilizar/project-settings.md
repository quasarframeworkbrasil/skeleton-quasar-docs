---
description: >-
  Para poder configurar a estrutura existe uma pasta que centraliza o que é
  parametrizável dentro do projeto
---

# Settings \[project\]

A pasta `src/settings` possui vários arquivos de configuração. Através deles é possível configurar uma série de recursos que veremos a seguir.

### `components.js`

Configura os componentes da aplicação de um modo geral. Através dele podemos aplicar configurações à todos os campos de texto do sistema, por exemplo.

### `date.js`

Lida com os formatos e configurações de datas que são suportadas

### `field.js`

Constitui uma fábrica de construção de campos com todas as propriedades que um campo deve possuir.

### `http.js`

Instância de cliente HTTP para realizar conexões na API base da aplicação. Possui interceptadores e será alterado para passar `headers` e modificar as configurações básicas de conexão.

### `local.js`

É a instância de cliente HTTP para fazer requests para o próprio projeto. Ele cria um cliente que aponta para a URL na qual o projeto está disponível no navegador.

### `report.js`

Representa as configurações que podem ser feitas para executar os relatórios.

### `rest.js`

Possui recursos para adaptar a comunicação da classe `Rest` com as respostas que as APIs retornam.

### `schema.js`

Agrupa as principais propriedades que podemos alterar na construção do `schema` e conversão de um `field` em um componente [`Vue`](https://vuejs.org).


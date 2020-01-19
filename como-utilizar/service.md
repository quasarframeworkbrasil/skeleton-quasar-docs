---
description: >-
  Os serviços são responsáveis por consumir dados dos servidores e são muito
  importantes para a lógica de negócio da aplicação
---

# Services

## Estrutura dos Services

Na pasta `app/` existem uma série de documentos que estão pré-configurados e prontos para serem estendidos. Dentre estes temos alguns que são destinados para a criação do nossos serviços.

Caso o `service` em questão não vá atender um `CRUD` é possível estender apenas de `Http` e ter acesso apenas aos métodos referentes aos verbos `HTTP`.

![Exemplo de service que usa apenas a classe Http](../.gitbook/assets/image%20%2827%29.png)

Um service criado para resolver as operações básicas vai estender de `Rest` e terá uma sintaxe parecida com a imagem abaixo.

![Service Rest simples](../.gitbook/assets/image%20%2830%29.png)

### Http

A classe Http serve de base para a Rest e é uma abstração de um HTTP client. Por padrão ela irá utilizar o `axios` que é criado em `src/settings/http.js` , que usa como `baseURL` o valor da entrada do `.env` `VUE_APP_REST_BASE_URL`. 

### Rest

Para suprir os 4 pilares da gestão das entidades ela já conta com os métodos create, read, update e destroy, tendo ainda o método search / paginate para lidar com a pesquisa e paginação de dados.

{% hint style="info" %}
Para se adaptar à diferentes APIs existe em `src/settings/rest.js` duas funções que podem ser adaptadas para extrair os dados da resposta da requisição e passarem para o formato que o projeto espera
{% endhint %}

![](../.gitbook/assets/image%20%2816%29.png)


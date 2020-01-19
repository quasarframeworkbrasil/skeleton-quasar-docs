# Adicionando rotas

Um arquivo de rotas precisa simplesmente exportar uma função que retorne um array de rotas como a imagem abaixo.

![](../.gitbook/assets/image%20%288%29.png)

### Criando Rotas de CRUD

Quando se está criando uma quantidade grande de telas é comum repetir diversas vezes vários trechos e configurações. Para acelerar a criação é possível usar alguns helpers para a criação de rotas para CRUD, como pode ser visto no exemplo abaixo.

![](../.gitbook/assets/image%20%2820%29.png)

Este trecho acima cria um conjunto de 5 rotas devidamente configuradas. Para utilizar alguns recursos que estão pré-configurados no projeto é preciso configurar alguns detalhes no meta das rotas. A função `crud` já resolve isso e introduz o `scope` e o `namespace` no [`meta`](https://router.vuejs.org/guide/advanced/meta.html) das rotas, permitindo que sejam passadas configurações adicionais. O exemplo a seguir é um trecho do arquivo [`src/app/Util/routing.js`](https://github.com/quasarframeworkbrasil/skeleton/blob/master/src/app/Util/routing.js#L53).

![Trecho da fun&#xE7;&#xE3;o crud de src/app/Util/routing](../.gitbook/assets/image%20%289%29.png)




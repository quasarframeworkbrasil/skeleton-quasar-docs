---
description: >-
  Os schema são agrupamento de recursos que serão usados para prover
  comportamentos e estados para as regras de negócio
---

# Definindo o Schema

### Criando o Schema

Para criar um `schema` para a entidade `Action` vamos criar dentro da pasta `Schema` do domínio um arquivo `ActionSchema.js` \(`src/domains/Admin/Action/Schema/ActionSchema.js`\). Este arquivo deverá estender a classe `Schema`. O resultado inicial será um documento como o da imagem a seguir.

![](../.gitbook/assets/image%20%2824%29.png)

### Importando Recursos

Esta definição é a mais básica que podemos fazer para esta classe porque o método `construct` deve ser implementado mesmo nessa primeira versão. Além desse método vamos fazer mais algumas configurações, informando na estrutura da classe as propriedades: `domain`, `path` e `service`. 

![](../.gitbook/assets/image%20%282%29.png)

As propriedades estáticas `domain` e `path` são importados do `settings.js` que definimos em [Configurando o domínio](configurando-o-dominio.md) e a propriedade `service` é o arquivo `ActionService.js` que criamos em [Preparando o acesso à API](criando-o-service.md).

### Criando o Campo `name`

Com o nosso schema inciado vamos configurar os campos que serão usados pela entidade. Para isso vamos usar o método `addField` que deve ser chamado dentro do `construct`.

![](../.gitbook/assets/image%20%2817%29.png)

Na imagem acima declaramos que o nosso `schema` irá trabalhar com o campo `name`.  Por padrão um campo criado não é exibido na `table` e é exibido no `form` com uma largura que ocupa 100% da linha num campo de texto. O campo `primaryKey` é carregado de forma implícita em todos os filhos de `Schema`. Portanto, nossa classe está mapeando dois campos: `id` e `name`. Mais adiante veremos as configurações dos campos e tudo que podemos fazer com eles, além de outros recursos configuráveis nos nossos `schema`.




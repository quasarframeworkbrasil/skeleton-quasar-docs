---
description: >-
  Tudo o que você precisa saber e mais um pouco sobre como trabalhar com o
  projeto Skeleton da comunidade Quasar Framework Brasil
---

# Conceitos

A ideia do Skeleton é entregar uma experiência RAD \(Rapid Application Development\) centralizando operações rotineiras e deixando para o desenvolvedor apenas as regras de negócio. Atuando apenas na lógica do negócio, o desenvolvedor trabalha na configuração dos estados e comportamentos que serão exibidos na tela. Em seguida ele cria um `Controller Component` que irá passar essas configuração para o `Container Component`. Este por sua vez irá se comunicar com os `Specialist Components` para renderizar as telas. 

![](.gitbook/assets/image%20%2824%29.png)

## Quando é interessante usar essa metodologia?

Pelos nossos estudos e experiências a metodologia usada na construção do Skeleton tende à ser mais eficiente em aplicações que sejam painéis de controle com muitas e muitas telas com a mesma estrutura. O custo de criar um `Container Component` é relativamente alto e se a aplicação tiver telas muito diferentes em cada ambiente não vale à pena o investimento. Em contrapartida se a aplicação tiver dezenas de forms e tables no padrão que já é suportado a produtividade será absurdamente alta.

## Meu projeto vai ficar mais complexo?

A resposta franca é SIM. Em contrapartida existem alguns benefícios como:

* Simplificação da cadeia de produtiva \(não é preciso reescrever toda a lógica de gestão de estados, validação, e etc\);
* Centralização das mudanças, caso o Quasar sofra alguma modificação o seu código não será impactado, apenas os adaptadores que aplicam suas configurações aos componentes dele;
* Possibilidade de criar estruturas base que se repetem com frequência;
* Controle do projeto em cima de uma linguagem de programação e não em cima de templates ou dependência vital de um framework de UI.

## Utilizar esta metodologia engessa meu projeto?

Absolutamente NÃO. É possível ver em [Customizando Components](customizacao/customizando-components.md) que podemos criar componentes customizados, em [Customizando Views](customizacao/customizando-views.md) podemos ver como criar views totalmente customizados sem sequer fazer uso da estrutura dos domínios.

## Como posso conseguir suporte?

Estamos usando o nosso grupo no [Telegram](https://t.me/quasarframeworkbrasil) e as [issues do repositório](https://github.com/quasarframeworkbrasil/skeleton/issues) do Skeleton para tirar dúvidas e acolher críticas / sugestões.

`--`

> Bora começar a codar?!


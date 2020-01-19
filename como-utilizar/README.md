---
description: Descrição detalhada da estrutura básica montada
---

# Estrutura

## Visão Geral

Vamos conhecer a estrutura e entender o que muda em relação a um projeto [Quasar](https://quasar.dev/quasar-cli/cli-documentation/directory-structure) qualquer. A estrutura de pastas que vem por padrão no projeto pode ser vista abaixo.

```bash
src/
  ├── ¹app       # centralizad todo o código agnóstico
  ├── assets     # recursos dinâmicos (processado pelo webpack)
  ├── boot       # arquivos de inicialização
  ├── css        # definições de estilo (CSS/Stylus/Sass/..)
  ├── ¹domains   # lógica de negócio
  ├── ¹lang      # documentos para internacionalização
  ├── ¹modules   # principais módulos da aplicação
  ├── router     # [Vue Router]
  ├── ¹settings  # configurações primárias
  ├── statics    # pure static assets (directly copied)
  ├── store      # [Vuex Store]
  ├── ¹views     # arquivos .vue para a apresentação
```

{% hint style="info" %}
Os itens com ¹ não são padrão do [Quasar](https://quasar.dev/quasar-cli/cli-documentation/directory-structure)
{% endhint %}

Veremos então de forma discriminada qual a responsabilidade de cada diretório destes listados acima.

## Estrutura de Diretórios

As pastas `assets/`, `boot/`, `css/`, `router/`, `statics/` e `store/` são basicamente o que vem no [template padrão do Quasar](https://quasar.dev/quasar-cli/cli-documentation/directory-structure) e tem apenas alguns recursos básicos para preparar o projeto para a metodologia. Em `boot/`, por exemplo, temos todos os `boot files` necessários para inicializar a aplicação. Já em `css/` há um import para os estilos dos componentes base. Na pasta `store/` há uma base `Vuex Store` configurada para suprir necessidades primárias de um app desse tipo. A pasta `router/`, por sua vez,  tem muitas modificações em relação à original, principalmente em relação à sua organização interna. As pastas `components/` ,`layouts/` e `pages/` são apagadas por não serem usadas por padrão.

A seguir veremos cada diretório que é adicionado à uma instalação tradicional do Quasar. O router/ não está nessa lista, mas por entregar uma experiência muito diferente do usual podemos ver mais sobre ele em [Trabalhando com Routes](trabalhando-com-rotas.md).

### `app/`

Este diretório é o coração da estrutura que permite que haja toda a automatização que a metodologia entrega. Dentro dela é possível achar classes e arquivos que serão estendidos e utilizados para montar os fluxos de trabalho.

### `domains/`

Em domains vamos colocar nossas classes de Schema e Service, e todos os arquivos responsáveis por prover configurações para os componentes \(camada de apresentação em geral\). O Skeleton vem com alguns exemplos apenas para dar uma ideia da organização e do que é possível fazer, mas não há regras nesse ponto.

### `lang/`

Diretório que centraliza a parte de internacionalização. Nele é possível ver arquivos de mensagens padrão do sistema e métodos para gerenciar o idioma da aplicação.

### `modules/`

Nesta estrutura um `module` é o arcabouço básico de um tipo de visão que do aplicativo. Eles agregam arquivos de rotas e componentes para prover a base da apresentação à que se destinam. Por padrão o projeto possui dois leiautes: `Auth` e `Dashboard`. O `Auth` é para atender à todas as telas que são acessadas fora do painel de controle \(por exemplos, telas de login ou de criação de uma nova conta\). Já o `Dashboard` cobre a área administrativa que é exibida quando um usuário tem uma sessão ativa. Em [Compondo Modules](compondo-leiautes.md) é possível saber mais sobre o conteúdo deste diretório.

### `settings/`

No diretório settings temos arquivos que provêm configuração para quase todos os outros dessa lista. É nele que ficam declarados detalhes que vão desde como será feita a criação de um campo, como será alimentada a table após fazer um fetch até o\(s\) HTTP Client\(s\) que serão usados no projeto.

### `views/`

Todas as views são direcionadas para cá. Neste ponto será possível ver os arquivos `.vue` mapeados pelas rotas e seus componentes auxiliares \(caso seja necessário fazê-los\). Por padrão as visões são geralmente direcionadas para `Controller Components` e contam com um template bem enxuto, mas é possível personalizá-los para contextos específicos, veja mais sobre isso em [Customizando Components](../customizacao/customizando-components.md) e [Customizando Views](../customizacao/customizando-views.md).

> A seguir veremos detalhes sobre cada conteúdo que será adicionado em cada diretório destes afim de criar uma tela


---
description: Cada módulo é um ponto de partida de central para uma estrutura do projeto
---

# Module

Os módulos possuem os recursos base para renderizar a estrutura que será usada para montar todas as suas telas filhas. Para isso serão configurados componentes para fazer a apresentação, rotas, gerenciadores de estado e etc. A aplicação já possui dois módulos criados: Auth e Dashboard.

![](../.gitbook/assets/image%20%2821%29.png)

## Módulo Auth

Este módulo está destinado à dar suporte às telas que são acessadas sem ter uma sessão definida. Estamos falando de telas como a que é usada pra informar usuário e senha para iniciar uma sessão, a que é usada para criar um usuário ou ainda para alterar a senha que foi perdida. Nesse caso iríamos adicionar tudo o que fosse base para essas telas e então iríamos prosseguir com a construção de seus `Services`, `Schema` e `Views`. Inicialmente ele possui as pastas abaixo, mas pode ser alterado livremente com a finalidade de implementar todos os recursos que o projeto demandar.

### store

Gerencia apenas dois estados: `token` e `user`. O estado user é explorado com `getters` para compor informações das telas de outros módulos, por exemplo.

### helper

Possui funções que são usadas para validar permissão e permitir acesso à recursos como rotas e menus.

### router

Possui apenas a rota da tela de login, mas pode ser incrementado para abrigar os recursos que forem criados para administrar o acesso do usuário que não possui uma sessão.

## Módulo Dashboard

Os recursos necessários para configurar o painel de controle, que é a área protegida da aplicação ficarão nesse módulo. Ele conta com as pastas:

### store

Gerencia `transition`, `report`, `title` que são relacionados à interface.

### router

Integra todas as rotas de dominios que são usados para criar telas para o módulo.

### components

Possui componentes para renderizar o menu superior direito e o menu lateral  esquerdo \(drawer\).




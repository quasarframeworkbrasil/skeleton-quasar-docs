---
description: >-
  Esta sessão trata de um passo-a-passo para criação de um novo recurso dentro
  de um projeto já previamente instalado
---

# Começando

### Iniciar o modo de desenvolvimento

Para rodar o projeto podemos usar o [CLI do Quasar](https://quasar.dev/quasar-cli/cli-documentation/commands-list#dev) devidamente instalado ou [Docker](https://docs.docker.com/install).

Usando o [CLI do Quasar](https://quasar.dev/quasar-cli/cli-documentation/commands-list#dev) podemos fazer

```bash
quasar dev
```

Se a estação de trabalho tiver [Docker](https://docs.docker.com/install) + [Docker Compose](https://docs.docker.com/compose/install) é possível utilizar docker-compose para iniciar o modo de desenvolvimento usando

```bash
docker-compose up
```

### Começando os trabalhos

Depois de feita a instalação e de colocarmos o projeto em modo de desenvolvimento iremos implementar um novo recurso. O recurso que será criado será um cadastro simples de Categoria. O nome desse cadastro será `Category` , que poderia ser usado num cenário real para categorizar qualquer outro cadastro. Use o link abaixo para seguir para o próximo passo.

{% hint style="info" %}
O exemplo usará a entidade `Category` como referência daqui pra frente, mas sinta-se à vontade para criar o que for mais legal para você
{% endhint %}

{% page-ref page="iniciando-o-dominio.md" %}




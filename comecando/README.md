---
description: >-
  Este é um tutorial de poucos minutos que mostra um passo-a-passo de como criar
  um novo recurso dentro de um projeto já previamente instalado
---

# Começando com o Skeleton

## Iniciar o modo de desenvolvimento

Para rodar o projeto podemos usar o [CLI do Quasar](https://quasar.dev/quasar-cli/cli-documentation/commands-list#dev) ou [Docker](https://docs.docker.com/install).

### Quasar CLI

Se já tiver no seu ambiente o [CLI do Quasar](https://quasar.dev/quasar-cli/cli-documentation/commands-list#dev) devidamente instalado podemos usar o comando abaixo para iniciar o modo de desenvolvimento

```bash
quasar dev
```

### Docker Compose

Se a estação de trabalho tiver [Docker](https://docs.docker.com/install) + [Docker Compose](https://docs.docker.com/compose/install) é possível utilizar docker-compose para iniciar o modo de desenvolvimento usando

```bash
docker-compose up
```

### Status do Comando

Aguarde até ver no terminal uma saída como a da imagem abaixo. Neste ponto seu projeto estará pronto para iniciar os trabalhos.

![](../.gitbook/assets/image%20%2835%29.png)

## Começando os trabalhos

Acesse na barra de endereços do navegador a URL [`http://localhost:8080`](http://localhost:8080) e confira se aparece algo como a imagem abaixo.

![](../.gitbook/assets/image%20%2836%29.png)

Depois de feita a instalação e de colocarmos o projeto em modo de desenvolvimento iremos implementar um novo recurso. O recurso que será criado será um cadastro simples de Categoria. O nome da classe deste cadastro será `Category`  \(apenas para acompanhar o resto do código que está em inglês\), que poderia ser usado num cenário real para categorizar qualquer outro cadastro. Use o link abaixo para seguir para o próximo passo.

{% hint style="info" %}
O exemplo usará a entidade `Category` como referência daqui pra frente, mas sinta-se à vontade para criar o que for mais legal para você
{% endhint %}

{% page-ref page="iniciando-o-dominio.md" %}




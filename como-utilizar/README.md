---
description: Detailed description of the assembled basic structure
---

# Structure

## Overview

Let's get to know the structure and understand what changes in relation to any [Quasar](https://quasar.dev/quasar-cli/cli-documentation/directory-structure) project. The folder structure that comes standard in the project can be seen below.

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
Items with ¹ are not standard [Quasar](https://quasar.dev/quasar-cli/cli-documentation/directory-structure)
{% endhint %}

We will then see in a discriminated manner the responsibility of each directory listed above.

## Directory Structure

The `assets/`, `boot/`, `css/`, `router/`, `statics/` and `store/` folders are basically what comes in the [standard Quasar template](https://quasar.dev/quasar-cli/cli-documentation/directory-structure) and have only a few basic resources to prepare the project for the methodology. In`boot/`, for example, we have all the`boot files` needed to start the application. In`css/` there is an import for the styles of the base components. In the`store/` folder there is a`Vuex Store` base configured to supply the primary needs of such an app. The`router/`folder, in turn, has many modifications in relation to the original, mainly in relation to its internal organization. The`components/` ,`layouts/` and `pages/` folders are deleted because they are not used by default.

Next, we'll look at each directory that is added to a traditional Quasar installation. The router / is not on that list, but for delivering a very different experience than we can see more about it in [Working with Routes](trabalhando-com-rotas.md).

### `app/`

This directory is the heart of the structure that allows all the automation that the methodology delivers. Within it, you can find classes and files that will be extended and used to assemble workflows.

### `domains/`

In domains we will place our Schema and Service classes, and all files responsible for providing configurations for the components \(presentation layer in general\). Skeleton comes with some examples just to give you an idea of the organization and what is possible to do, but there are no rules at this point.

### `lang/`

Directory that centralizes the internationalization part. It is possible to view standard system message files and methods for managing the application language.

### `modules/`

In this structure, a`module`is the basic framework of a type of view that of the application. They aggregate route and component files to provide the basis for the presentation to which they are intended. By default the project has two layouts:`Auth` and`Dashboard`.`Auth`is for all screens that are accessed outside of the control panel \(for example, login or new account creation screens\). The`Dashboard`covers the administrative area that is displayed when a user has an active session. In [Componsing Modules](compondo-leiautes.md)  you can find out more about the contents of this directory.

### `settings/`

In the settings directory we have files that provide configuration for almost everyone else on this list. It is here that details are stated, ranging from how to create a field, how the table will be fed after fetching it to the HTTP Client \(s\) that will be used in the project.

### `views/`

All views are directed here. At this point, it will be possible to see the`.vue` files mapped by the routes and their auxiliary components \(if necessary\). By default the views are usually directed towards`Controller`Components and have a very lean template, but it is possible to customize them for specific contexts, see more about this in [Customizing Components](../customizacao/customizando-components.md) e [Customizing Views](../customizacao/customizando-views.md).

> Below we will see details about each content that will be added in each directory in order to create a screen


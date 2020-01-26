---
description: >-
  Nosso trabalho começa por definir o domínio do recurso com o qual iremos
  trabalhar
---

# Domains

Domínio é um termo complicado de se explicar. Tentando ver o significado da palavra no nosso idioma teremos algo que não é muito apropriado para a informática.

![resultado da pesquisa pela palavra dom&#xED;nio no google](../.gitbook/assets/image%20%2836%29.png)

Quando fazemos a mesma pesquisa em inglês os resultados dão uma mudada e começamos a nos aproximar do que é esperado para a informática

![resultado da pesquisa pela palavra domain no google](../.gitbook/assets/image%20%2839%29.png)

A definição acima `"a specified sphere of activity or knowledge"` é o que vou usar como referência para explicar o propósito da pasta `domain`. Se por acaso já tiver ouvido falar de Domain Driven Design \(DDD\) também vai dar uma mão na compreensão do termo.

O projeto trata domínios como um grupo de recursos que fazem sentido estarem agrupados. Não há uma necessidade física de estarem juntos, mas há uma certa familiaridade entre eles. O que está em cada domínio é geralmente cunhado como entidade ou `entity`. Então vamos agrupar nossas entidades em domínios para mapear nossas regras de negócio, estados e comportamentos. A representação das entidades na metodologia aplicada é o [`schema`](schema.md). Logo dentro da pasta domains teremos `schemes` e `services` à disposição dos componentes. Alguns recursos de suporte à eles também estarão disponíveis por lá como arquivos de rotas e de internacionalização, mas o foco dele é agrupar o que chamaremos de `business rules` \(`behaviours` & `states`\).




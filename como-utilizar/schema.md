---
description: >-
  O schema é a definição dos comportamentos e estados das nossas regras de
  negócio
---

# Schema

Ao definirmos um `schema` vamos informar quais campos serão usados, quais eventos estes campos irão manipular, os componentes que serão usados nos formulários por cada um dos campos e como será exibida a tabela que carrega os dados relacionados à entidade que o `schema` representa. Além dos campos também as ações \(botões\) disponíveis e comportamentos dos componentes serão mapeados.

Resumidamente com os `schemes` serão criados todos os `forms` e `tables` que serão renderizados. O objetivo de um `schema` é criar os artefatos necessários para que os componentes de criação de formulários e tabelas tenham dados suficientes para trabalhar.

Para gerenciar os campos temos dois métodos:

* `addField`: adiciona um novo campo ao `schema`;
* `getField`: seleciona um campo que já faz parte do `schema` para ser manipulado;

Para manipular as propriedades relacionadas à table:

* `fieldTableWidth`: define a largura do campo na tabela;
* `fieldTableShow`: define se o campo será visível ou não na tabela;
* `fieldTableWhere`: determina se o campo será exibido na pesquisa lateral da tabela;
* `fieldTableFilter`: define se o campo será usado como um filtro fixo na parte superior da tabela;
* `fieldTableRequired`: especifica se é possível ocultar o campo;
* `fieldTableName`: permite alterar o nome da propriedade que está sendo acessada na lista;
* `fieldTableAlign`: configura o alinhamento na tabela;
* `fieldTableSortable`: determina se é possível aplicar ordenação através desse campo;
* `fieldTableFormat`: função que será usada para formatar os valores da coluna antes de exibir na linha;
* `fieldTableOrder`: permite configurar a ordenação do campo entre os campos da tabela;

Para determinar os componentes que serão usados pelos campos temos:

* `fieldIsInput`: determina que o campo usará um componente de texto padrão;
* `fieldIsNumber`: ;
* `fieldIsPassword`: ;
* `fieldIsEmail`: ;
* `fieldIsText`: ;
* `fieldIsCheckbox`: ;
* `fieldIsRadio`: ;
* `fieldIsSelect`: ;
* `fieldIsSelectRemote`: ;
* `fieldIsSelectRemoteMultiple`: ;
* `fieldIsToggle`: ;
* `fieldIsDate`: ;
* `fieldIsDatetime`: ;
* `fieldIsInputPlan`: ;
* `fieldIsArray`: ;
* `fieldIsCurrency`: ;
* `fieldIsButton`: ;

Há ainda algumas macros disponíveis para configurar alguns campos:

* `fieldAsPrimaryKey`: ;
* `fieldAsZip`: ;
* `fieldAsPhone`: ;
* `fieldAsCell`: ;
* `fieldAsMasked`: ;

Para manipular propriedades relacionadas ao form temos os seguintes métodos:

* `fieldFormWidth`: ;
* `fieldFormDisabled`: ;
* `fieldFormHeight`: ;
* `fieldFormHidden`: ;
* `fieldFormName`: ;
* `fieldFormAutofocus`: ;
* `fieldFormDefaultValue`: ;
* `fieldFormErrorHide`: ;
* `fieldFormErrorShow`: ;
* `fieldFormUpperCase`: ;
* `fieldFormPlaceholder`: ;
* `fieldFormOrder`: ;

Para tratar sobre validação temos os seguintes métodos:

* `validationAdd`: ;
* `validationAs`: ;
* `validationRequired`: ;
* `validationRequiredIf`: ;
* `validationRequiredWhen`: ;
* `validationRequiredUnless`: ;
* `validationMinLength`: ;
* `validationMaxLength`: ;
* `validationMinValue`: ;
* `validationMaxValue`: ;
* `validationBetween`: ;
* `validationAlpha`: ;
* `validationAlphaNum`: ;
* `validationNumeric`: ;
* `validationInteger`: ;
* `validationDecimal`: ;
* `validationEmail`: ;
* `validationIpAddress`: ;
* `validationMacAddress`: ;
* `validationPassword`: ;
* `validationSameAs`: ;
* `validationUrl`: ;
* `validationOr`: ;
* `validationAnd`: ;
* `validationNot`: ;
* `validationWithParams`: ;
* `validationClear`: ;
* `validationRemove`: ;




---
description: >-
  O schema é a definição dos comportamentos e estados das nossas regras de
  negócio
---

# Schema

Ao definirmos um `schema` vamos informar quais campos serão usados, quais eventos estes campos irão manipular, os componentes que serão usados nos formulários por cada um dos campos e como será exibida a tabela que carrega os dados relacionados à entidade que o `schema` representa. Além dos campos também as ações \(botões\) disponíveis e comportamentos dos componentes serão mapeados.

Resumidamente com os `schemes` serão criados todos os `forms` e `tables` que serão renderizados. O objetivo de um `schema` é criar os artefatos necessários para que os componentes de criação de formulários e tabelas tenham dados suficientes para trabalhar.

Para gerenciar os campos temos dois métodos:

* `addField`: ;
* `getField`: ;

Para determinar os componentes que serão usados pelos campos temos:

* `fieldIsInput`: ;
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

Para manipular os campos com macros tempos as seguintes macros:

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

Para manipular as propriedades relacionadas à table:

* `fieldTableWidth`: ;
* `fieldTableShow`: ;
* `fieldTableWhere`: ;
* `fieldTableFilter`: ;
* `fieldTableRequired`: ;
* `fieldTableName`: ;
* `fieldTableAlign`: ;
* `fieldTableSortable`: ;
* `fieldTableFormat`: ;
* `fieldTableOrder`: ;




---
description: The schema is the definition of the behaviors and states of our business rules
---

# Schema

When defining a`schema`we will inform which fields will be used, which events these fields will handle, the components that will be used in the forms for each of the fields and how the table that carries the data related to the entity that the`schema`represents will be displayed. In addition to the fields, the available actions \(buttons\) and component behaviors will also be mapped.

Briefly with the`schemes`, all`forms` and `tables` that will be rendered will be created. The purpose of a`schema`is to create the necessary artifacts so that the components of creating forms and tables have enough data to work with.

To manage the fields we have two methods:

* `addField`: adds a new field to the`schema`;
* `getField`: select a field that is already part of the `schema`to be manipulated;

To manipulate table-related properties:

* `fieldTableWidth`: defines the width of the field in the table;
* `fieldTableShow`: defines whether the field will be visible or not in the table;
* `fieldTableWhere`: determines whether the field will be displayed in the table side search;
* `fieldTableFilter`: defines whether the field will be used as a fixed filter at the top of the table;
* `fieldTableRequired`: specifies whether it is possible to hide the field;
* `fieldTableName`: allows changing the name of the property being accessed in the list;
* `fieldTableAlign`: configure the alignment in the table;
* `fieldTableSortable`: determines whether it is possible to apply sorting through that field;
* `fieldTableFormat`: function that will be used to format column values before displaying on the line;
* `fieldTableOrder`: it allows configuring the field ordering between the table fields;

To determine the components that will be used by the fields we have:

* `fieldIsInput`: determines that the field will use a standard text component;
* `fieldIsNumber`: determines that the field will use a numeric type input component;
* `fieldIsPassword`: determines that the field will use an input component of type password with hashes in the characters;
* `fieldIsEmail`: determines that the field will use an e-mail input component, according to the validations created for it;
* `fieldIsText`: determines that the field will use a textarea component similar to a notepad;
* `fieldIsCheckbox`: determines that the field will use a checkbox component;
* `fieldIsRadio`: determines that the field will use a radio button component, passing the values through a parameter;
* `fieldIsSelect`: ;
* `fieldIsSelectRemote`: ;
* `fieldIsSelectRemoteMultiple`: ;
* `fieldIsToggle`: ;
* `fieldIsDate`: determines that the field will use a Data component, the settings must be passed via an attribute;
* `fieldIsDatetime`: determines that the field will use a Date and Time component, the settings must be passed via attribute;
* `fieldIsInputPlan`: ;
* `fieldIsArray`: determines that the field will use a customized CRUD component, its functionality is the same as that of a crud;
* `fieldIsCurrency`: ;
* `fieldIsButton`: ;

There are still some macros available to configure some fields:

* `fieldAsPrimaryKey`: ;
* `fieldAsZip`: ;
* `fieldAsPhone`: ;
* `fieldAsCell`: ;
* `fieldAsMasked`: ;

To manipulate properties related to the form we have the following methods:

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

To deal with validation we have the following methods:

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


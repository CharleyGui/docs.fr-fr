---
title: Règles du langage de style de code
description: En savoir plus sur les différentes règles de style de code pour l’utilisation des constructions de langage C# et Visual Basic.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
- language rules
- EditorConfig language conventions
ms.openlocfilehash: 2aa2261534363f1da6a2109f092e08d210ebd915
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957973"
---
# <a name="language-rules"></a>Règles de langage

Les règles de langage de style de code affectent la manière dont les différentes constructions de langages de programmation .NET, par exemple les modificateurs et les parenthèses, sont utilisées. Les règles sont classées dans les catégories suivantes :

- [Règles de style .net](#net-style-rules): règles qui s’appliquent à la fois à C# et Visual Basic. Les noms des options EditorConfig pour ces règles commencent par le `dotnet_style_` préfixe.
- [Règles de style c#](#c-style-rules): règles spécifiques au langage c# uniquement. Les noms des options EditorConfig pour ces règles commencent par le `csharp_style_` préfixe.
- [Règles de style de Visual Basic](#visual-basic-style-rules): règles spécifiques à Visual BSIC Language uniquement. Les noms des options EditorConfig pour ces règles commencent par le `visual_basic_style_` préfixe.

## <a name="option-format"></a>Format d’option

Les options des règles de langue peuvent être spécifiées dans un fichier EditorConfig au format suivant :

`option_name = value` (Visual Studio 2019 version 16,9 Preview 2 et versions ultérieures)

ou

`option_name = value:severity`

- **Valeur**

  Pour chaque règle de langue, vous spécifiez une valeur qui définit si le style doit être préféré ou pas. De nombreuses règles acceptent la valeur `true` (préférer ce style) ou `false` (ne pas préférer ce style). D’autres règles acceptent des valeurs telles que `when_on_single_line` ou `never` .

- **Gravité** (facultatif dans Visual Studio 2019 version 16,9 Preview 2 et versions ultérieures)

  La deuxième partie de la règle spécifie le [niveau de gravité](../configuration-options.md#severity-level) de la règle. Lorsqu’il est spécifié de cette manière, le paramètre de gravité est respecté uniquement dans les IDE de développement, tels que Visual Studio. Elle n’est *pas* respectée lors de la génération.

  Pour appliquer des règles de style de code au moment de la génération, définissez la gravité en utilisant la syntaxe de configuration de gravité basée sur l’ID de règle pour les analyseurs à la place. La syntaxe prend la forme `dotnet_diagnostic.<rule ID>.severity = <severity>` , par exemple, `dotnet_diagnostic.IDE0040.severity = silent` . Pour plus d’informations, consultez [niveau de gravité](../configuration-options.md#severity-level).

> [!TIP]
>
> À compter de Visual Studio 2019 version 16,3, vous pouvez configurer des règles de style de code à partir du menu de l’ampoule [actions rapides](/visualstudio/ide/quick-actions) après une violation de style. Pour plus d’informations, consultez [configurer automatiquement les styles de code dans Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).

## <a name="net-style-rules"></a>Règles de style .NET

Les règles de style mentionnées dans cette section s’appliquent aussi bien au langage C# qu’au langage Visual Basic.

- [qualificateurs’This. 'et’me. '](ide0003-ide0009.md)
  - [dotnet_style_qualification_for_field](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [dotnet_style_qualification_for_property](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [dotnet_style_qualification_for_method](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [dotnet_style_qualification_for_event](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [Mots clés de langage à la place des noms de type Framework pour les références de type](ide0049.md)
  - [dotnet_style_predefined_type_for_locals_parameters_members](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [dotnet_style_predefined_type_for_member_access](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [Préférences relatives aux modificateurs](modifier-preferences.md#net-modifier-preferences)
  - [dotnet_style_require_accessibility_modifiers](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [csharp_preferred_modifier_order](ide0036.md#csharp_preferred_modifier_order)
  - [visual_basic_preferred_modifier_order](ide0036.md#visual_basic_preferred_modifier_order)
  - [dotnet_style_readonly_field](ide0044.md#dotnet_style_readonly_field)
- [Préférences relatives aux parenthèses](ide0047-ide0048.md)
  - [dotnet_style_parentheses_in_arithmetic_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [dotnet_style_parentheses_in_relational_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [dotnet_style_parentheses_in_other_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [dotnet_style_parentheses_in_other_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [Préférences au niveau des expressions](expression-level-preferences.md#net-expression-level-preferences)
  - [dotnet_style_object_initializer](ide0017.md#dotnet_style_object_initializer)
  - [dotnet_style_collection_initializer](ide0028.md#dotnet_style_collection_initializer)
  - [dotnet_style_explicit_tuple_names](ide0033.md#dotnet_style_explicit_tuple_names)
  - [dotnet_style_prefer_inferred_tuple_names](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [dotnet_style_prefer_inferred_anonymous_type_member_names](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [dotnet_style_prefer_auto_properties](ide0032.md#dotnet_style_prefer_auto_properties)
  - [dotnet_style_prefer_conditional_expression_over_assignment](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [dotnet_style_prefer_conditional_expression_over_return](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [dotnet_style_prefer_compound_assignment](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [dotnet_style_prefer_simplified_interpolation](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [dotnet_style_prefer_simplified_boolean_expressions](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - [Ajouter des cas manquants à l’instruction switch](ide0010.md) : cette règle n’a pas d’option de style code.
  - [Convertir un type anonyme en Tuple](ide0050.md) : cette règle n’a pas d’option de style de code.
  - [Utilisez’System. code de hachage. combine'](ide0070.md) -cette règle n’a pas d’option de style de code.
  - [Convertir « typeof » en « nameof »](ide0082.md) -cette règle n’a pas d’option de style de code.
- [Préférences de vérification de valeur null](null-checking-preferences.md#net-null-checking-preferences)
  - [dotnet_style_coalesce_expression](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [dotnet_style_null_propagation](ide0031.md#dotnet_style_null_propagation)
  - [dotnet_style_prefer_is_null_check_over_reference_equality_method](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [Préférences d'en-tête de fichier](ide0073.md)
  - [file_header_template](ide0073.md#file_header_template)

## <a name="c-style-rules"></a>Règles de style C#

Les règles de style de cette section s’appliquent uniquement au langage C#.

- [Préférences’var'](ide0007-ide0008.md)
  - [csharp_style_var_for_built_in_types](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [csharp_style_var_when_type_is_apparent](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [csharp_style_var_elsewhere](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [Membres expression-bodied](expression-bodied-members.md)
  - [csharp_style_expression_bodied_methods](ide0022.md#csharp_style_expression_bodied_methods)
  - [csharp_style_expression_bodied_constructors](ide0021.md#csharp_style_expression_bodied_constructors)
  - [csharp_style_expression_bodied_operators](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [csharp_style_expression_bodied_properties](ide0025.md#csharp_style_expression_bodied_properties)
  - [csharp_style_expression_bodied_indexers](ide0026.md#csharp_style_expression_bodied_indexers)
  - [csharp_style_expression_bodied_accessors](ide0027.md#csharp_style_expression_bodied_accessors)
  - [csharp_style_expression_bodied_lambdas](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [csharp_style_expression_bodied_local_functions](ide0061.md#csharp_style_expression_bodied_local_functions)
- [Préférences correspondants au modèle](pattern-matching-preferences.md)
  - [csharp_style_pattern_matching_over_is_with_cast_check](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [csharp_style_pattern_matching_over_as_with_null_check](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [csharp_style_prefer_switch_expression](ide0066.md#csharp_style_prefer_switch_expression)
  - [csharp_style_prefer_pattern_matching](ide0078.md#csharp_style_prefer_pattern_matching)
  - [csharp_style_prefer_not_pattern](ide0083.md#csharp_style_prefer_not_pattern)
- [Préférences au niveau des expressions](expression-level-preferences.md#c-expression-level-preferences)
  - [csharp_style_inlined_variable_declaration](ide0018.md#csharp_style_inlined_variable_declaration)
  - [csharp_prefer_simple_default_expression](ide0034.md#csharp_prefer_simple_default_expression)
  - [csharp_style_pattern_local_over_anonymous_function](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [csharp_style_deconstructed_variable_declaration](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [csharp_style_prefer_index_operator](ide0056.md#csharp_style_prefer_index_operator)
  - [csharp_style_prefer_range_operator](ide0057.md#csharp_style_prefer_range_operator)
  - [csharp_style_implicit_object_creation_when_type_is_apparent](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - [Ajouter des cas manquants pour changer l’expression](ide0072.md) -cette règle n’a pas d’option de style de code.
- [Préférences de vérification de la valeur « null »](null-checking-preferences.md#c-null-checking-preferences)
  - [csharp_style_throw_expression](ide0016.md#csharp_style_throw_expression)
  - [csharp_style_conditional_delegate_call](ide1005.md#csharp_style_conditional_delegate_call)
- [Préférences relatives aux blocs de code](code-block-preferences.md)
  - [csharp_prefer_braces](ide0011.md#csharp_prefer_braces)
  - [csharp_prefer_simple_using_statement](ide0063.md#csharp_prefer_simple_using_statement)
- [préférences de directive’Using'](ide0065.md)
  - [csharp_using_directive_placement](ide0065.md#csharp_using_directive_placement)
- [Préférences relatives aux modificateurs](modifier-preferences.md#c-modifier-preferences)
  - [csharp_prefer_static_local_function](ide0062.md#csharp_prefer_static_local_function)
  - [Rendre les champs de struct accessibles en écriture](ide0064.md) : cette règle n’a pas d’option de style de code.

## <a name="visual-basic-style-rules"></a>Règles de style de Visual Basic

Les règles de style de cette section s’appliquent uniquement à Visual Basic langage.

- [Préférences correspondants au modèle](pattern-matching-preferences.md)
  - [visual_basic_style_prefer_isnot_expression](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a>Voir aussi

- [Règles de code inutiles](unnecessary-code-rules.md)
- [Règles de mise en forme](formatting-rules.md)
- [Règles d’affectation des noms](naming-rules.md)
- [Référence des règles de style de code .NET](index.md)

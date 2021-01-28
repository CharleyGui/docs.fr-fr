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
# <a name="language-rules"></a><span data-ttu-id="81445-103">Règles de langage</span><span class="sxs-lookup"><span data-stu-id="81445-103">Language rules</span></span>

<span data-ttu-id="81445-104">Les règles de langage de style de code affectent la manière dont les différentes constructions de langages de programmation .NET, par exemple les modificateurs et les parenthèses, sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="81445-104">Code style language rules affect how various constructs of .NET programming languages, for example, modifiers and parentheses, are used.</span></span> <span data-ttu-id="81445-105">Les règles sont classées dans les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="81445-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="81445-106">[Règles de style .net](#net-style-rules): règles qui s’appliquent à la fois à C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="81445-106">[.NET style rules](#net-style-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="81445-107">Les noms des options EditorConfig pour ces règles commencent par le `dotnet_style_` préfixe.</span><span class="sxs-lookup"><span data-stu-id="81445-107">The EditorConfig option names for these rules start with `dotnet_style_` prefix.</span></span>
- <span data-ttu-id="81445-108">[Règles de style c#](#c-style-rules): règles spécifiques au langage c# uniquement.</span><span class="sxs-lookup"><span data-stu-id="81445-108">[C# style rules](#c-style-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="81445-109">Les noms des options EditorConfig pour ces règles commencent par le `csharp_style_` préfixe.</span><span class="sxs-lookup"><span data-stu-id="81445-109">The EditorConfig option names for these rules start with `csharp_style_` prefix.</span></span>
- <span data-ttu-id="81445-110">[Règles de style de Visual Basic](#visual-basic-style-rules): règles spécifiques à Visual BSIC Language uniquement.</span><span class="sxs-lookup"><span data-stu-id="81445-110">[Visual Basic style rules](#visual-basic-style-rules): Rules that are specific to Visual Bsic language only.</span></span> <span data-ttu-id="81445-111">Les noms des options EditorConfig pour ces règles commencent par le `visual_basic_style_` préfixe.</span><span class="sxs-lookup"><span data-stu-id="81445-111">The EditorConfig option names for these rules start with `visual_basic_style_` prefix.</span></span>

## <a name="option-format"></a><span data-ttu-id="81445-112">Format d’option</span><span class="sxs-lookup"><span data-stu-id="81445-112">Option format</span></span>

<span data-ttu-id="81445-113">Les options des règles de langue peuvent être spécifiées dans un fichier EditorConfig au format suivant :</span><span class="sxs-lookup"><span data-stu-id="81445-113">Options for language rules can be specified in an EditorConfig file with the following format:</span></span>

<span data-ttu-id="81445-114">`option_name = value` (Visual Studio 2019 version 16,9 Preview 2 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="81445-114">`option_name = value` (Visual Studio 2019 version 16.9 Preview 2 and later)</span></span>

<span data-ttu-id="81445-115">ou</span><span class="sxs-lookup"><span data-stu-id="81445-115">or</span></span>

`option_name = value:severity`

- <span data-ttu-id="81445-116">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="81445-116">**Value**</span></span>

  <span data-ttu-id="81445-117">Pour chaque règle de langue, vous spécifiez une valeur qui définit si le style doit être préféré ou pas.</span><span class="sxs-lookup"><span data-stu-id="81445-117">For each language rule, you specify a value that defines if or when to prefer the style.</span></span> <span data-ttu-id="81445-118">De nombreuses règles acceptent la valeur `true` (préférer ce style) ou `false` (ne pas préférer ce style).</span><span class="sxs-lookup"><span data-stu-id="81445-118">Many rules accept a value of `true` (prefer this style) or `false` (do not prefer this style).</span></span> <span data-ttu-id="81445-119">D’autres règles acceptent des valeurs telles que `when_on_single_line` ou `never` .</span><span class="sxs-lookup"><span data-stu-id="81445-119">Other rules accept values such as `when_on_single_line` or `never`.</span></span>

- <span data-ttu-id="81445-120">**Gravité** (facultatif dans Visual Studio 2019 version 16,9 Preview 2 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="81445-120">**Severity** (optional in Visual Studio 2019 version 16.9 Preview 2 and later versions)</span></span>

  <span data-ttu-id="81445-121">La deuxième partie de la règle spécifie le [niveau de gravité](../configuration-options.md#severity-level) de la règle.</span><span class="sxs-lookup"><span data-stu-id="81445-121">The second part of the rule specifies the [severity level](../configuration-options.md#severity-level) for the rule.</span></span> <span data-ttu-id="81445-122">Lorsqu’il est spécifié de cette manière, le paramètre de gravité est respecté uniquement dans les IDE de développement, tels que Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81445-122">When specified in this way, the severity setting is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="81445-123">Elle n’est *pas* respectée lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="81445-123">It is *not* respected during build.</span></span>

  <span data-ttu-id="81445-124">Pour appliquer des règles de style de code au moment de la génération, définissez la gravité en utilisant la syntaxe de configuration de gravité basée sur l’ID de règle pour les analyseurs à la place.</span><span class="sxs-lookup"><span data-stu-id="81445-124">To enforce code style rules at build time, set the severity by using the rule ID-based severity configuration syntax for analyzers instead.</span></span> <span data-ttu-id="81445-125">La syntaxe prend la forme `dotnet_diagnostic.<rule ID>.severity = <severity>` , par exemple, `dotnet_diagnostic.IDE0040.severity = silent` .</span><span class="sxs-lookup"><span data-stu-id="81445-125">The syntax takes the form `dotnet_diagnostic.<rule ID>.severity = <severity>`, for example, `dotnet_diagnostic.IDE0040.severity = silent`.</span></span> <span data-ttu-id="81445-126">Pour plus d’informations, consultez [niveau de gravité](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="81445-126">For more information, see [severity level](../configuration-options.md#severity-level).</span></span>

> [!TIP]
>
> <span data-ttu-id="81445-127">À compter de Visual Studio 2019 version 16,3, vous pouvez configurer des règles de style de code à partir du menu de l’ampoule [actions rapides](/visualstudio/ide/quick-actions) après une violation de style.</span><span class="sxs-lookup"><span data-stu-id="81445-127">Starting in Visual Studio 2019 version 16.3, you can configure code style rules from the [Quick Actions](/visualstudio/ide/quick-actions) light bulb menu after a style violation occurs.</span></span> <span data-ttu-id="81445-128">Pour plus d’informations, consultez [configurer automatiquement les styles de code dans Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="81445-128">For more information, see [Automatically configure code styles in Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).</span></span>

## <a name="net-style-rules"></a><span data-ttu-id="81445-129">Règles de style .NET</span><span class="sxs-lookup"><span data-stu-id="81445-129">.NET style rules</span></span>

<span data-ttu-id="81445-130">Les règles de style mentionnées dans cette section s’appliquent aussi bien au langage C# qu’au langage Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="81445-130">The style rules in this section are applicable to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="81445-131">qualificateurs’This. 'et’me. '</span><span class="sxs-lookup"><span data-stu-id="81445-131">'this.' and 'Me.' qualifiers</span></span>](ide0003-ide0009.md)
  - [<span data-ttu-id="81445-132">dotnet_style_qualification_for_field</span><span class="sxs-lookup"><span data-stu-id="81445-132">dotnet_style_qualification_for_field</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [<span data-ttu-id="81445-133">dotnet_style_qualification_for_property</span><span class="sxs-lookup"><span data-stu-id="81445-133">dotnet_style_qualification_for_property</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [<span data-ttu-id="81445-134">dotnet_style_qualification_for_method</span><span class="sxs-lookup"><span data-stu-id="81445-134">dotnet_style_qualification_for_method</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [<span data-ttu-id="81445-135">dotnet_style_qualification_for_event</span><span class="sxs-lookup"><span data-stu-id="81445-135">dotnet_style_qualification_for_event</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [<span data-ttu-id="81445-136">Mots clés de langage à la place des noms de type Framework pour les références de type</span><span class="sxs-lookup"><span data-stu-id="81445-136">Language keywords instead of framework type names for type references</span></span>](ide0049.md)
  - [<span data-ttu-id="81445-137">dotnet_style_predefined_type_for_locals_parameters_members</span><span class="sxs-lookup"><span data-stu-id="81445-137">dotnet_style_predefined_type_for_locals_parameters_members</span></span>](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [<span data-ttu-id="81445-138">dotnet_style_predefined_type_for_member_access</span><span class="sxs-lookup"><span data-stu-id="81445-138">dotnet_style_predefined_type_for_member_access</span></span>](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [<span data-ttu-id="81445-139">Préférences relatives aux modificateurs</span><span class="sxs-lookup"><span data-stu-id="81445-139">Modifier preferences</span></span>](modifier-preferences.md#net-modifier-preferences)
  - [<span data-ttu-id="81445-140">dotnet_style_require_accessibility_modifiers</span><span class="sxs-lookup"><span data-stu-id="81445-140">dotnet_style_require_accessibility_modifiers</span></span>](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [<span data-ttu-id="81445-141">csharp_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="81445-141">csharp_preferred_modifier_order</span></span>](ide0036.md#csharp_preferred_modifier_order)
  - [<span data-ttu-id="81445-142">visual_basic_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="81445-142">visual_basic_preferred_modifier_order</span></span>](ide0036.md#visual_basic_preferred_modifier_order)
  - [<span data-ttu-id="81445-143">dotnet_style_readonly_field</span><span class="sxs-lookup"><span data-stu-id="81445-143">dotnet_style_readonly_field</span></span>](ide0044.md#dotnet_style_readonly_field)
- [<span data-ttu-id="81445-144">Préférences relatives aux parenthèses</span><span class="sxs-lookup"><span data-stu-id="81445-144">Parentheses preferences</span></span>](ide0047-ide0048.md)
  - [<span data-ttu-id="81445-145">dotnet_style_parentheses_in_arithmetic_binary_operators</span><span class="sxs-lookup"><span data-stu-id="81445-145">dotnet_style_parentheses_in_arithmetic_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [<span data-ttu-id="81445-146">dotnet_style_parentheses_in_relational_binary_operators</span><span class="sxs-lookup"><span data-stu-id="81445-146">dotnet_style_parentheses_in_relational_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [<span data-ttu-id="81445-147">dotnet_style_parentheses_in_other_binary_operators</span><span class="sxs-lookup"><span data-stu-id="81445-147">dotnet_style_parentheses_in_other_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [<span data-ttu-id="81445-148">dotnet_style_parentheses_in_other_operators</span><span class="sxs-lookup"><span data-stu-id="81445-148">dotnet_style_parentheses_in_other_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [<span data-ttu-id="81445-149">Préférences au niveau des expressions</span><span class="sxs-lookup"><span data-stu-id="81445-149">Expression-level preferences</span></span>](expression-level-preferences.md#net-expression-level-preferences)
  - [<span data-ttu-id="81445-150">dotnet_style_object_initializer</span><span class="sxs-lookup"><span data-stu-id="81445-150">dotnet_style_object_initializer</span></span>](ide0017.md#dotnet_style_object_initializer)
  - [<span data-ttu-id="81445-151">dotnet_style_collection_initializer</span><span class="sxs-lookup"><span data-stu-id="81445-151">dotnet_style_collection_initializer</span></span>](ide0028.md#dotnet_style_collection_initializer)
  - [<span data-ttu-id="81445-152">dotnet_style_explicit_tuple_names</span><span class="sxs-lookup"><span data-stu-id="81445-152">dotnet_style_explicit_tuple_names</span></span>](ide0033.md#dotnet_style_explicit_tuple_names)
  - [<span data-ttu-id="81445-153">dotnet_style_prefer_inferred_tuple_names</span><span class="sxs-lookup"><span data-stu-id="81445-153">dotnet_style_prefer_inferred_tuple_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [<span data-ttu-id="81445-154">dotnet_style_prefer_inferred_anonymous_type_member_names</span><span class="sxs-lookup"><span data-stu-id="81445-154">dotnet_style_prefer_inferred_anonymous_type_member_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [<span data-ttu-id="81445-155">dotnet_style_prefer_auto_properties</span><span class="sxs-lookup"><span data-stu-id="81445-155">dotnet_style_prefer_auto_properties</span></span>](ide0032.md#dotnet_style_prefer_auto_properties)
  - [<span data-ttu-id="81445-156">dotnet_style_prefer_conditional_expression_over_assignment</span><span class="sxs-lookup"><span data-stu-id="81445-156">dotnet_style_prefer_conditional_expression_over_assignment</span></span>](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [<span data-ttu-id="81445-157">dotnet_style_prefer_conditional_expression_over_return</span><span class="sxs-lookup"><span data-stu-id="81445-157">dotnet_style_prefer_conditional_expression_over_return</span></span>](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [<span data-ttu-id="81445-158">dotnet_style_prefer_compound_assignment</span><span class="sxs-lookup"><span data-stu-id="81445-158">dotnet_style_prefer_compound_assignment</span></span>](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [<span data-ttu-id="81445-159">dotnet_style_prefer_simplified_interpolation</span><span class="sxs-lookup"><span data-stu-id="81445-159">dotnet_style_prefer_simplified_interpolation</span></span>](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [<span data-ttu-id="81445-160">dotnet_style_prefer_simplified_boolean_expressions</span><span class="sxs-lookup"><span data-stu-id="81445-160">dotnet_style_prefer_simplified_boolean_expressions</span></span>](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - <span data-ttu-id="81445-161">[Ajouter des cas manquants à l’instruction switch](ide0010.md) : cette règle n’a pas d’option de style code.</span><span class="sxs-lookup"><span data-stu-id="81445-161">[Add missing cases to switch statement](ide0010.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="81445-162">[Convertir un type anonyme en Tuple](ide0050.md) : cette règle n’a pas d’option de style de code.</span><span class="sxs-lookup"><span data-stu-id="81445-162">[Convert anonymous type to tuple](ide0050.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="81445-163">[Utilisez’System. code de hachage. combine'](ide0070.md) -cette règle n’a pas d’option de style de code.</span><span class="sxs-lookup"><span data-stu-id="81445-163">[Use 'System.HashCode.Combine'](ide0070.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="81445-164">[Convertir « typeof » en « nameof »](ide0082.md) -cette règle n’a pas d’option de style de code.</span><span class="sxs-lookup"><span data-stu-id="81445-164">[Convert 'typeof' to 'nameof'](ide0082.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="81445-165">Préférences de vérification de valeur null</span><span class="sxs-lookup"><span data-stu-id="81445-165">Null-checking preferences</span></span>](null-checking-preferences.md#net-null-checking-preferences)
  - [<span data-ttu-id="81445-166">dotnet_style_coalesce_expression</span><span class="sxs-lookup"><span data-stu-id="81445-166">dotnet_style_coalesce_expression</span></span>](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [<span data-ttu-id="81445-167">dotnet_style_null_propagation</span><span class="sxs-lookup"><span data-stu-id="81445-167">dotnet_style_null_propagation</span></span>](ide0031.md#dotnet_style_null_propagation)
  - [<span data-ttu-id="81445-168">dotnet_style_prefer_is_null_check_over_reference_equality_method</span><span class="sxs-lookup"><span data-stu-id="81445-168">dotnet_style_prefer_is_null_check_over_reference_equality_method</span></span>](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [<span data-ttu-id="81445-169">Préférences d'en-tête de fichier</span><span class="sxs-lookup"><span data-stu-id="81445-169">File header preferences</span></span>](ide0073.md)
  - [<span data-ttu-id="81445-170">file_header_template</span><span class="sxs-lookup"><span data-stu-id="81445-170">file_header_template</span></span>](ide0073.md#file_header_template)

## <a name="c-style-rules"></a><span data-ttu-id="81445-171">Règles de style C#</span><span class="sxs-lookup"><span data-stu-id="81445-171">C# style rules</span></span>

<span data-ttu-id="81445-172">Les règles de style de cette section s’appliquent uniquement au langage C#.</span><span class="sxs-lookup"><span data-stu-id="81445-172">The style rules in this section are applicable to C# language only.</span></span>

- [<span data-ttu-id="81445-173">Préférences’var'</span><span class="sxs-lookup"><span data-stu-id="81445-173">'var' preferences</span></span>](ide0007-ide0008.md)
  - [<span data-ttu-id="81445-174">csharp_style_var_for_built_in_types</span><span class="sxs-lookup"><span data-stu-id="81445-174">csharp_style_var_for_built_in_types</span></span>](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [<span data-ttu-id="81445-175">csharp_style_var_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="81445-175">csharp_style_var_when_type_is_apparent</span></span>](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [<span data-ttu-id="81445-176">csharp_style_var_elsewhere</span><span class="sxs-lookup"><span data-stu-id="81445-176">csharp_style_var_elsewhere</span></span>](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [<span data-ttu-id="81445-177">Membres expression-bodied</span><span class="sxs-lookup"><span data-stu-id="81445-177">Expression-bodied members</span></span>](expression-bodied-members.md)
  - [<span data-ttu-id="81445-178">csharp_style_expression_bodied_methods</span><span class="sxs-lookup"><span data-stu-id="81445-178">csharp_style_expression_bodied_methods</span></span>](ide0022.md#csharp_style_expression_bodied_methods)
  - [<span data-ttu-id="81445-179">csharp_style_expression_bodied_constructors</span><span class="sxs-lookup"><span data-stu-id="81445-179">csharp_style_expression_bodied_constructors</span></span>](ide0021.md#csharp_style_expression_bodied_constructors)
  - [<span data-ttu-id="81445-180">csharp_style_expression_bodied_operators</span><span class="sxs-lookup"><span data-stu-id="81445-180">csharp_style_expression_bodied_operators</span></span>](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [<span data-ttu-id="81445-181">csharp_style_expression_bodied_properties</span><span class="sxs-lookup"><span data-stu-id="81445-181">csharp_style_expression_bodied_properties</span></span>](ide0025.md#csharp_style_expression_bodied_properties)
  - [<span data-ttu-id="81445-182">csharp_style_expression_bodied_indexers</span><span class="sxs-lookup"><span data-stu-id="81445-182">csharp_style_expression_bodied_indexers</span></span>](ide0026.md#csharp_style_expression_bodied_indexers)
  - [<span data-ttu-id="81445-183">csharp_style_expression_bodied_accessors</span><span class="sxs-lookup"><span data-stu-id="81445-183">csharp_style_expression_bodied_accessors</span></span>](ide0027.md#csharp_style_expression_bodied_accessors)
  - [<span data-ttu-id="81445-184">csharp_style_expression_bodied_lambdas</span><span class="sxs-lookup"><span data-stu-id="81445-184">csharp_style_expression_bodied_lambdas</span></span>](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [<span data-ttu-id="81445-185">csharp_style_expression_bodied_local_functions</span><span class="sxs-lookup"><span data-stu-id="81445-185">csharp_style_expression_bodied_local_functions</span></span>](ide0061.md#csharp_style_expression_bodied_local_functions)
- [<span data-ttu-id="81445-186">Préférences correspondants au modèle</span><span class="sxs-lookup"><span data-stu-id="81445-186">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="81445-187">csharp_style_pattern_matching_over_is_with_cast_check</span><span class="sxs-lookup"><span data-stu-id="81445-187">csharp_style_pattern_matching_over_is_with_cast_check</span></span>](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [<span data-ttu-id="81445-188">csharp_style_pattern_matching_over_as_with_null_check</span><span class="sxs-lookup"><span data-stu-id="81445-188">csharp_style_pattern_matching_over_as_with_null_check</span></span>](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [<span data-ttu-id="81445-189">csharp_style_prefer_switch_expression</span><span class="sxs-lookup"><span data-stu-id="81445-189">csharp_style_prefer_switch_expression</span></span>](ide0066.md#csharp_style_prefer_switch_expression)
  - [<span data-ttu-id="81445-190">csharp_style_prefer_pattern_matching</span><span class="sxs-lookup"><span data-stu-id="81445-190">csharp_style_prefer_pattern_matching</span></span>](ide0078.md#csharp_style_prefer_pattern_matching)
  - [<span data-ttu-id="81445-191">csharp_style_prefer_not_pattern</span><span class="sxs-lookup"><span data-stu-id="81445-191">csharp_style_prefer_not_pattern</span></span>](ide0083.md#csharp_style_prefer_not_pattern)
- [<span data-ttu-id="81445-192">Préférences au niveau des expressions</span><span class="sxs-lookup"><span data-stu-id="81445-192">Expression-level preferences</span></span>](expression-level-preferences.md#c-expression-level-preferences)
  - [<span data-ttu-id="81445-193">csharp_style_inlined_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="81445-193">csharp_style_inlined_variable_declaration</span></span>](ide0018.md#csharp_style_inlined_variable_declaration)
  - [<span data-ttu-id="81445-194">csharp_prefer_simple_default_expression</span><span class="sxs-lookup"><span data-stu-id="81445-194">csharp_prefer_simple_default_expression</span></span>](ide0034.md#csharp_prefer_simple_default_expression)
  - [<span data-ttu-id="81445-195">csharp_style_pattern_local_over_anonymous_function</span><span class="sxs-lookup"><span data-stu-id="81445-195">csharp_style_pattern_local_over_anonymous_function</span></span>](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [<span data-ttu-id="81445-196">csharp_style_deconstructed_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="81445-196">csharp_style_deconstructed_variable_declaration</span></span>](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [<span data-ttu-id="81445-197">csharp_style_prefer_index_operator</span><span class="sxs-lookup"><span data-stu-id="81445-197">csharp_style_prefer_index_operator</span></span>](ide0056.md#csharp_style_prefer_index_operator)
  - [<span data-ttu-id="81445-198">csharp_style_prefer_range_operator</span><span class="sxs-lookup"><span data-stu-id="81445-198">csharp_style_prefer_range_operator</span></span>](ide0057.md#csharp_style_prefer_range_operator)
  - [<span data-ttu-id="81445-199">csharp_style_implicit_object_creation_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="81445-199">csharp_style_implicit_object_creation_when_type_is_apparent</span></span>](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - <span data-ttu-id="81445-200">[Ajouter des cas manquants pour changer l’expression](ide0072.md) -cette règle n’a pas d’option de style de code.</span><span class="sxs-lookup"><span data-stu-id="81445-200">[Add missing cases to switch expression](ide0072.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="81445-201">Préférences de vérification de la valeur « null »</span><span class="sxs-lookup"><span data-stu-id="81445-201">"Null" checking preferences</span></span>](null-checking-preferences.md#c-null-checking-preferences)
  - [<span data-ttu-id="81445-202">csharp_style_throw_expression</span><span class="sxs-lookup"><span data-stu-id="81445-202">csharp_style_throw_expression</span></span>](ide0016.md#csharp_style_throw_expression)
  - [<span data-ttu-id="81445-203">csharp_style_conditional_delegate_call</span><span class="sxs-lookup"><span data-stu-id="81445-203">csharp_style_conditional_delegate_call</span></span>](ide1005.md#csharp_style_conditional_delegate_call)
- [<span data-ttu-id="81445-204">Préférences relatives aux blocs de code</span><span class="sxs-lookup"><span data-stu-id="81445-204">Code block preferences</span></span>](code-block-preferences.md)
  - [<span data-ttu-id="81445-205">csharp_prefer_braces</span><span class="sxs-lookup"><span data-stu-id="81445-205">csharp_prefer_braces</span></span>](ide0011.md#csharp_prefer_braces)
  - [<span data-ttu-id="81445-206">csharp_prefer_simple_using_statement</span><span class="sxs-lookup"><span data-stu-id="81445-206">csharp_prefer_simple_using_statement</span></span>](ide0063.md#csharp_prefer_simple_using_statement)
- [<span data-ttu-id="81445-207">préférences de directive’Using'</span><span class="sxs-lookup"><span data-stu-id="81445-207">'using' directive preferences</span></span>](ide0065.md)
  - [<span data-ttu-id="81445-208">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="81445-208">csharp_using_directive_placement</span></span>](ide0065.md#csharp_using_directive_placement)
- [<span data-ttu-id="81445-209">Préférences relatives aux modificateurs</span><span class="sxs-lookup"><span data-stu-id="81445-209">Modifier preferences</span></span>](modifier-preferences.md#c-modifier-preferences)
  - [<span data-ttu-id="81445-210">csharp_prefer_static_local_function</span><span class="sxs-lookup"><span data-stu-id="81445-210">csharp_prefer_static_local_function</span></span>](ide0062.md#csharp_prefer_static_local_function)
  - <span data-ttu-id="81445-211">[Rendre les champs de struct accessibles en écriture](ide0064.md) : cette règle n’a pas d’option de style de code.</span><span class="sxs-lookup"><span data-stu-id="81445-211">[Make struct fields writable](ide0064.md) - This rule has no code style option.</span></span>

## <a name="visual-basic-style-rules"></a><span data-ttu-id="81445-212">Règles de style de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81445-212">Visual Basic style rules</span></span>

<span data-ttu-id="81445-213">Les règles de style de cette section s’appliquent uniquement à Visual Basic langage.</span><span class="sxs-lookup"><span data-stu-id="81445-213">The style rules in this section are applicable to Visual Basic language only.</span></span>

- [<span data-ttu-id="81445-214">Préférences correspondants au modèle</span><span class="sxs-lookup"><span data-stu-id="81445-214">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="81445-215">visual_basic_style_prefer_isnot_expression</span><span class="sxs-lookup"><span data-stu-id="81445-215">visual_basic_style_prefer_isnot_expression</span></span>](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a><span data-ttu-id="81445-216">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81445-216">See also</span></span>

- [<span data-ttu-id="81445-217">Règles de code inutiles</span><span class="sxs-lookup"><span data-stu-id="81445-217">Unnecessary code rules</span></span>](unnecessary-code-rules.md)
- [<span data-ttu-id="81445-218">Règles de mise en forme</span><span class="sxs-lookup"><span data-stu-id="81445-218">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="81445-219">Règles d’affectation des noms</span><span class="sxs-lookup"><span data-stu-id="81445-219">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="81445-220">Référence des règles de style de code .NET</span><span class="sxs-lookup"><span data-stu-id="81445-220">.NET code style rules reference</span></span>](index.md)

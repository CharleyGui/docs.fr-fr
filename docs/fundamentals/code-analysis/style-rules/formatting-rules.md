---
title: Règles de mise en forme du style de code
description: En savoir plus sur les règles de style de code pour mettre en forme les retraits, les espaces et les nouvelles lignes.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE0055
- formatting rules
helpviewer_keywords:
- IDE0055
- formatting code style rules [EditorConfig]
- formatting rules
- EditorConfig formatting conventions
ms.openlocfilehash: 61e6f6a6afdc6aaf9710eef3143af8ae700ef612
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "96587753"
---
# <a name="formatting-rules"></a><span data-ttu-id="eebc1-103">Règles de mise en forme</span><span class="sxs-lookup"><span data-stu-id="eebc1-103">Formatting rules</span></span>

<span data-ttu-id="eebc1-104">Les règles de mise en forme affectent la manière dont les retraits, les espaces et les nouvelles lignes sont alignés autour des constructions du langage de programmation .NET.</span><span class="sxs-lookup"><span data-stu-id="eebc1-104">Formatting rules affect how indentation, spaces, and new lines are aligned around .NET programming language constructs.</span></span> <span data-ttu-id="eebc1-105">Les règles sont classées dans les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="eebc1-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="eebc1-106">[Règles de mise en forme .net](#net-formatting-rules): règles qui s’appliquent à la fois à C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eebc1-106">[.NET formatting rules](#net-formatting-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="eebc1-107">Les noms des options EditorConfig pour ces règles commencent par le `dotnet_` préfixe.</span><span class="sxs-lookup"><span data-stu-id="eebc1-107">The EditorConfig option names for these rules start with `dotnet_` prefix.</span></span>
- <span data-ttu-id="eebc1-108">[Règles de mise en forme c#](#c-formatting-rules): règles spécifiques au langage c# uniquement.</span><span class="sxs-lookup"><span data-stu-id="eebc1-108">[C# formatting rules](#c-formatting-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="eebc1-109">Les noms des options EditorConfig pour ces règles commencent par le `csharp_` préfixe.</span><span class="sxs-lookup"><span data-stu-id="eebc1-109">The EditorConfig option names for these rules start with `csharp_` prefix.</span></span>

## <a name="rule-id-ide0055-fix-formatting"></a><span data-ttu-id="eebc1-110">ID de règle : « IDE0055 » (correction de la mise en forme)</span><span class="sxs-lookup"><span data-stu-id="eebc1-110">Rule ID: "IDE0055" (Fix formatting)</span></span>

<span data-ttu-id="eebc1-111">Toutes les options de mise en forme ont un ID `IDE0055` et un titre de règle `Fix formatting` .</span><span class="sxs-lookup"><span data-stu-id="eebc1-111">All formatting options have rule ID `IDE0055` and title `Fix formatting`.</span></span> <span data-ttu-id="eebc1-112">Définissez la gravité d’une violation de mise en forme dans un fichier baEditorConfig à l’aide de la ligne de configuration suivante.</span><span class="sxs-lookup"><span data-stu-id="eebc1-112">Set the severity of a formatting violation in an EditorConfig file using the following configuration line.</span></span>

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

<span data-ttu-id="eebc1-113">La valeur de gravité doit être ou doit être `warning` `error` [appliquée lors de la génération](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="eebc1-113">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="eebc1-114">Pour toutes les valeurs de gravité possibles, consultez [niveau de gravité](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="eebc1-114">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="option-format"></a><span data-ttu-id="eebc1-115">Format d’option</span><span class="sxs-lookup"><span data-stu-id="eebc1-115">Option format</span></span>

<span data-ttu-id="eebc1-116">Les options de mise en forme des règles peuvent être spécifiées dans un fichier EditorConfig au format suivant :</span><span class="sxs-lookup"><span data-stu-id="eebc1-116">Options for formatting rules can be specified in an EditorConfig file with the following format:</span></span>

`rule_name = value`

<span data-ttu-id="eebc1-117">Pour de nombreuses règles, vous spécifiez `true` (préférer ce style) ou `false` (ne pas préférer ce style) pour `value`.</span><span class="sxs-lookup"><span data-stu-id="eebc1-117">For many rules, you specify either `true` (prefer this style) or `false` (do not prefer this style) for `value`.</span></span> <span data-ttu-id="eebc1-118">Pour les autres règles, vous spécifiez une valeur comme `flush_left` ou `before_and_after` pour décrire quand et où appliquer la règle.</span><span class="sxs-lookup"><span data-stu-id="eebc1-118">For other rules, you specify a value such as `flush_left` or `before_and_after` to describe when and where to apply the rule.</span></span> <span data-ttu-id="eebc1-119">Vous ne spécifiez pas un niveau de gravité.</span><span class="sxs-lookup"><span data-stu-id="eebc1-119">You don't specify a severity.</span></span>

## <a name="net-formatting-rules"></a><span data-ttu-id="eebc1-120">Règles de mise en forme .NET</span><span class="sxs-lookup"><span data-stu-id="eebc1-120">.NET formatting rules</span></span>

<span data-ttu-id="eebc1-121">Les règles de mise en forme de cette section s’appliquent à C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eebc1-121">The formatting rules in this section apply to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="eebc1-122">Organiser les using</span><span class="sxs-lookup"><span data-stu-id="eebc1-122">Organize usings</span></span>](#organize-using-directives)
  - <span data-ttu-id="eebc1-123">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="eebc1-123">dotnet_sort_system_directives_first</span></span>
  - <span data-ttu-id="eebc1-124">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="eebc1-124">dotnet_separate_import_directive_groups</span></span>

### <a name="organize-using-directives"></a><span data-ttu-id="eebc1-125">Organiser les directives using</span><span class="sxs-lookup"><span data-stu-id="eebc1-125">Organize using directives</span></span>

<span data-ttu-id="eebc1-126">Ces règles de mise en forme concernent le tri et l’affichage des directives `using` et instructions `Imports`.</span><span class="sxs-lookup"><span data-stu-id="eebc1-126">These formatting rules concern the sorting and display of `using` directives and `Imports` statements.</span></span>

<span data-ttu-id="eebc1-127">Exemple de fichier *.editorconfig* :</span><span class="sxs-lookup"><span data-stu-id="eebc1-127">Example *.editorconfig* file:</span></span>

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a><span data-ttu-id="eebc1-128">dotnet\_sort\_system\_directives_first</span><span class="sxs-lookup"><span data-stu-id="eebc1-128">dotnet\_sort\_system\_directives_first</span></span>

|<span data-ttu-id="eebc1-129">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-129">Property</span></span>|<span data-ttu-id="eebc1-130">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-130">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-131">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-131">**Option name**</span></span> | <span data-ttu-id="eebc1-132">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="eebc1-132">dotnet_sort_system_directives_first</span></span> |
| <span data-ttu-id="eebc1-133">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-133">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-134">C# et Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eebc1-134">C# and Visual Basic</span></span> |
| <span data-ttu-id="eebc1-135">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-135">**Introduced version**</span></span> | <span data-ttu-id="eebc1-136">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-136">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-137">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-137">**Option values**</span></span> | <span data-ttu-id="eebc1-138">`true` -Trier `System.*` `using` les directives par ordre alphabétique et les placer avant les autres directives using.</span><span class="sxs-lookup"><span data-stu-id="eebc1-138">`true` - Sort `System.*` `using` directives alphabetically, and place them before other using directives.</span></span><br /><br /><span data-ttu-id="eebc1-139">`false` -Ne pas placer de `System.*` `using` directives avant d’autres `using` directives.</span><span class="sxs-lookup"><span data-stu-id="eebc1-139">`false` - Do not place `System.*` `using` directives before other `using` directives.</span></span> |

<span data-ttu-id="eebc1-140">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-140">Code examples:</span></span>

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a><span data-ttu-id="eebc1-141">dotnet\_separate\_import\_directive\_groups</span><span class="sxs-lookup"><span data-stu-id="eebc1-141">dotnet\_separate\_import\_directive\_groups</span></span>

|<span data-ttu-id="eebc1-142">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-142">Property</span></span>|<span data-ttu-id="eebc1-143">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-143">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-144">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-144">**Option name**</span></span> | <span data-ttu-id="eebc1-145">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="eebc1-145">dotnet_separate_import_directive_groups</span></span> |
| <span data-ttu-id="eebc1-146">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-146">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-147">C# et Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eebc1-147">C# and Visual Basic</span></span> |
| <span data-ttu-id="eebc1-148">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-148">**Introduced version**</span></span> | <span data-ttu-id="eebc1-149">Visual Studio 2017 version 15.5</span><span class="sxs-lookup"><span data-stu-id="eebc1-149">Visual Studio 2017 version 15.5</span></span> |
| <span data-ttu-id="eebc1-150">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-150">**Option values**</span></span> | <span data-ttu-id="eebc1-151">`true` - Placer une ligne vide entre les groupes de directives `using`.</span><span class="sxs-lookup"><span data-stu-id="eebc1-151">`true` - Place a blank line between `using` directive groups.</span></span><br /><br /><span data-ttu-id="eebc1-152">`false` - Ne pas placer de ligne vide entre les groupes de directives `using`.</span><span class="sxs-lookup"><span data-stu-id="eebc1-152">`false` - Do not place a blank line between `using` directive groups.</span></span> |

<span data-ttu-id="eebc1-153">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-153">Code examples:</span></span>

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-rules"></a><span data-ttu-id="eebc1-154">Règles de mise en forme C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-154">C# formatting rules</span></span>

<span data-ttu-id="eebc1-155">Les règles de mise en forme mentionnées dans cette section s’appliquent uniquement au code C#.</span><span class="sxs-lookup"><span data-stu-id="eebc1-155">The formatting rules in this section apply only to C# code.</span></span>

- [<span data-ttu-id="eebc1-156">Options de saut de ligne</span><span class="sxs-lookup"><span data-stu-id="eebc1-156">Newline options</span></span>](#new-line-options)
  - <span data-ttu-id="eebc1-157">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="eebc1-157">csharp_new_line_before_open_brace</span></span>
  - <span data-ttu-id="eebc1-158">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="eebc1-158">csharp_new_line_before_else</span></span>
  - <span data-ttu-id="eebc1-159">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="eebc1-159">csharp_new_line_before_catch</span></span>
  - <span data-ttu-id="eebc1-160">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="eebc1-160">csharp_new_line_before_finally</span></span>
  - <span data-ttu-id="eebc1-161">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="eebc1-161">csharp_new_line_before_members_in_object_initializers</span></span>
  - <span data-ttu-id="eebc1-162">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="eebc1-162">csharp_new_line_before_members_in_anonymous_types</span></span>
  - <span data-ttu-id="eebc1-163">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="eebc1-163">csharp_new_line_between_query_expression_clauses</span></span>
- [<span data-ttu-id="eebc1-164">Options de mise en retrait</span><span class="sxs-lookup"><span data-stu-id="eebc1-164">Indentation options</span></span>](#indentation-options)
  - <span data-ttu-id="eebc1-165">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="eebc1-165">csharp_indent_case_contents</span></span>
  - <span data-ttu-id="eebc1-166">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="eebc1-166">csharp_indent_switch_labels</span></span>
  - <span data-ttu-id="eebc1-167">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="eebc1-167">csharp_indent_labels</span></span>
  - <span data-ttu-id="eebc1-168">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="eebc1-168">csharp_indent_block_contents</span></span>
  - <span data-ttu-id="eebc1-169">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="eebc1-169">csharp_indent_braces</span></span>
  - <span data-ttu-id="eebc1-170">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="eebc1-170">csharp_indent_case_contents_when_block</span></span>
- [<span data-ttu-id="eebc1-171">Options d’espacement</span><span class="sxs-lookup"><span data-stu-id="eebc1-171">Spacing options</span></span>](#spacing-options)
  - <span data-ttu-id="eebc1-172">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="eebc1-172">csharp_space_after_cast</span></span>
  - <span data-ttu-id="eebc1-173">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="eebc1-173">csharp_space_after_keywords_in_control_flow_statements</span></span>
  - <span data-ttu-id="eebc1-174">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-174">csharp_space_between_parentheses</span></span>
  - <span data-ttu-id="eebc1-175">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="eebc1-175">csharp_space_before_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="eebc1-176">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="eebc1-176">csharp_space_after_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="eebc1-177">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="eebc1-177">csharp_space_around_binary_operators</span></span>
  - <span data-ttu-id="eebc1-178">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-178">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>
  - <span data-ttu-id="eebc1-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="eebc1-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="eebc1-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>
  - <span data-ttu-id="eebc1-181">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-181">csharp_space_between_method_call_parameter_list_parentheses</span></span>
  - <span data-ttu-id="eebc1-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="eebc1-183">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="eebc1-183">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>
  - <span data-ttu-id="eebc1-184">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="eebc1-184">csharp_space_after_comma</span></span>
  - <span data-ttu-id="eebc1-185">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="eebc1-185">csharp_space_before_comma</span></span>
  - <span data-ttu-id="eebc1-186">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="eebc1-186">csharp_space_after_dot</span></span>
  - <span data-ttu-id="eebc1-187">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="eebc1-187">csharp_space_before_dot</span></span>
  - <span data-ttu-id="eebc1-188">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="eebc1-188">csharp_space_after_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="eebc1-189">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="eebc1-189">csharp_space_before_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="eebc1-190">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="eebc1-190">csharp_space_around_declaration_statements</span></span>
  - <span data-ttu-id="eebc1-191">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="eebc1-191">csharp_space_before_open_square_brackets</span></span>
  - <span data-ttu-id="eebc1-192">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="eebc1-192">csharp_space_between_empty_square_brackets</span></span>
  - <span data-ttu-id="eebc1-193">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="eebc1-193">csharp_space_between_square_brackets</span></span>
- [<span data-ttu-id="eebc1-194">Options d’encapsulage</span><span class="sxs-lookup"><span data-stu-id="eebc1-194">Wrap options</span></span>](#wrap-options)
  - <span data-ttu-id="eebc1-195">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="eebc1-195">csharp_preserve_single_line_statements</span></span>
  - <span data-ttu-id="eebc1-196">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="eebc1-196">csharp_preserve_single_line_blocks</span></span>
- [<span data-ttu-id="eebc1-197">Utilisation des options de directive</span><span class="sxs-lookup"><span data-stu-id="eebc1-197">Using directive options</span></span>](#using-directive-options)
  - <span data-ttu-id="eebc1-198">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="eebc1-198">csharp_using_directive_placement</span></span>

### <a name="new-line-options"></a><span data-ttu-id="eebc1-199">Options de nouvelle ligne</span><span class="sxs-lookup"><span data-stu-id="eebc1-199">New-line options</span></span>

<span data-ttu-id="eebc1-200">Ces règles de mise en forme concernent l’utilisation de nouvelles lignes pour mettre en forme du code.</span><span class="sxs-lookup"><span data-stu-id="eebc1-200">These formatting rules concern the use of new lines to format code.</span></span>

<span data-ttu-id="eebc1-201">Exemple de fichier *.editorconfig* :</span><span class="sxs-lookup"><span data-stu-id="eebc1-201">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a><span data-ttu-id="eebc1-202">csharp\_new\_line\_before\_open_brace</span><span class="sxs-lookup"><span data-stu-id="eebc1-202">csharp\_new\_line\_before\_open_brace</span></span>

<span data-ttu-id="eebc1-203">Cette règle vise à déterminer si une accolade ouvrante `{` doit être placée sur la même ligne que le code précédent, ou sur une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="eebc1-203">This rule concerns whether an open brace `{` should be placed on the same line as the preceding code, or on a new line.</span></span> <span data-ttu-id="eebc1-204">Pour cette règle, vous spécifiez à la place **all**, **none**, ou un ou plusieurs éléments de code tels que **methods** ou **proprerties**, pour définir quand cette règle doit être appliquée.</span><span class="sxs-lookup"><span data-stu-id="eebc1-204">For this rule, you specify **all**, **none**, or one or more code elements such as **methods** or **properties**, to define when this rule should be applied.</span></span> <span data-ttu-id="eebc1-205">Pour spécifier plusieurs éléments de code, séparez-les par une virgule (,).</span><span class="sxs-lookup"><span data-stu-id="eebc1-205">To specify multiple code elements, separate them with a comma (,).</span></span>

|<span data-ttu-id="eebc1-206">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-206">Property</span></span>|<span data-ttu-id="eebc1-207">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-207">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-208">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-208">**Option name**</span></span> | <span data-ttu-id="eebc1-209">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="eebc1-209">csharp_new_line_before_open_brace</span></span> |
| <span data-ttu-id="eebc1-210">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-210">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-211">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-211">C#</span></span> |
| <span data-ttu-id="eebc1-212">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-212">**Introduced version**</span></span> | <span data-ttu-id="eebc1-213">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-213">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-214">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-214">**Option values**</span></span> | <span data-ttu-id="eebc1-215">`all` - Les accolades doivent se trouver sur une nouvelle ligne pour toutes les expressions (style « Allman »).</span><span class="sxs-lookup"><span data-stu-id="eebc1-215">`all` - Require braces to be on a new line for all expressions ("Allman" style).</span></span><br /><br /><span data-ttu-id="eebc1-216">`none` - Les accolades doivent se trouver sur la même ligne pour toutes les expressions ("K&R").</span><span class="sxs-lookup"><span data-stu-id="eebc1-216">`none` - Require braces to be on the same line for all expressions ("K&R").</span></span><br /><br /><span data-ttu-id="eebc1-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Nécessiter la présence d’accolades sur une nouvelle ligne pour l’élément de code spécifié (style « Allman »).</span><span class="sxs-lookup"><span data-stu-id="eebc1-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Require braces to be on a new line for the specified code element ("Allman" style).</span></span> |

<span data-ttu-id="eebc1-218">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-218">Code examples:</span></span>

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a><span data-ttu-id="eebc1-219">csharp\_new\_line\_before_else</span><span class="sxs-lookup"><span data-stu-id="eebc1-219">csharp\_new\_line\_before_else</span></span>

|<span data-ttu-id="eebc1-220">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-220">Property</span></span>|<span data-ttu-id="eebc1-221">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-221">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-222">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-222">**Option name**</span></span> | <span data-ttu-id="eebc1-223">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="eebc1-223">csharp_new_line_before_else</span></span> |
| <span data-ttu-id="eebc1-224">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-224">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-225">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-225">C#</span></span> |
| <span data-ttu-id="eebc1-226">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-226">**Introduced version**</span></span> | <span data-ttu-id="eebc1-227">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-227">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-228">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-228">**Option values**</span></span> | <span data-ttu-id="eebc1-229">`true` - Placer les instructions `else` sur une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="eebc1-229">`true` - Place `else` statements on a new line.</span></span><br /><br /><span data-ttu-id="eebc1-230">`false` - Placer les instructions `else` sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="eebc1-230">`false` - Place `else` statements on the same line.</span></span> |

<span data-ttu-id="eebc1-231">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-231">Code examples:</span></span>

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a><span data-ttu-id="eebc1-232">csharp\_new\_line\_before_catch</span><span class="sxs-lookup"><span data-stu-id="eebc1-232">csharp\_new\_line\_before_catch</span></span>

|<span data-ttu-id="eebc1-233">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-233">Property</span></span>|<span data-ttu-id="eebc1-234">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-234">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-235">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-235">**Option name**</span></span> | <span data-ttu-id="eebc1-236">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="eebc1-236">csharp_new_line_before_catch</span></span> |
| <span data-ttu-id="eebc1-237">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-237">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-238">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-238">C#</span></span> |
| <span data-ttu-id="eebc1-239">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-239">**Introduced version**</span></span> | <span data-ttu-id="eebc1-240">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-240">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-241">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-241">**Option values**</span></span> | <span data-ttu-id="eebc1-242">`true` - Placer les instructions `catch` sur une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="eebc1-242">`true` - Place `catch` statements on a new line.</span></span><br /><br /><span data-ttu-id="eebc1-243">`false` - Placer les instructions `catch` sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="eebc1-243">`false` - Place `catch` statements on the same line.</span></span> |

<span data-ttu-id="eebc1-244">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-244">Code examples:</span></span>

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a><span data-ttu-id="eebc1-245">csharp\_new\_line\_before_finally</span><span class="sxs-lookup"><span data-stu-id="eebc1-245">csharp\_new\_line\_before_finally</span></span>

|<span data-ttu-id="eebc1-246">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-246">Property</span></span>|<span data-ttu-id="eebc1-247">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-247">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-248">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-248">**Option name**</span></span> | <span data-ttu-id="eebc1-249">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="eebc1-249">csharp_new_line_before_finally</span></span> |
| <span data-ttu-id="eebc1-250">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-250">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-251">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-251">C#</span></span> |
| <span data-ttu-id="eebc1-252">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-252">**Introduced version**</span></span> | <span data-ttu-id="eebc1-253">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-253">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-254">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-254">**Option values**</span></span> | <span data-ttu-id="eebc1-255">`true` - Les instructions `finally` doivent se trouver sur une nouvelle ligne après l’accolade fermante.</span><span class="sxs-lookup"><span data-stu-id="eebc1-255">`true` - Require `finally` statements to be on a new line after the closing brace.</span></span><br /><br /><span data-ttu-id="eebc1-256">`false` - Les instructions `finally` doivent se trouver sur la même ligne que l’accolade fermante.</span><span class="sxs-lookup"><span data-stu-id="eebc1-256">`false` - Require `finally` statements to be on the same line as the closing brace.</span></span> |

<span data-ttu-id="eebc1-257">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-257">Code examples:</span></span>

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a><span data-ttu-id="eebc1-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span><span class="sxs-lookup"><span data-stu-id="eebc1-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span></span>

|<span data-ttu-id="eebc1-259">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-259">Property</span></span>|<span data-ttu-id="eebc1-260">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-260">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-261">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-261">**Option name**</span></span> | <span data-ttu-id="eebc1-262">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="eebc1-262">csharp_new_line_before_members_in_object_initializers</span></span> |
| <span data-ttu-id="eebc1-263">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-263">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-264">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-264">C#</span></span> |
| <span data-ttu-id="eebc1-265">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-265">**Introduced version**</span></span> | <span data-ttu-id="eebc1-266">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-266">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-267">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-267">**Option values**</span></span> | <span data-ttu-id="eebc1-268">`true` - Les membres d’initialiseurs d’objet doivent être sur des lignes distinctes</span><span class="sxs-lookup"><span data-stu-id="eebc1-268">`true` - Require members of object initializers to be on separate lines</span></span><br /><br /><span data-ttu-id="eebc1-269">`false` - Les membres d’initialiseurs d’objet doivent être sur la même ligne</span><span class="sxs-lookup"><span data-stu-id="eebc1-269">`false` - Require members of object initializers to be on the same line</span></span> |

<span data-ttu-id="eebc1-270">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-270">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a><span data-ttu-id="eebc1-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="eebc1-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span></span>

|<span data-ttu-id="eebc1-272">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-272">Property</span></span>|<span data-ttu-id="eebc1-273">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-273">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-274">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-274">**Option name**</span></span> | <span data-ttu-id="eebc1-275">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="eebc1-275">csharp_new_line_before_members_in_anonymous_types</span></span> |
| <span data-ttu-id="eebc1-276">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-276">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-277">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-277">C#</span></span> |
| <span data-ttu-id="eebc1-278">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-278">**Introduced version**</span></span> | <span data-ttu-id="eebc1-279">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-279">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-280">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-280">**Option values**</span></span> | <span data-ttu-id="eebc1-281">`true` - Les membres de types anonymes doivent être sur des lignes distinctes</span><span class="sxs-lookup"><span data-stu-id="eebc1-281">`true` - Require members of anonymous types to be on separate lines</span></span><br /><br /><span data-ttu-id="eebc1-282">`false` - Les membres de types anonymes doivent être sur la même ligne</span><span class="sxs-lookup"><span data-stu-id="eebc1-282">`false` - Require members of anonymous types to be on the same line</span></span> |

<span data-ttu-id="eebc1-283">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-283">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a><span data-ttu-id="eebc1-284">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="eebc1-284">csharp_new_line_between_query_expression_clauses</span></span>

|<span data-ttu-id="eebc1-285">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-285">Property</span></span>|<span data-ttu-id="eebc1-286">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-286">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-287">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-287">**Option name**</span></span> | <span data-ttu-id="eebc1-288">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="eebc1-288">csharp_new_line_between_query_expression_clauses</span></span> |
| <span data-ttu-id="eebc1-289">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-289">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-290">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-290">C#</span></span> |
| <span data-ttu-id="eebc1-291">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-291">**Introduced version**</span></span> | <span data-ttu-id="eebc1-292">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-292">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-293">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-293">**Option values**</span></span> | <span data-ttu-id="eebc1-294">`true` - Les éléments des clauses d’expression de requête doivent se trouver sur des lignes distinctes</span><span class="sxs-lookup"><span data-stu-id="eebc1-294">`true` - Require elements of query expression clauses to be on separate lines</span></span><br /><br /><span data-ttu-id="eebc1-295">`false` - Les éléments des clauses d’expression de requête doivent se trouver sur la même ligne</span><span class="sxs-lookup"><span data-stu-id="eebc1-295">`false` - Require elements of query expression clauses to be on the same line</span></span> |

<span data-ttu-id="eebc1-296">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-296">Code examples:</span></span>

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a><span data-ttu-id="eebc1-297">Options d’indentation</span><span class="sxs-lookup"><span data-stu-id="eebc1-297">Indentation options</span></span>

<span data-ttu-id="eebc1-298">Ces règles de mise en forme concernent l’utilisation de l’indentation pour mettre en forme du code.</span><span class="sxs-lookup"><span data-stu-id="eebc1-298">These formatting rules concern the use of indentation to format code.</span></span>

<span data-ttu-id="eebc1-299">Exemple de fichier *.editorconfig* :</span><span class="sxs-lookup"><span data-stu-id="eebc1-299">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a><span data-ttu-id="eebc1-300">csharp\_indent\_case_contents</span><span class="sxs-lookup"><span data-stu-id="eebc1-300">csharp\_indent\_case_contents</span></span>

|<span data-ttu-id="eebc1-301">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-301">Property</span></span>|<span data-ttu-id="eebc1-302">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-302">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-303">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-303">**Option name**</span></span> | <span data-ttu-id="eebc1-304">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="eebc1-304">csharp_indent_case_contents</span></span> |
| <span data-ttu-id="eebc1-305">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-305">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-306">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-306">C#</span></span> |
| <span data-ttu-id="eebc1-307">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-307">**Introduced version**</span></span> | <span data-ttu-id="eebc1-308">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-308">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-309">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-309">**Option values**</span></span> | <span data-ttu-id="eebc1-310">`true` - Mettre en retrait le contenu de `switch` case</span><span class="sxs-lookup"><span data-stu-id="eebc1-310">`true` - Indent `switch` case contents</span></span><br /><br /><span data-ttu-id="eebc1-311">`false` - Ne pas mettre en retrait le contenu de `switch` case</span><span class="sxs-lookup"><span data-stu-id="eebc1-311">`false` - Do not indent `switch` case contents</span></span> |

- <span data-ttu-id="eebc1-312">Quand cette règle est définie sur **true**, i.</span><span class="sxs-lookup"><span data-stu-id="eebc1-312">When this rule is set to **true**, i.</span></span>
- <span data-ttu-id="eebc1-313">Quand cette règle est définie sur **false**, d.</span><span class="sxs-lookup"><span data-stu-id="eebc1-313">When this rule is set to **false**, d.</span></span>

<span data-ttu-id="eebc1-314">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-314">Code examples:</span></span>

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a><span data-ttu-id="eebc1-315">csharp\_indent\_switch_labels</span><span class="sxs-lookup"><span data-stu-id="eebc1-315">csharp\_indent\_switch_labels</span></span>

|<span data-ttu-id="eebc1-316">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-316">Property</span></span>|<span data-ttu-id="eebc1-317">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-317">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-318">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-318">**Option name**</span></span> | <span data-ttu-id="eebc1-319">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="eebc1-319">csharp_indent_switch_labels</span></span> |
| <span data-ttu-id="eebc1-320">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-320">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-321">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-321">C#</span></span> |
| <span data-ttu-id="eebc1-322">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-322">**Introduced version**</span></span> | <span data-ttu-id="eebc1-323">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-323">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-324">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-324">**Option values**</span></span> | <span data-ttu-id="eebc1-325">`true` - Mettre en retrait les étiquettes `switch`</span><span class="sxs-lookup"><span data-stu-id="eebc1-325">`true` - Indent `switch` labels</span></span><br /><br /><span data-ttu-id="eebc1-326">`false` - Ne pas mettre en retrait les étiquettes `switch`</span><span class="sxs-lookup"><span data-stu-id="eebc1-326">`false` - Do not indent `switch` labels</span></span> |

<span data-ttu-id="eebc1-327">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-327">Code examples:</span></span>

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a><span data-ttu-id="eebc1-328">csharp\_indent_labels</span><span class="sxs-lookup"><span data-stu-id="eebc1-328">csharp\_indent_labels</span></span>

|<span data-ttu-id="eebc1-329">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-329">Property</span></span>|<span data-ttu-id="eebc1-330">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-330">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-331">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-331">**Option name**</span></span> | <span data-ttu-id="eebc1-332">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="eebc1-332">csharp_indent_labels</span></span> |
| <span data-ttu-id="eebc1-333">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-333">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-334">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-334">C#</span></span> |
| <span data-ttu-id="eebc1-335">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-335">**Introduced version**</span></span> | <span data-ttu-id="eebc1-336">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-336">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-337">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-337">**Option values**</span></span> | <span data-ttu-id="eebc1-338">`flush_left` - Les étiquettes sont positionnées au niveau de la colonne la plus à gauche</span><span class="sxs-lookup"><span data-stu-id="eebc1-338">`flush_left` - Labels are placed at the leftmost column</span></span><br /><br /><span data-ttu-id="eebc1-339">`one_less_than_current` - Les étiquettes sont positionnées d’un retrait à gauche par rapport au contexte actuel</span><span class="sxs-lookup"><span data-stu-id="eebc1-339">`one_less_than_current` - Labels are placed at one less indent to the current context</span></span><br /><br /><span data-ttu-id="eebc1-340">`no_change` - Les étiquettes sont placées au même niveau de retrait que le contexte actuel</span><span class="sxs-lookup"><span data-stu-id="eebc1-340">`no_change` - Labels are placed at the same indent as the current context</span></span> |

<span data-ttu-id="eebc1-341">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-341">Code examples:</span></span>

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a><span data-ttu-id="eebc1-342">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="eebc1-342">csharp_indent_block_contents</span></span>

|<span data-ttu-id="eebc1-343">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-343">Property</span></span>|<span data-ttu-id="eebc1-344">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-344">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-345">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-345">**Option name**</span></span> | <span data-ttu-id="eebc1-346">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="eebc1-346">csharp_indent_block_contents</span></span> |
| <span data-ttu-id="eebc1-347">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-347">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-348">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-348">C#</span></span> |
| <span data-ttu-id="eebc1-349">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-349">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="eebc1-350">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-350">Code examples:</span></span>

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a><span data-ttu-id="eebc1-351">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="eebc1-351">csharp_indent_braces</span></span>

|<span data-ttu-id="eebc1-352">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-352">Property</span></span>|<span data-ttu-id="eebc1-353">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-353">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-354">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-354">**Option name**</span></span> | <span data-ttu-id="eebc1-355">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="eebc1-355">csharp_indent_braces</span></span> |
| <span data-ttu-id="eebc1-356">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-356">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-357">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-357">C#</span></span> |
| <span data-ttu-id="eebc1-358">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-358">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="eebc1-359">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-359">Code examples:</span></span>

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a><span data-ttu-id="eebc1-360">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="eebc1-360">csharp_indent_case_contents_when_block</span></span>

|<span data-ttu-id="eebc1-361">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-361">Property</span></span>|<span data-ttu-id="eebc1-362">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-362">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-363">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-363">**Option name**</span></span> | <span data-ttu-id="eebc1-364">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="eebc1-364">csharp_indent_case_contents_when_block</span></span> |
| <span data-ttu-id="eebc1-365">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-365">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-366">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-366">C#</span></span> |
| <span data-ttu-id="eebc1-367">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-367">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="eebc1-368">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-368">Code examples:</span></span>

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a><span data-ttu-id="eebc1-369">Options d’espacement</span><span class="sxs-lookup"><span data-stu-id="eebc1-369">Spacing options</span></span>

<span data-ttu-id="eebc1-370">Ces règles de mise en forme concernent l’utilisation de caractères d’espacement pour mettre en forme du code.</span><span class="sxs-lookup"><span data-stu-id="eebc1-370">These formatting rules concern the use of space characters to format code.</span></span>

<span data-ttu-id="eebc1-371">Exemple de fichier *.editorconfig* :</span><span class="sxs-lookup"><span data-stu-id="eebc1-371">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a><span data-ttu-id="eebc1-372">csharp\_space\_after_cast</span><span class="sxs-lookup"><span data-stu-id="eebc1-372">csharp\_space\_after_cast</span></span>

|<span data-ttu-id="eebc1-373">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-373">Property</span></span>|<span data-ttu-id="eebc1-374">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-374">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-375">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-375">**Option name**</span></span> | <span data-ttu-id="eebc1-376">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="eebc1-376">csharp_space_after_cast</span></span> |
| <span data-ttu-id="eebc1-377">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-377">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-378">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-378">C#</span></span> |
| <span data-ttu-id="eebc1-379">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-379">**Introduced version**</span></span> | <span data-ttu-id="eebc1-380">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-380">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-381">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-381">**Option values**</span></span> | <span data-ttu-id="eebc1-382">`true` - Placer un espace entre un cast et la valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-382">`true` - Place a space character between a cast and the value</span></span><br /><br /><span data-ttu-id="eebc1-383">`false` - Supprimer l’espace entre le cast et la valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-383">`false` - Remove space between the cast and the value</span></span> |

<span data-ttu-id="eebc1-384">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-384">Code examples:</span></span>

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a><span data-ttu-id="eebc1-385">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="eebc1-385">csharp_space_after_keywords_in_control_flow_statements</span></span>

|<span data-ttu-id="eebc1-386">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-386">Property</span></span>|<span data-ttu-id="eebc1-387">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-387">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-388">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-388">**Option name**</span></span> | <span data-ttu-id="eebc1-389">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="eebc1-389">csharp_space_after_keywords_in_control_flow_statements</span></span> |
| <span data-ttu-id="eebc1-390">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-390">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-391">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-391">C#</span></span> |
| <span data-ttu-id="eebc1-392">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-392">**Introduced version**</span></span> | <span data-ttu-id="eebc1-393">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-393">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-394">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-394">**Option values**</span></span> | <span data-ttu-id="eebc1-395">`true` - Placer un espace après un mot clé dans une instruction de flux de contrôle, par exemple une boucle `for`</span><span class="sxs-lookup"><span data-stu-id="eebc1-395">`true` - Place a space character after a keyword in a control flow statement such as a `for` loop</span></span><br /><br /><span data-ttu-id="eebc1-396">`false` - Supprimer l’espace après un mot clé dans une instruction de flux de contrôle, par exemple une boucle `for`</span><span class="sxs-lookup"><span data-stu-id="eebc1-396">`false` - Remove space after a keyword in a control flow statement such as a `for` loop</span></span> |

<span data-ttu-id="eebc1-397">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-397">Code examples:</span></span>

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a><span data-ttu-id="eebc1-398">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-398">csharp_space_between_parentheses</span></span>

|<span data-ttu-id="eebc1-399">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-399">Property</span></span>|<span data-ttu-id="eebc1-400">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-400">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-401">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-401">**Option name**</span></span> | <span data-ttu-id="eebc1-402">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-402">csharp_space_between_parentheses</span></span> |
| <span data-ttu-id="eebc1-403">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-403">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-404">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-404">C#</span></span> |
| <span data-ttu-id="eebc1-405">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-405">**Introduced version**</span></span> | <span data-ttu-id="eebc1-406">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-406">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-407">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-407">**Option values**</span></span> | <span data-ttu-id="eebc1-408">`control_flow_statements` - Placer un espace entre les parenthèses d’instructions de flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="eebc1-408">`control_flow_statements` - Place space between parentheses of control flow statements</span></span><br /><br /><span data-ttu-id="eebc1-409">`expressions` - Placer un espace entre les parenthèses d’expressions</span><span class="sxs-lookup"><span data-stu-id="eebc1-409">`expressions` - Place space between parentheses of expressions</span></span><br /><br /><span data-ttu-id="eebc1-410">`type_casts` - Placer un espace entre les parenthèses dans les casts de type</span><span class="sxs-lookup"><span data-stu-id="eebc1-410">`type_casts` - Place space between parentheses in type casts</span></span> |

<span data-ttu-id="eebc1-411">Si vous omettez cette règle, ou si vous utilisez une valeur autre que `control_flow_statements`, `expressions` ou `type_casts`, le paramètre n’est pas appliqué.</span><span class="sxs-lookup"><span data-stu-id="eebc1-411">If you omit this rule or use a value other than `control_flow_statements`, `expressions`, or `type_casts`, the setting is not applied.</span></span>

<span data-ttu-id="eebc1-412">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-412">Code examples:</span></span>

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a><span data-ttu-id="eebc1-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="eebc1-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="eebc1-414">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-414">Property</span></span>|<span data-ttu-id="eebc1-415">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-415">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-416">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-416">**Option name**</span></span> | <span data-ttu-id="eebc1-417">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="eebc1-417">csharp_space_before_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="eebc1-418">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-418">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-419">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-419">C#</span></span> |
| <span data-ttu-id="eebc1-420">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-420">**Introduced version**</span></span> | <span data-ttu-id="eebc1-421">Visual Studio 2017 version 15.7</span><span class="sxs-lookup"><span data-stu-id="eebc1-421">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="eebc1-422">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-422">**Option values**</span></span> | <span data-ttu-id="eebc1-423">`true` - Placer un espace avant le signe deux-points pour les bases ou les interfaces dans une déclaration de type</span><span class="sxs-lookup"><span data-stu-id="eebc1-423">`true` - Place a space character before the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="eebc1-424">`false` - Supprimer l’espace avant le signe deux-points pour les bases ou les interfaces dans une déclaration de type</span><span class="sxs-lookup"><span data-stu-id="eebc1-424">`false` - Remove space before the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="eebc1-425">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-425">Code examples:</span></span>

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a><span data-ttu-id="eebc1-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="eebc1-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="eebc1-427">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-427">Property</span></span>|<span data-ttu-id="eebc1-428">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-428">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-429">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-429">**Option name**</span></span> | <span data-ttu-id="eebc1-430">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="eebc1-430">csharp_space_after_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="eebc1-431">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-431">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-432">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-432">C#</span></span> |
| <span data-ttu-id="eebc1-433">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-433">**Introduced version**</span></span> | <span data-ttu-id="eebc1-434">Visual Studio 2017 version 15.7</span><span class="sxs-lookup"><span data-stu-id="eebc1-434">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="eebc1-435">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-435">**Option values**</span></span> | <span data-ttu-id="eebc1-436">`true` - Placer un espace après le signe deux-points pour les bases ou les interfaces dans une déclaration de type</span><span class="sxs-lookup"><span data-stu-id="eebc1-436">`true` - Place a space character after the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="eebc1-437">`false` - Supprimer l’espace après le signe deux-points pour les bases ou les interfaces dans une déclaration de type</span><span class="sxs-lookup"><span data-stu-id="eebc1-437">`false` - Remove space after the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="eebc1-438">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-438">Code examples:</span></span>

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a><span data-ttu-id="eebc1-439">csharp\_space\_around\_binary_operators</span><span class="sxs-lookup"><span data-stu-id="eebc1-439">csharp\_space\_around\_binary_operators</span></span>

|<span data-ttu-id="eebc1-440">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-440">Property</span></span>|<span data-ttu-id="eebc1-441">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-441">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-442">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-442">**Option name**</span></span> | <span data-ttu-id="eebc1-443">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="eebc1-443">csharp_space_around_binary_operators</span></span> |
| <span data-ttu-id="eebc1-444">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-444">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-445">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-445">C#</span></span> |
| <span data-ttu-id="eebc1-446">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-446">**Introduced version**</span></span> | <span data-ttu-id="eebc1-447">Visual Studio 2017 version 15.7</span><span class="sxs-lookup"><span data-stu-id="eebc1-447">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="eebc1-448">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-448">**Option values**</span></span> | <span data-ttu-id="eebc1-449">`before_and_after` - Insérer un espace avant et après l’opérateur binaire</span><span class="sxs-lookup"><span data-stu-id="eebc1-449">`before_and_after` - Insert space before and after the binary operator</span></span><br /><br /><span data-ttu-id="eebc1-450">`none` - Supprimer les espaces avant et après l’opérateur binaire</span><span class="sxs-lookup"><span data-stu-id="eebc1-450">`none` - Remove spaces before and after the binary operator</span></span><br /><br /><span data-ttu-id="eebc1-451">`ignore` - Ignorer les espaces autour des opérateurs binaires</span><span class="sxs-lookup"><span data-stu-id="eebc1-451">`ignore` - Ignore spaces around binary operators</span></span> |

<span data-ttu-id="eebc1-452">Si vous omettez cette règle, ou si vous utilisez une valeur autre que `before_and_after`, `none` ou `ignore`, le paramètre n’est pas appliqué.</span><span class="sxs-lookup"><span data-stu-id="eebc1-452">If you omit this rule, or use a value other than `before_and_after`, `none`, or `ignore`, the setting is not applied.</span></span>

<span data-ttu-id="eebc1-453">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-453">Code examples:</span></span>

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a><span data-ttu-id="eebc1-454">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-454">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>

|<span data-ttu-id="eebc1-455">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-455">Property</span></span>|<span data-ttu-id="eebc1-456">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-456">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-457">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-457">**Option name**</span></span> | <span data-ttu-id="eebc1-458">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-458">csharp_space_between_method_declaration_parameter_list_parentheses</span></span> |
| <span data-ttu-id="eebc1-459">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-459">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-460">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-460">C#</span></span> |
| <span data-ttu-id="eebc1-461">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-461">**Introduced version**</span></span> | <span data-ttu-id="eebc1-462">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-462">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-463">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-463">**Option values**</span></span> | <span data-ttu-id="eebc1-464">`true` - Placez un espace après la parenthèse ouvrante et avant la parenthèse fermante d’une liste de paramètres de déclaration de méthode.</span><span class="sxs-lookup"><span data-stu-id="eebc1-464">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span><br /><br /><span data-ttu-id="eebc1-465">`false` - Supprimer les espaces après la parenthèse ouvrante et avant la parenthèse fermante d’une liste de paramètres de déclaration de méthode</span><span class="sxs-lookup"><span data-stu-id="eebc1-465">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span> |

<span data-ttu-id="eebc1-466">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-466">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a><span data-ttu-id="eebc1-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="eebc1-468">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-468">Property</span></span>|<span data-ttu-id="eebc1-469">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-469">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-470">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-470">**Option name**</span></span> | <span data-ttu-id="eebc1-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="eebc1-472">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-472">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-473">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-473">C#</span></span> |
| <span data-ttu-id="eebc1-474">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-474">**Introduced version**</span></span> | <span data-ttu-id="eebc1-475">Visual Studio 2017 version 15.7</span><span class="sxs-lookup"><span data-stu-id="eebc1-475">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="eebc1-476">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-476">**Option values**</span></span> | <span data-ttu-id="eebc1-477">`true` - Insérer un espace dans les parenthèses de liste de paramètres vides pour une déclaration de méthode</span><span class="sxs-lookup"><span data-stu-id="eebc1-477">`true` - Insert space within empty parameter list parentheses for a method declaration</span></span><br /><br /><span data-ttu-id="eebc1-478">`false` - Supprimer l’espace dans les parenthèses de liste de paramètres vides pour une déclaration de méthode</span><span class="sxs-lookup"><span data-stu-id="eebc1-478">`false` - Remove space within empty parameter list parentheses for a method declaration</span></span> |

<span data-ttu-id="eebc1-479">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-479">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a><span data-ttu-id="eebc1-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="eebc1-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>

|<span data-ttu-id="eebc1-481">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-481">Property</span></span>|<span data-ttu-id="eebc1-482">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-482">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-483">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-483">**Option name**</span></span> | <span data-ttu-id="eebc1-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="eebc1-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span> |
| <span data-ttu-id="eebc1-485">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-485">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-486">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-486">C#</span></span> |
| <span data-ttu-id="eebc1-487">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-487">**Option values**</span></span> | <span data-ttu-id="eebc1-488">`true` - Placer un espace entre le nom de la méthode et la parenthèse ouvrante dans la déclaration de méthode</span><span class="sxs-lookup"><span data-stu-id="eebc1-488">`true` - Place a space character between the method name and opening parenthesis in the method declaration</span></span><br /><br /><span data-ttu-id="eebc1-489">`false` - Supprimer les espaces entre le nom de la méthode et la parenthèse ouvrante dans la déclaration de méthode</span><span class="sxs-lookup"><span data-stu-id="eebc1-489">`false` - Remove space characters between the method name and opening parenthesis in the method declaration</span></span> |

<span data-ttu-id="eebc1-490">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-490">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a><span data-ttu-id="eebc1-491">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-491">csharp_space_between_method_call_parameter_list_parentheses</span></span>

|<span data-ttu-id="eebc1-492">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-492">Property</span></span>|<span data-ttu-id="eebc1-493">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-493">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-494">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-494">**Option name**</span></span> | <span data-ttu-id="eebc1-495">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-495">csharp_space_between_method_call_parameter_list_parentheses</span></span> |
| <span data-ttu-id="eebc1-496">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-496">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-497">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-497">C#</span></span> |
| <span data-ttu-id="eebc1-498">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-498">**Introduced version**</span></span> | <span data-ttu-id="eebc1-499">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-499">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-500">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-500">**Option values**</span></span> | <span data-ttu-id="eebc1-501">`true` - Placer un caractère d’espacement après la parenthèse ouvrante et avant la parenthèse fermante d’un appel de méthode</span><span class="sxs-lookup"><span data-stu-id="eebc1-501">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method call</span></span><br /><br /><span data-ttu-id="eebc1-502">`false` - Supprimer les espaces après la parenthèse ouvrante et avant la parenthèse fermante d’un appel de méthode</span><span class="sxs-lookup"><span data-stu-id="eebc1-502">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method call</span></span> |

<span data-ttu-id="eebc1-503">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-503">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a><span data-ttu-id="eebc1-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="eebc1-505">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-505">Property</span></span>|<span data-ttu-id="eebc1-506">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-506">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-507">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-507">**Option name**</span></span> | <span data-ttu-id="eebc1-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="eebc1-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="eebc1-509">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-509">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-510">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-510">C#</span></span> |
| <span data-ttu-id="eebc1-511">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-511">**Introduced version**</span></span> | <span data-ttu-id="eebc1-512">Visual Studio 2017 version 15.7</span><span class="sxs-lookup"><span data-stu-id="eebc1-512">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="eebc1-513">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-513">**Option values**</span></span> | <span data-ttu-id="eebc1-514">`true` - Insérer un espace dans les parenthèses de la liste d’arguments vide</span><span class="sxs-lookup"><span data-stu-id="eebc1-514">`true` - Insert space within empty argument list parentheses</span></span><br /><br /><span data-ttu-id="eebc1-515">`false` - Supprimer un espace dans les parenthèses de la liste d’arguments vide</span><span class="sxs-lookup"><span data-stu-id="eebc1-515">`false` - Remove space within empty argument list parentheses</span></span> |

<span data-ttu-id="eebc1-516">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-516">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a><span data-ttu-id="eebc1-517">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="eebc1-517">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>

|<span data-ttu-id="eebc1-518">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-518">Property</span></span>|<span data-ttu-id="eebc1-519">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-519">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-520">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-520">**Option name**</span></span> | <span data-ttu-id="eebc1-521">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="eebc1-521">csharp_space_between_method_call_name_and_opening_parenthesis</span></span> |
| <span data-ttu-id="eebc1-522">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-522">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-523">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-523">C#</span></span> |
| <span data-ttu-id="eebc1-524">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-524">**Introduced version**</span></span> | <span data-ttu-id="eebc1-525">Visual Studio 2017 version 15.7</span><span class="sxs-lookup"><span data-stu-id="eebc1-525">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="eebc1-526">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-526">**Option values**</span></span> | <span data-ttu-id="eebc1-527">`true` - Insérer un espace entre le nom d’appel de méthode et la parenthèse ouvrante</span><span class="sxs-lookup"><span data-stu-id="eebc1-527">`true` - Insert space between method call name and opening parenthesis</span></span><br /><br /><span data-ttu-id="eebc1-528">`false` - Supprimer l’espace entre le nom d’appel de méthode et la parenthèse ouvrante</span><span class="sxs-lookup"><span data-stu-id="eebc1-528">`false` - Remove space between method call name and opening parenthesis</span></span> |

<span data-ttu-id="eebc1-529">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-529">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a><span data-ttu-id="eebc1-530">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="eebc1-530">csharp_space_after_comma</span></span>

|<span data-ttu-id="eebc1-531">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-531">Property</span></span>|<span data-ttu-id="eebc1-532">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-532">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-533">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-533">**Option name**</span></span> | <span data-ttu-id="eebc1-534">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="eebc1-534">csharp_space_after_comma</span></span> |
| <span data-ttu-id="eebc1-535">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-535">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-536">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-536">C#</span></span> |
| <span data-ttu-id="eebc1-537">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-537">**Option values**</span></span> | <span data-ttu-id="eebc1-538">`true` - Insérer un espace après une virgule</span><span class="sxs-lookup"><span data-stu-id="eebc1-538">`true` - Insert space after a comma</span></span><br /><br /><span data-ttu-id="eebc1-539">`false` - Supprimer l’espace après une virgule</span><span class="sxs-lookup"><span data-stu-id="eebc1-539">`false` - Remove space after a comma</span></span> |

<span data-ttu-id="eebc1-540">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-540">Code examples:</span></span>

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a><span data-ttu-id="eebc1-541">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="eebc1-541">csharp_space_before_comma</span></span>

|<span data-ttu-id="eebc1-542">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-542">Property</span></span>|<span data-ttu-id="eebc1-543">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-543">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-544">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-544">**Option name**</span></span> | <span data-ttu-id="eebc1-545">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="eebc1-545">csharp_space_before_comma</span></span> |
| <span data-ttu-id="eebc1-546">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-546">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-547">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-547">C#</span></span> |
| <span data-ttu-id="eebc1-548">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-548">**Option values**</span></span> | <span data-ttu-id="eebc1-549">`true` - Insérer un espace avant une virgule</span><span class="sxs-lookup"><span data-stu-id="eebc1-549">`true` - Insert space before a comma</span></span><br /><br /><span data-ttu-id="eebc1-550">`false` - Supprimer l’espace avant une virgule</span><span class="sxs-lookup"><span data-stu-id="eebc1-550">`false` - Remove space before a comma</span></span> |

<span data-ttu-id="eebc1-551">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-551">Code examples:</span></span>

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a><span data-ttu-id="eebc1-552">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="eebc1-552">csharp_space_after_dot</span></span>

|<span data-ttu-id="eebc1-553">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-553">Property</span></span>|<span data-ttu-id="eebc1-554">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-554">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-555">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-555">**Option name**</span></span> | <span data-ttu-id="eebc1-556">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="eebc1-556">csharp_space_after_dot</span></span> |
| <span data-ttu-id="eebc1-557">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-557">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-558">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-558">C#</span></span> |
| <span data-ttu-id="eebc1-559">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-559">**Option values**</span></span> | <span data-ttu-id="eebc1-560">`true` - Insérer un espace après un point</span><span class="sxs-lookup"><span data-stu-id="eebc1-560">`true` - Insert space after a dot</span></span><br /><br /><span data-ttu-id="eebc1-561">`false` - Supprimer l’espace après un point</span><span class="sxs-lookup"><span data-stu-id="eebc1-561">`false` - Remove space after a dot</span></span> |

<span data-ttu-id="eebc1-562">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-562">Code examples:</span></span>

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a><span data-ttu-id="eebc1-563">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="eebc1-563">csharp_space_before_dot</span></span>

|<span data-ttu-id="eebc1-564">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-564">Property</span></span>|<span data-ttu-id="eebc1-565">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-565">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-566">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-566">**Option name**</span></span> | <span data-ttu-id="eebc1-567">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="eebc1-567">csharp_space_before_dot</span></span> |
| <span data-ttu-id="eebc1-568">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-568">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-569">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-569">C#</span></span> |
| <span data-ttu-id="eebc1-570">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-570">**Option values**</span></span> | <span data-ttu-id="eebc1-571">`true` - Insérer un espace avant un point</span><span class="sxs-lookup"><span data-stu-id="eebc1-571">`true` - Insert space before a dot</span></span> <br /><br /><span data-ttu-id="eebc1-572">`false` - Supprimer l’espace avant un point</span><span class="sxs-lookup"><span data-stu-id="eebc1-572">`false` - Remove space before a dot</span></span> |

<span data-ttu-id="eebc1-573">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-573">Code examples:</span></span>

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a><span data-ttu-id="eebc1-574">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="eebc1-574">csharp_space_after_semicolon_in_for_statement</span></span>

|<span data-ttu-id="eebc1-575">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-575">Property</span></span>|<span data-ttu-id="eebc1-576">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-576">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-577">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-577">**Option name**</span></span> | <span data-ttu-id="eebc1-578">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="eebc1-578">csharp_space_after_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="eebc1-579">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-579">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-580">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-580">C#</span></span> |
| <span data-ttu-id="eebc1-581">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-581">**Option values**</span></span> | <span data-ttu-id="eebc1-582">`true` - Insérer un espace après chaque point-virgule dans une instruction `for`</span><span class="sxs-lookup"><span data-stu-id="eebc1-582">`true` - Insert space after each semicolon in a `for` statement</span></span><br /><br /><span data-ttu-id="eebc1-583">`false` - Supprimer l’espace après chaque point-virgule dans une instruction `for`</span><span class="sxs-lookup"><span data-stu-id="eebc1-583">`false` - Remove space after each semicolon in a `for` statement</span></span> |

<span data-ttu-id="eebc1-584">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-584">Code examples:</span></span>

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a><span data-ttu-id="eebc1-585">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="eebc1-585">csharp_space_before_semicolon_in_for_statement</span></span>

|<span data-ttu-id="eebc1-586">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-586">Property</span></span>|<span data-ttu-id="eebc1-587">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-587">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-588">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-588">**Option name**</span></span> | <span data-ttu-id="eebc1-589">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="eebc1-589">csharp_space_before_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="eebc1-590">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-590">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-591">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-591">C#</span></span> |
| <span data-ttu-id="eebc1-592">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-592">**Option values**</span></span> | <span data-ttu-id="eebc1-593">`true` - Insérer un espace avant chaque point-virgule dans une instruction `for`</span><span class="sxs-lookup"><span data-stu-id="eebc1-593">`true` - Insert space before each semicolon in a `for` statement</span></span> <br /><br /><span data-ttu-id="eebc1-594">`false` - Supprimer l’espace avant chaque point-virgule dans une instruction `for`</span><span class="sxs-lookup"><span data-stu-id="eebc1-594">`false` - Remove space before each semicolon in a `for` statement</span></span> |

<span data-ttu-id="eebc1-595">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-595">Code examples:</span></span>

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a><span data-ttu-id="eebc1-596">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="eebc1-596">csharp_space_around_declaration_statements</span></span>

|<span data-ttu-id="eebc1-597">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-597">Property</span></span>|<span data-ttu-id="eebc1-598">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-598">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-599">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-599">**Option name**</span></span> | <span data-ttu-id="eebc1-600">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="eebc1-600">csharp_space_around_declaration_statements</span></span> |
| <span data-ttu-id="eebc1-601">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-601">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-602">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-602">C#</span></span> |
| <span data-ttu-id="eebc1-603">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-603">**Option values**</span></span> | <span data-ttu-id="eebc1-604">`ignore` - Ne pas supprimer les espaces supplémentaires dans les instructions de déclaration</span><span class="sxs-lookup"><span data-stu-id="eebc1-604">`ignore` - Don't remove extra space characters in declaration statements</span></span><br /><br /><span data-ttu-id="eebc1-605">`false` - Supprimer les espaces supplémentaires dans les instructions de déclaration</span><span class="sxs-lookup"><span data-stu-id="eebc1-605">`false` - Remove extra space characters in declaration statements</span></span> |

<span data-ttu-id="eebc1-606">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-606">Code examples:</span></span>

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a><span data-ttu-id="eebc1-607">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="eebc1-607">csharp_space_before_open_square_brackets</span></span>

|<span data-ttu-id="eebc1-608">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-608">Property</span></span>|<span data-ttu-id="eebc1-609">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-609">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-610">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-610">**Option name**</span></span> | <span data-ttu-id="eebc1-611">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="eebc1-611">csharp_space_before_open_square_brackets</span></span> |
| <span data-ttu-id="eebc1-612">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-612">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-613">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-613">C#</span></span> |
| <span data-ttu-id="eebc1-614">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-614">**Option values**</span></span> | <span data-ttu-id="eebc1-615">`true` - Insérer un espace avant les crochets ouvrants `[`</span><span class="sxs-lookup"><span data-stu-id="eebc1-615">`true` - Insert space before opening square brackets `[`</span></span> <br /><br /><span data-ttu-id="eebc1-616">`false` - Supprimer l’espace avant les crochets ouvrants `[`</span><span class="sxs-lookup"><span data-stu-id="eebc1-616">`false` - Remove space before opening square brackets `[`</span></span> |

<span data-ttu-id="eebc1-617">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-617">Code examples:</span></span>

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a><span data-ttu-id="eebc1-618">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="eebc1-618">csharp_space_between_empty_square_brackets</span></span>

|<span data-ttu-id="eebc1-619">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-619">Property</span></span>|<span data-ttu-id="eebc1-620">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-620">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-621">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-621">**Option name**</span></span> | <span data-ttu-id="eebc1-622">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="eebc1-622">csharp_space_between_empty_square_brackets</span></span> |
| <span data-ttu-id="eebc1-623">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-623">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-624">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-624">C#</span></span> |
| <span data-ttu-id="eebc1-625">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-625">**Option values**</span></span> | <span data-ttu-id="eebc1-626">`true` - Insérer un espace entre des crochets vides `[ ]`</span><span class="sxs-lookup"><span data-stu-id="eebc1-626">`true` - Insert space between empty square brackets `[ ]`</span></span> <br /><br /><span data-ttu-id="eebc1-627">`false` - Supprimer l’espace entre des crochets vides `[]`</span><span class="sxs-lookup"><span data-stu-id="eebc1-627">`false` - Remove space between empty square brackets `[]`</span></span> |

<span data-ttu-id="eebc1-628">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-628">Code examples:</span></span>

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a><span data-ttu-id="eebc1-629">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="eebc1-629">csharp_space_between_square_brackets</span></span>

|<span data-ttu-id="eebc1-630">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-630">Property</span></span>|<span data-ttu-id="eebc1-631">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-631">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-632">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-632">**Option name**</span></span> | <span data-ttu-id="eebc1-633">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="eebc1-633">csharp_space_between_square_brackets</span></span> |
| <span data-ttu-id="eebc1-634">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-634">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-635">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-635">C#</span></span> |
| <span data-ttu-id="eebc1-636">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-636">**Option values**</span></span> | <span data-ttu-id="eebc1-637">`true` - Insérer des espaces entre des crochets non vides `[ 0 ]`</span><span class="sxs-lookup"><span data-stu-id="eebc1-637">`true` - Insert space characters in non-empty square brackets `[ 0 ]`</span></span> <br /><br /><span data-ttu-id="eebc1-638">`false` - Supprimer des espaces entre des crochets non vides `[0]`</span><span class="sxs-lookup"><span data-stu-id="eebc1-638">`false` - Remove space characters in non-empty square brackets `[0]`</span></span> |

<span data-ttu-id="eebc1-639">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-639">Code examples:</span></span>

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a><span data-ttu-id="eebc1-640">Options d’encapsulage</span><span class="sxs-lookup"><span data-stu-id="eebc1-640">Wrap options</span></span>

<span data-ttu-id="eebc1-641">Ces règles de mise en forme concernent l’utilisation de lignes uniques ou de lignes distinctes pour les instructions et les blocs de code.</span><span class="sxs-lookup"><span data-stu-id="eebc1-641">These formatting rules concern the use of single lines versus separate lines for statements and code blocks.</span></span>

<span data-ttu-id="eebc1-642">Exemple de fichier *.editorconfig* :</span><span class="sxs-lookup"><span data-stu-id="eebc1-642">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a><span data-ttu-id="eebc1-643">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="eebc1-643">csharp_preserve_single_line_statements</span></span>

|<span data-ttu-id="eebc1-644">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-644">Property</span></span>|<span data-ttu-id="eebc1-645">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-645">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-646">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-646">**Option name**</span></span> | <span data-ttu-id="eebc1-647">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="eebc1-647">csharp_preserve_single_line_statements</span></span> |
| <span data-ttu-id="eebc1-648">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-648">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-649">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-649">C#</span></span> |
| <span data-ttu-id="eebc1-650">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-650">**Introduced version**</span></span> | <span data-ttu-id="eebc1-651">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-651">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-652">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-652">**Option values**</span></span> | <span data-ttu-id="eebc1-653">`true` - Laisser les instructions et les déclarations de membre sur la même ligne</span><span class="sxs-lookup"><span data-stu-id="eebc1-653">`true` - Leave statements and member declarations on the same line</span></span><br /><br /><span data-ttu-id="eebc1-654">`false` - Laisser les instructions et les déclarations de membre sur des lignes différentes</span><span class="sxs-lookup"><span data-stu-id="eebc1-654">`false` - Leave statements and member declarations on different lines</span></span> |

<span data-ttu-id="eebc1-655">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-655">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a><span data-ttu-id="eebc1-656">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="eebc1-656">csharp_preserve_single_line_blocks</span></span>

|<span data-ttu-id="eebc1-657">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-657">Property</span></span>|<span data-ttu-id="eebc1-658">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-658">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-659">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-659">**Option name**</span></span> | <span data-ttu-id="eebc1-660">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="eebc1-660">csharp_preserve_single_line_blocks</span></span> |
| <span data-ttu-id="eebc1-661">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-661">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-662">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-662">C#</span></span> |
| <span data-ttu-id="eebc1-663">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-663">**Introduced version**</span></span> | <span data-ttu-id="eebc1-664">Visual Studio 2017 version 15.3</span><span class="sxs-lookup"><span data-stu-id="eebc1-664">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="eebc1-665">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-665">**Option values**</span></span> | <span data-ttu-id="eebc1-666">`true` - Laisser le bloc de code sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="eebc1-666">`true` - Leave code block on single line</span></span><br /><br /><span data-ttu-id="eebc1-667">`false` - Laisser le bloc de code sur des lignes distinctes</span><span class="sxs-lookup"><span data-stu-id="eebc1-667">`false` - Leave code block on separate lines</span></span> |

<span data-ttu-id="eebc1-668">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-668">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a><span data-ttu-id="eebc1-669">Utilisation des options de directive</span><span class="sxs-lookup"><span data-stu-id="eebc1-669">Using directive options</span></span>

<span data-ttu-id="eebc1-670">Cette règle de mise en forme concerne l’utilisation des directives using placées à l’intérieur et à l’extérieur d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="eebc1-670">This formatting rule concerns the use of using directives being placed inside versus outside a namespace.</span></span>

<span data-ttu-id="eebc1-671">Exemple de fichier *.editorconfig* :</span><span class="sxs-lookup"><span data-stu-id="eebc1-671">Example *.editorconfig* file:</span></span>

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a><span data-ttu-id="eebc1-672">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="eebc1-672">csharp_using_directive_placement</span></span>

|<span data-ttu-id="eebc1-673">Propriété</span><span class="sxs-lookup"><span data-stu-id="eebc1-673">Property</span></span>|<span data-ttu-id="eebc1-674">Valeur</span><span class="sxs-lookup"><span data-stu-id="eebc1-674">Value</span></span>|
|-|-|
| <span data-ttu-id="eebc1-675">**Nom de l’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-675">**Option name**</span></span> | <span data-ttu-id="eebc1-676">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="eebc1-676">csharp_using_directive_placement</span></span> |
| <span data-ttu-id="eebc1-677">**Langues applicables**</span><span class="sxs-lookup"><span data-stu-id="eebc1-677">**Applicable languages**</span></span> | <span data-ttu-id="eebc1-678">C#</span><span class="sxs-lookup"><span data-stu-id="eebc1-678">C#</span></span> |
| <span data-ttu-id="eebc1-679">**Version introduite**</span><span class="sxs-lookup"><span data-stu-id="eebc1-679">**Introduced version**</span></span> | <span data-ttu-id="eebc1-680">Visual Studio 2019 version 16.1</span><span class="sxs-lookup"><span data-stu-id="eebc1-680">Visual Studio 2019 version 16.1</span></span> |
| <span data-ttu-id="eebc1-681">**Valeurs d’option**</span><span class="sxs-lookup"><span data-stu-id="eebc1-681">**Option values**</span></span> | <span data-ttu-id="eebc1-682">`outside_namespace` -Laissez les directives using en dehors de l’espace de noms</span><span class="sxs-lookup"><span data-stu-id="eebc1-682">`outside_namespace` - Leave using directives outside namespace</span></span><br /><br /><span data-ttu-id="eebc1-683">`inside_namespace` -Laissez les directives using à l’intérieur de l’espace de noms</span><span class="sxs-lookup"><span data-stu-id="eebc1-683">`inside_namespace` - Leave using directives inside namespace</span></span> |

<span data-ttu-id="eebc1-684">Exemples de code :</span><span class="sxs-lookup"><span data-stu-id="eebc1-684">Code examples:</span></span>

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a><span data-ttu-id="eebc1-685">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eebc1-685">See also</span></span>

- [<span data-ttu-id="eebc1-686">Règles de langage</span><span class="sxs-lookup"><span data-stu-id="eebc1-686">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="eebc1-687">Règles d’affectation des noms</span><span class="sxs-lookup"><span data-stu-id="eebc1-687">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="eebc1-688">Référence des règles de style de code .NET</span><span class="sxs-lookup"><span data-stu-id="eebc1-688">.NET code style rules reference</span></span>](index.md)

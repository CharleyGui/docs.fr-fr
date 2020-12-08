---
title: Options de configuration d’une règle de qualité du code
description: Découvrez comment spécifier des options de configuration supplémentaires pour les règles de qualité du code.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: af2984e73c554e8a1e1b32df9460933f86cc41be
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96587127"
---
# <a name="code-quality-rule-configuration-options"></a><span data-ttu-id="04181-103">Options de configuration d’une règle de qualité du code</span><span class="sxs-lookup"><span data-stu-id="04181-103">Code quality rule configuration options</span></span>

<span data-ttu-id="04181-104">Les règles de *qualité du code* comportent des options de configuration supplémentaires, outre la simple [configuration de leur gravité](configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="04181-104">The *code quality* rules have additional configuration options, besides just [configuring their severity](configuration-options.md#severity-level).</span></span> <span data-ttu-id="04181-105">Par exemple, chaque analyseur de qualité du code peut être configuré pour s’appliquer uniquement à des parties spécifiques de votre code base.</span><span class="sxs-lookup"><span data-stu-id="04181-105">For example, each code quality analyzer can be configured to only apply to specific parts of your codebase.</span></span> <span data-ttu-id="04181-106">Vous spécifiez ces options en ajoutant des paires clé-valeur au même [EditorConfig](https://editorconfig.org) fichier où vous spécifiez des gravités de règle et des préférences générales de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="04181-106">You specify these options by adding key-value pairs to the same [EditorConfig](https://editorconfig.org) file where you specify rule severities and general editor preferences.</span></span>

## <a name="option-scopes"></a><span data-ttu-id="04181-107">Étendues des options</span><span class="sxs-lookup"><span data-stu-id="04181-107">Option scopes</span></span>

<span data-ttu-id="04181-108">Chaque option d’affinage peut être configurée pour toutes les règles, pour une catégorie de règles (par exemple, la sécurité ou la conception) ou pour une règle spécifique.</span><span class="sxs-lookup"><span data-stu-id="04181-108">Each refining option can be configured for all rules, for a category of rules (for example, Security or Design), or for a specific rule.</span></span>

### <a name="all-rules"></a><span data-ttu-id="04181-109">Toutes les règles</span><span class="sxs-lookup"><span data-stu-id="04181-109">All rules</span></span>

<span data-ttu-id="04181-110">La syntaxe de configuration d’une option pour *toutes les* règles est la suivante :</span><span class="sxs-lookup"><span data-stu-id="04181-110">The syntax for configuring an option for *all* rules is as follows:</span></span>

|<span data-ttu-id="04181-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04181-111">Syntax</span></span>|<span data-ttu-id="04181-112"> Exemple</span><span class="sxs-lookup"><span data-stu-id="04181-112">Example</span></span>|
|-|-|
| <span data-ttu-id="04181-113">dotnet_code_quality. Nomoptin = OptionValue</span><span class="sxs-lookup"><span data-stu-id="04181-113">dotnet_code_quality.OptionName = OptionValue</span></span> | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a><span data-ttu-id="04181-114">Catégorie de règles</span><span class="sxs-lookup"><span data-stu-id="04181-114">Category of rules</span></span>

<span data-ttu-id="04181-115">La syntaxe permettant de configurer une option pour une *catégorie* de règles (par exemple, le nom, la conception ou la performance) est la suivante :</span><span class="sxs-lookup"><span data-stu-id="04181-115">The syntax for configuring an option for a *category* of rules (such as Naming, Design, or Performance) is as follows:</span></span>

|<span data-ttu-id="04181-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04181-116">Syntax</span></span>|<span data-ttu-id="04181-117"> Exemple</span><span class="sxs-lookup"><span data-stu-id="04181-117">Example</span></span>|
|-|-|
| <span data-ttu-id="04181-118">dotnet_code_quality. RuleCategory. OptionName = OptionValue</span><span class="sxs-lookup"><span data-stu-id="04181-118">dotnet_code_quality.RuleCategory.OptionName = OptionValue</span></span> | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a><span data-ttu-id="04181-119">Règle spécifique</span><span class="sxs-lookup"><span data-stu-id="04181-119">Specific rule</span></span>

<span data-ttu-id="04181-120">La syntaxe de configuration d’une option pour une règle *spécifique* est la suivante :</span><span class="sxs-lookup"><span data-stu-id="04181-120">The syntax for configuring an option for a *specific* rule is as follows:</span></span>

|<span data-ttu-id="04181-121">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04181-121">Syntax</span></span>|<span data-ttu-id="04181-122"> Exemple</span><span class="sxs-lookup"><span data-stu-id="04181-122">Example</span></span>|
|-|-|
| <span data-ttu-id="04181-123">dotnet_code_quality. RuleId. OptionName = OptionValue</span><span class="sxs-lookup"><span data-stu-id="04181-123">dotnet_code_quality.RuleId.OptionName = OptionValue</span></span> | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="options"></a><span data-ttu-id="04181-124">Options</span><span class="sxs-lookup"><span data-stu-id="04181-124">Options</span></span>

<span data-ttu-id="04181-125">Cette section répertorie certaines des options disponibles.</span><span class="sxs-lookup"><span data-stu-id="04181-125">This section lists some of the available options.</span></span> <span data-ttu-id="04181-126">Pour afficher la liste complète des options disponibles, consultez [configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md).</span><span class="sxs-lookup"><span data-stu-id="04181-126">To see the full list of available options, see [Analyzer configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md).</span></span>

### <a name="api_surface"></a><span data-ttu-id="04181-127">api_surface</span><span class="sxs-lookup"><span data-stu-id="04181-127">api_surface</span></span>

| <span data-ttu-id="04181-128">Description</span><span class="sxs-lookup"><span data-stu-id="04181-128">Description</span></span> | <span data-ttu-id="04181-129">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-129">Allowable values</span></span> | <span data-ttu-id="04181-130">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-130">Default value</span></span> | <span data-ttu-id="04181-131">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-131">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-132">La partie de la surface d’API à analyser</span><span class="sxs-lookup"><span data-stu-id="04181-132">Which part of the API surface to analyze</span></span> | `public`<br/><span data-ttu-id="04181-133">`internal` ou `friend`</span><span class="sxs-lookup"><span data-stu-id="04181-133">`internal` or `friend`</span></span><br/>`private`<br/>`all`<br/><br/><span data-ttu-id="04181-134">Séparez plusieurs valeurs par une virgule (,)</span><span class="sxs-lookup"><span data-stu-id="04181-134">Separate multiple values with a comma (,)</span></span> | `public` | <span data-ttu-id="04181-135">CA1000 [CA1003](quality-rules/ca1003.md) [CA1008](quality-rules/ca1008.md) [CA1010](quality-rules/ca1010.md) [CA1](quality-rules/ca1000.md)</span><span class="sxs-lookup"><span data-stu-id="04181-135">[CA1000](quality-rules/ca1000.md) [CA1003](quality-rules/ca1003.md) [CA1008](quality-rules/ca1008.md) [CA1010](quality-rules/ca1010.md)</span></span><br/><span data-ttu-id="04181-136">[CA1012](quality-rules/ca1012.md) - [1024](quality-rules/ca1024.md) [CA1027](quality-rules/ca1027.md) [CA1028](quality-rules/ca1028.md)</span><span class="sxs-lookup"><span data-stu-id="04181-136">[CA1012](quality-rules/ca1012.md) [CA1024](quality-rules/ca1024.md) [CA1027](quality-rules/ca1027.md) [CA1028](quality-rules/ca1028.md)</span></span><br/><span data-ttu-id="04181-137">[CA1030](quality-rules/ca1030.md) [CA1036](quality-rules/ca1036.md) [CA1040](quality-rules/ca1040.md) [CA1041](quality-rules/ca1041.md)</span><span class="sxs-lookup"><span data-stu-id="04181-137">[CA1030](quality-rules/ca1030.md) [CA1036](quality-rules/ca1036.md) [CA1040](quality-rules/ca1040.md) [CA1041](quality-rules/ca1041.md)</span></span><br/><span data-ttu-id="04181-138">[Ca1043](quality-rules/ca1043.md) [CA1044](quality-rules/ca1044.md) [CA1051](quality-rules/ca1051.md) [CA1052](quality-rules/ca1052.md)</span><span class="sxs-lookup"><span data-stu-id="04181-138">[CA1043](quality-rules/ca1043.md) [CA1044](quality-rules/ca1044.md) [CA1051](quality-rules/ca1051.md) [CA1052](quality-rules/ca1052.md)</span></span><br/><span data-ttu-id="04181-139">[CA1054](quality-rules/ca1054.md) [CA1055](quality-rules/ca1055.md) [CA1056](quality-rules/ca1056.md) ca--le ca- [1058](quality-rules/ca1058.md)</span><span class="sxs-lookup"><span data-stu-id="04181-139">[CA1054](quality-rules/ca1054.md) [CA1055](quality-rules/ca1055.md) [CA1056](quality-rules/ca1056.md) [CA1058](quality-rules/ca1058.md)</span></span><br/><span data-ttu-id="04181-140">[CA1063](quality-rules/ca1063.md) [CA1708](quality-rules/ca1708.md) [CA1710](quality-rules/ca1710.md) [CA1711](quality-rules/ca1711.md)</span><span class="sxs-lookup"><span data-stu-id="04181-140">[CA1063](quality-rules/ca1063.md) [CA1708](quality-rules/ca1708.md) [CA1710](quality-rules/ca1710.md) [CA1711](quality-rules/ca1711.md)</span></span><br/><span data-ttu-id="04181-141">[CA1714](quality-rules/ca1714.md) [CA1715](quality-rules/ca1715.md) [CA1716](quality-rules/ca1716.md) [ca1717](quality-rules/ca1717.md)</span><span class="sxs-lookup"><span data-stu-id="04181-141">[CA1714](quality-rules/ca1714.md) [CA1715](quality-rules/ca1715.md) [CA1716](quality-rules/ca1716.md) [CA1717](quality-rules/ca1717.md)</span></span><br/><span data-ttu-id="04181-142">[Ca1720](quality-rules/ca1720.md) [ca1721s](quality-rules/ca1721.md) [CA1725](quality-rules/ca1725.md) [CA1801](quality-rules/ca1801.md)</span><span class="sxs-lookup"><span data-stu-id="04181-142">[CA1720](quality-rules/ca1720.md) [CA1721](quality-rules/ca1721.md) [CA1725](quality-rules/ca1725.md) [CA1801](quality-rules/ca1801.md)</span></span><br/><span data-ttu-id="04181-143">[Ca1802](quality-rules/ca1802.md) [-1815](quality-rules/ca1815.md) [CA1819](quality-rules/ca1819.md) [CA2217](quality-rules/ca2217.md)</span><span class="sxs-lookup"><span data-stu-id="04181-143">[CA1802](quality-rules/ca1802.md) [CA1815](quality-rules/ca1815.md) [CA1819](quality-rules/ca1819.md) [CA2217](quality-rules/ca2217.md)</span></span><br/><span data-ttu-id="04181-144">[CA2225](quality-rules/ca2225.md) [CA2226](quality-rules/ca2226.md) [CA2231](quality-rules/ca2231.md) [CA2234](quality-rules/ca2234.md)</span><span class="sxs-lookup"><span data-stu-id="04181-144">[CA2225](quality-rules/ca2225.md) [CA2226](quality-rules/ca2226.md) [CA2231](quality-rules/ca2231.md) [CA2234](quality-rules/ca2234.md)</span></span><br/>|

### <a name="exclude_async_void_methods"></a><span data-ttu-id="04181-145">exclude_async_void_methods</span><span class="sxs-lookup"><span data-stu-id="04181-145">exclude_async_void_methods</span></span>

| <span data-ttu-id="04181-146">Description</span><span class="sxs-lookup"><span data-stu-id="04181-146">Description</span></span> | <span data-ttu-id="04181-147">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-147">Allowable values</span></span> | <span data-ttu-id="04181-148">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-148">Default value</span></span> | <span data-ttu-id="04181-149">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-149">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-150">Indique s’il faut ignorer les méthodes asynchrones qui ne retournent pas de valeur</span><span class="sxs-lookup"><span data-stu-id="04181-150">Whether to ignore asynchronous methods that don't return a value</span></span> | `true`<br/>`false` | `false` | [<span data-ttu-id="04181-151">CA2007</span><span class="sxs-lookup"><span data-stu-id="04181-151">CA2007</span></span>](quality-rules/ca2007.md) |

> [!NOTE]
> <span data-ttu-id="04181-152">Cette option a été nommée `skip_async_void_methods` dans une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="04181-152">This option was named `skip_async_void_methods` in an earlier version.</span></span>

### <a name="exclude_single_letter_type_parameters"></a><span data-ttu-id="04181-153">exclude_single_letter_type_parameters</span><span class="sxs-lookup"><span data-stu-id="04181-153">exclude_single_letter_type_parameters</span></span>

| <span data-ttu-id="04181-154">Description</span><span class="sxs-lookup"><span data-stu-id="04181-154">Description</span></span> | <span data-ttu-id="04181-155">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-155">Allowable values</span></span> | <span data-ttu-id="04181-156">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-156">Default value</span></span> | <span data-ttu-id="04181-157">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-157">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-158">Indique s’il faut exclure les [paramètres de type](../../csharp/programming-guide/generics/generic-type-parameters.md) à un seul caractère de la règle, par exemple `S` dans `Collection<S>`</span><span class="sxs-lookup"><span data-stu-id="04181-158">Whether to exclude single-character [type parameters](../../csharp/programming-guide/generics/generic-type-parameters.md) from the rule, for example, `S` in `Collection<S>`</span></span> | `true`<br/>`false` | `false` | [<span data-ttu-id="04181-159">CA1715</span><span class="sxs-lookup"><span data-stu-id="04181-159">CA1715</span></span>](quality-rules/ca1715.md) |

> [!NOTE]
> <span data-ttu-id="04181-160">Cette option a été nommée `allow_single_letter_type_parameters` dans une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="04181-160">This option was named `allow_single_letter_type_parameters` in an earlier version.</span></span>

### <a name="output_kind"></a><span data-ttu-id="04181-161">output_kind</span><span class="sxs-lookup"><span data-stu-id="04181-161">output_kind</span></span>

| <span data-ttu-id="04181-162">Description</span><span class="sxs-lookup"><span data-stu-id="04181-162">Description</span></span> | <span data-ttu-id="04181-163">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-163">Allowable values</span></span> | <span data-ttu-id="04181-164">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-164">Default value</span></span> | <span data-ttu-id="04181-165">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-165">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-166">Spécifie que le code d’un projet qui génère ce type d’assembly doit être analysé</span><span class="sxs-lookup"><span data-stu-id="04181-166">Specifies that code in a project that generates this type of assembly should be analyzed</span></span> | <span data-ttu-id="04181-167">Un ou plusieurs champs de l' <xref:Microsoft.CodeAnalysis.OutputKind> énumération</span><span class="sxs-lookup"><span data-stu-id="04181-167">One or more fields of the <xref:Microsoft.CodeAnalysis.OutputKind> enumeration</span></span><br/><br/><span data-ttu-id="04181-168">Séparez plusieurs valeurs par une virgule (,)</span><span class="sxs-lookup"><span data-stu-id="04181-168">Separate multiple values with a comma (,)</span></span> | <span data-ttu-id="04181-169">Tous les types de sortie</span><span class="sxs-lookup"><span data-stu-id="04181-169">All output kinds</span></span> | [<span data-ttu-id="04181-170">CA2007</span><span class="sxs-lookup"><span data-stu-id="04181-170">CA2007</span></span>](quality-rules/ca2007.md) |

### <a name="required_modifiers"></a><span data-ttu-id="04181-171">required_modifiers</span><span class="sxs-lookup"><span data-stu-id="04181-171">required_modifiers</span></span>

| <span data-ttu-id="04181-172">Description</span><span class="sxs-lookup"><span data-stu-id="04181-172">Description</span></span> | <span data-ttu-id="04181-173">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-173">Allowable values</span></span> | <span data-ttu-id="04181-174">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-174">Default value</span></span> | <span data-ttu-id="04181-175">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-175">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-176">Spécifie les modificateurs requis pour les API qui doivent être analysées</span><span class="sxs-lookup"><span data-stu-id="04181-176">Specifies the required modifiers for APIs that should be analyzed</span></span> | <span data-ttu-id="04181-177">Une ou plusieurs valeurs de la table de modificateurs autorisées ci-dessous</span><span class="sxs-lookup"><span data-stu-id="04181-177">One or more values from the below allowed modifiers table</span></span><br/><br/><span data-ttu-id="04181-178">Séparez plusieurs valeurs par une virgule (,)</span><span class="sxs-lookup"><span data-stu-id="04181-178">Separate multiple values with a comma (,)</span></span> | <span data-ttu-id="04181-179">Dépend de chaque règle</span><span class="sxs-lookup"><span data-stu-id="04181-179">Depends on each rule</span></span> | [<span data-ttu-id="04181-180">CA1802</span><span class="sxs-lookup"><span data-stu-id="04181-180">CA1802</span></span>](quality-rules/ca1802.md) |

| <span data-ttu-id="04181-181">Modificateur autorisé</span><span class="sxs-lookup"><span data-stu-id="04181-181">Allowed Modifier</span></span> | <span data-ttu-id="04181-182">Résumé</span><span class="sxs-lookup"><span data-stu-id="04181-182">Summary</span></span> |
| --- | --- |
| `none` | <span data-ttu-id="04181-183">Aucune exigence de modificateur</span><span class="sxs-lookup"><span data-stu-id="04181-183">No modifier requirement</span></span> |
| <span data-ttu-id="04181-184">`static` ou `Shared`</span><span class="sxs-lookup"><span data-stu-id="04181-184">`static` or `Shared`</span></span> | <span data-ttu-id="04181-185">Doit être déclarée comme `static` ( `Shared` dans Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04181-185">Must be declared as `static` (`Shared` in Visual Basic)</span></span> |
| `const` | <span data-ttu-id="04181-186">Doit être déclarée comme `const`</span><span class="sxs-lookup"><span data-stu-id="04181-186">Must be declared as `const`</span></span> |
| `readonly` | <span data-ttu-id="04181-187">Doit être déclarée comme `readonly`</span><span class="sxs-lookup"><span data-stu-id="04181-187">Must be declared as `readonly`</span></span> |
| `abstract` | <span data-ttu-id="04181-188">Doit être déclarée comme `abstract`</span><span class="sxs-lookup"><span data-stu-id="04181-188">Must be declared as `abstract`</span></span> |
| `virtual` | <span data-ttu-id="04181-189">Doit être déclarée comme `virtual`</span><span class="sxs-lookup"><span data-stu-id="04181-189">Must be declared as `virtual`</span></span> |
| `override` | <span data-ttu-id="04181-190">Doit être déclarée comme `override`</span><span class="sxs-lookup"><span data-stu-id="04181-190">Must be declared as `override`</span></span> |
| `sealed` | <span data-ttu-id="04181-191">Doit être déclarée comme `sealed`</span><span class="sxs-lookup"><span data-stu-id="04181-191">Must be declared as `sealed`</span></span> |
| `extern` | <span data-ttu-id="04181-192">Doit être déclarée comme `extern`</span><span class="sxs-lookup"><span data-stu-id="04181-192">Must be declared as `extern`</span></span> |
| `async` | <span data-ttu-id="04181-193">Doit être déclarée comme `async`</span><span class="sxs-lookup"><span data-stu-id="04181-193">Must be declared as `async`</span></span> |

### <a name="exclude_extension_method_this_parameter"></a><span data-ttu-id="04181-194">exclude_extension_method_this_parameter</span><span class="sxs-lookup"><span data-stu-id="04181-194">exclude_extension_method_this_parameter</span></span>

| <span data-ttu-id="04181-195">Description</span><span class="sxs-lookup"><span data-stu-id="04181-195">Description</span></span> | <span data-ttu-id="04181-196">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-196">Allowable values</span></span> | <span data-ttu-id="04181-197">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-197">Default value</span></span> | <span data-ttu-id="04181-198">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-198">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-199">Indique s’il faut ignorer l’analyse pour le `this` paramètre des méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="04181-199">Whether to skip analysis for the `this` parameter of extension methods</span></span> | `true`<br/>`false` | `false` | [<span data-ttu-id="04181-200">CA1062</span><span class="sxs-lookup"><span data-stu-id="04181-200">CA1062</span></span>](quality-rules/ca1062.md) |

### <a name="null_check_validation_methods"></a><span data-ttu-id="04181-201">null_check_validation_methods</span><span class="sxs-lookup"><span data-stu-id="04181-201">null_check_validation_methods</span></span>

| <span data-ttu-id="04181-202">Description</span><span class="sxs-lookup"><span data-stu-id="04181-202">Description</span></span> | <span data-ttu-id="04181-203">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-203">Allowable values</span></span> | <span data-ttu-id="04181-204">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-204">Default value</span></span> | <span data-ttu-id="04181-205">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-205">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-206">Noms des méthodes de validation de contrôle null qui valident que les arguments passés à la méthode sont non null</span><span class="sxs-lookup"><span data-stu-id="04181-206">Names of null-check validation methods that validate that arguments passed to the method are non-null</span></span> | <span data-ttu-id="04181-207">Formats de nom de méthode autorisés (séparés par `|` ) :</span><span class="sxs-lookup"><span data-stu-id="04181-207">Allowed method name formats (separated by `|`):</span></span><br/> <span data-ttu-id="04181-208">-Nom de méthode uniquement (comprend toutes les méthodes portant le nom, quel que soit le type ou l’espace de noms conteneur)</span><span class="sxs-lookup"><span data-stu-id="04181-208">- Method name only (includes all methods with the name, regardless of the containing type or namespace)</span></span><br/> <span data-ttu-id="04181-209">-Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole, avec un `M:` préfixe facultatif</span><span class="sxs-lookup"><span data-stu-id="04181-209">- Fully qualified names in the symbol's [documentation ID format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format), with an optional `M:` prefix</span></span> | <span data-ttu-id="04181-210">None</span><span class="sxs-lookup"><span data-stu-id="04181-210">None</span></span> | [<span data-ttu-id="04181-211">CA1062</span><span class="sxs-lookup"><span data-stu-id="04181-211">CA1062</span></span>](quality-rules/ca1062.md) |

### <a name="additional_string_formatting_methods"></a><span data-ttu-id="04181-212">additional_string_formatting_methods</span><span class="sxs-lookup"><span data-stu-id="04181-212">additional_string_formatting_methods</span></span>

| <span data-ttu-id="04181-213">Description</span><span class="sxs-lookup"><span data-stu-id="04181-213">Description</span></span> | <span data-ttu-id="04181-214">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-214">Allowable values</span></span> | <span data-ttu-id="04181-215">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-215">Default value</span></span> | <span data-ttu-id="04181-216">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-216">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-217">Noms des méthodes de mise en forme de chaînes supplémentaires</span><span class="sxs-lookup"><span data-stu-id="04181-217">Names of additional string formatting methods</span></span> | <span data-ttu-id="04181-218">Formats de nom de méthode autorisés (séparés par `|` ) :</span><span class="sxs-lookup"><span data-stu-id="04181-218">Allowed method name formats (separated by `|`):</span></span><br/> <span data-ttu-id="04181-219">-Nom de méthode uniquement (comprend toutes les méthodes portant le nom, quel que soit le type ou l’espace de noms conteneur)</span><span class="sxs-lookup"><span data-stu-id="04181-219">- Method name only (includes all methods with the name, regardless of the containing type or namespace)</span></span><br/> <span data-ttu-id="04181-220">-Noms qualifiés complets dans le format d' [ID de documentation](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)du symbole, avec un `M:` préfixe facultatif</span><span class="sxs-lookup"><span data-stu-id="04181-220">- Fully qualified names in the symbol's [documentation ID format](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format), with an optional `M:` prefix</span></span> | <span data-ttu-id="04181-221">None</span><span class="sxs-lookup"><span data-stu-id="04181-221">None</span></span> | [<span data-ttu-id="04181-222">CA2241</span><span class="sxs-lookup"><span data-stu-id="04181-222">CA2241</span></span>](quality-rules/ca2241.md) |

### <a name="excluded_type_names_with_derived_types"></a><span data-ttu-id="04181-223">excluded_type_names_with_derived_types</span><span class="sxs-lookup"><span data-stu-id="04181-223">excluded_type_names_with_derived_types</span></span>

| <span data-ttu-id="04181-224">Description</span><span class="sxs-lookup"><span data-stu-id="04181-224">Description</span></span> | <span data-ttu-id="04181-225">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-225">Allowable values</span></span> | <span data-ttu-id="04181-226">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-226">Default value</span></span> | <span data-ttu-id="04181-227">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-227">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-228">Les noms des types, de telle sorte que le type et tous ses types dérivés soient exclus pour l’analyse</span><span class="sxs-lookup"><span data-stu-id="04181-228">Names of types, such that the type and all its derived types are excluded for analysis</span></span> | <span data-ttu-id="04181-229">Formats de noms de symboles autorisés (séparés par `|` ) :</span><span class="sxs-lookup"><span data-stu-id="04181-229">Allowed symbol name formats (separated by `|`):</span></span><br/> <span data-ttu-id="04181-230">-Nom de type uniquement (comprend tous les types portant le nom, quel que soit le type ou l’espace de noms conteneur)</span><span class="sxs-lookup"><span data-stu-id="04181-230">- Type name only (includes all types with the name, regardless of the containing type or namespace)</span></span><br/> <span data-ttu-id="04181-231">-Noms qualifiés complets dans le format d' [ID de documentation](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)du symbole, avec un `T:` préfixe facultatif</span><span class="sxs-lookup"><span data-stu-id="04181-231">- Fully qualified names in the symbol's [documentation ID format](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format), with an optional `T:` prefix</span></span> | <span data-ttu-id="04181-232">None</span><span class="sxs-lookup"><span data-stu-id="04181-232">None</span></span> | [<span data-ttu-id="04181-233">CA1303</span><span class="sxs-lookup"><span data-stu-id="04181-233">CA1303</span></span>](quality-rules/ca1303.md) |

### <a name="excluded_symbol_names"></a><span data-ttu-id="04181-234">excluded_symbol_names</span><span class="sxs-lookup"><span data-stu-id="04181-234">excluded_symbol_names</span></span>

| <span data-ttu-id="04181-235">Description</span><span class="sxs-lookup"><span data-stu-id="04181-235">Description</span></span> | <span data-ttu-id="04181-236">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-236">Allowable values</span></span> | <span data-ttu-id="04181-237">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-237">Default value</span></span> | <span data-ttu-id="04181-238">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-238">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-239">Noms des symboles exclus pour l’analyse</span><span class="sxs-lookup"><span data-stu-id="04181-239">Names of symbols that are excluded for analysis</span></span> | <span data-ttu-id="04181-240">Formats de noms de symboles autorisés (séparés par `|` ) :</span><span class="sxs-lookup"><span data-stu-id="04181-240">Allowed symbol name formats (separated by `|`):</span></span><br/> <span data-ttu-id="04181-241">-Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur)</span><span class="sxs-lookup"><span data-stu-id="04181-241">- Symbol name only (includes all symbols with the name, regardless of the containing type or namespace)</span></span><br/> <span data-ttu-id="04181-242">-Noms qualifiés complets dans le format d' [ID de documentation](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)du symbole.</span><span class="sxs-lookup"><span data-stu-id="04181-242">- Fully qualified names in the symbol's [documentation ID format](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format).</span></span> <span data-ttu-id="04181-243">Chaque nom de symbole requiert un préfixe de type de symbole, tel que le préfixe `M:` pour les méthodes, le `T:` préfixe pour les types et le `N:` préfixe pour les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="04181-243">Each symbol name requires a symbol kind prefix, such as `M:` prefix for methods, `T:` prefix for types, and `N:` prefix for namespaces.</span></span><br/> <span data-ttu-id="04181-244">- `.ctor` pour les constructeurs et `.cctor` les constructeurs statiques</span><span class="sxs-lookup"><span data-stu-id="04181-244">- `.ctor` for constructors and `.cctor` for static constructors</span></span> | <span data-ttu-id="04181-245">None</span><span class="sxs-lookup"><span data-stu-id="04181-245">None</span></span> | <span data-ttu-id="04181-246">[CA1062](quality-rules/ca1062.md) [CA1303](quality-rules/ca1303.md) [Ca2](quality-rules/ca2000.md) [ca2100](quality-rules/ca2100.md) [ca2301](quality-rules/ca2301.md) [CA2302](quality-rules/ca2302.md)</span><span class="sxs-lookup"><span data-stu-id="04181-246">[CA1062](quality-rules/ca1062.md) [CA1303](quality-rules/ca1303.md) [CA2000](quality-rules/ca2000.md) [CA2100](quality-rules/ca2100.md) [CA2301](quality-rules/ca2301.md) [CA2302](quality-rules/ca2302.md)</span></span><br/><span data-ttu-id="04181-247">[CA2311](quality-rules/ca2311.md) [CA2312](quality-rules/ca2312.md) [CA2321](quality-rules/ca2321.md) [CA2322](quality-rules/ca2322.md) [CA2327](quality-rules/ca2327.md) [CA2328](quality-rules/ca2328.md)</span><span class="sxs-lookup"><span data-stu-id="04181-247">[CA2311](quality-rules/ca2311.md) [CA2312](quality-rules/ca2312.md) [CA2321](quality-rules/ca2321.md) [CA2322](quality-rules/ca2322.md) [CA2327](quality-rules/ca2327.md) [CA2328](quality-rules/ca2328.md)</span></span><br/><span data-ttu-id="04181-248">[CA2329](quality-rules/ca2329.md) [CA2330](quality-rules/ca2330.md) [CA3001](quality-rules/ca3001.md) [ca3002](quality-rules/ca3002.md) - [3003](quality-rules/ca3003.md) [ca3004](quality-rules/ca3004.md)</span><span class="sxs-lookup"><span data-stu-id="04181-248">[CA2329](quality-rules/ca2329.md) [CA2330](quality-rules/ca2330.md) [CA3001](quality-rules/ca3001.md) [CA3002](quality-rules/ca3002.md) [CA3003](quality-rules/ca3003.md) [CA3004](quality-rules/ca3004.md)</span></span><br/><span data-ttu-id="04181-249">[Ca3005](quality-rules/ca3005.md) [ca3006](quality-rules/ca3006.md) [CA3007](quality-rules/ca3007.md) [CA3008](quality-rules/ca3008.md) [CA3009](quality-rules/ca3009.md) [ca3010](quality-rules/ca3010.md)</span><span class="sxs-lookup"><span data-stu-id="04181-249">[CA3005](quality-rules/ca3005.md) [CA3006](quality-rules/ca3006.md) [CA3007](quality-rules/ca3007.md) [CA3008](quality-rules/ca3008.md) [CA3009](quality-rules/ca3009.md) [CA3010](quality-rules/ca3010.md)</span></span><br/><span data-ttu-id="04181-250">[CA3011](quality-rules/ca3011.md) [CA3012](quality-rules/ca3012.md) [CA5361](quality-rules/ca5361.md) CA5376 CA5377 [CA5378](quality-rules/ca5378.md)</span><span class="sxs-lookup"><span data-stu-id="04181-250">[CA3011](quality-rules/ca3011.md) [CA3012](quality-rules/ca3012.md) [CA5361](quality-rules/ca5361.md) CA5376 CA5377 [CA5378](quality-rules/ca5378.md)</span></span><br/><span data-ttu-id="04181-251">[CA5380](quality-rules/ca5380.md) [CA5381](quality-rules/ca5381.md) CA5382 CA5383 CA5384 CA5387</span><span class="sxs-lookup"><span data-stu-id="04181-251">[CA5380](quality-rules/ca5380.md) [CA5381](quality-rules/ca5381.md) CA5382 CA5383 CA5384 CA5387</span></span><br/><span data-ttu-id="04181-252">CA5388 [CA5389](quality-rules/ca5389.md) CA5390</span><span class="sxs-lookup"><span data-stu-id="04181-252">CA5388 [CA5389](quality-rules/ca5389.md) CA5390</span></span> |

### <a name="disallowed_symbol_names"></a><span data-ttu-id="04181-253">disallowed_symbol_names</span><span class="sxs-lookup"><span data-stu-id="04181-253">disallowed_symbol_names</span></span>

| <span data-ttu-id="04181-254">Description</span><span class="sxs-lookup"><span data-stu-id="04181-254">Description</span></span> | <span data-ttu-id="04181-255">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="04181-255">Allowable values</span></span> | <span data-ttu-id="04181-256">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="04181-256">Default value</span></span> | <span data-ttu-id="04181-257">Règles configurables</span><span class="sxs-lookup"><span data-stu-id="04181-257">Configurable rules</span></span> |
| - | - | - | - |
| <span data-ttu-id="04181-258">Noms des symboles non autorisés dans le contexte de l’analyse</span><span class="sxs-lookup"><span data-stu-id="04181-258">Names of symbols that are disallowed in the context of the analysis</span></span> | <span data-ttu-id="04181-259">Formats de noms de symboles autorisés (séparés par `|` ) :</span><span class="sxs-lookup"><span data-stu-id="04181-259">Allowed symbol name formats (separated by `|`):</span></span><br/> <span data-ttu-id="04181-260">-Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur)</span><span class="sxs-lookup"><span data-stu-id="04181-260">- Symbol name only (includes all symbols with the name, regardless of the containing type or namespace)</span></span><br/> <span data-ttu-id="04181-261">-Noms qualifiés complets dans le format d' [ID de documentation](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)du symbole.</span><span class="sxs-lookup"><span data-stu-id="04181-261">- Fully qualified names in the symbol's [documentation ID format](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format).</span></span> <span data-ttu-id="04181-262">Chaque nom de symbole requiert un préfixe de type de symbole, tel que le préfixe `M:` pour les méthodes, le `T:` préfixe pour les types et le `N:` préfixe pour les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="04181-262">Each symbol name requires a symbol kind prefix, such as `M:` prefix for methods, `T:` prefix for types, and `N:` prefix for namespaces.</span></span><br/> <span data-ttu-id="04181-263">- `.ctor` pour les constructeurs et `.cctor` les constructeurs statiques</span><span class="sxs-lookup"><span data-stu-id="04181-263">- `.ctor` for constructors and `.cctor` for static constructors</span></span> | <span data-ttu-id="04181-264">None</span><span class="sxs-lookup"><span data-stu-id="04181-264">None</span></span> | [<span data-ttu-id="04181-265">CA1031</span><span class="sxs-lookup"><span data-stu-id="04181-265">CA1031</span></span>](quality-rules/ca1031.md) |
---
title: Configurer les règles d’analyse du code
description: Découvrez comment configurer des règles d’analyse du code dans un fichier de configuration de l’analyseur.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 4f7b392a2b066023fec75c5295bd94651654d645
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851788"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="d9bb8-103">Options de configuration pour l’analyse du code</span><span class="sxs-lookup"><span data-stu-id="d9bb8-103">Configuration options for code analysis</span></span>

<span data-ttu-id="d9bb8-104">Les règles d’analyse du code ont plusieurs options de configuration.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="d9bb8-105">Ces options sont spécifiées en tant que paires clé-valeur dans un [fichier de configuration d’analyseur](configuration-files.md) à l’aide de la syntaxe `<option key> = <option value>` .</span><span class="sxs-lookup"><span data-stu-id="d9bb8-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="d9bb8-106">L’option la plus courante que vous configurez est la [gravité d’une règle](#severity-level).</span><span class="sxs-lookup"><span data-stu-id="d9bb8-106">The most common option you'll configure is a [rule's severity](#severity-level).</span></span> <span data-ttu-id="d9bb8-107">Vous pouvez configurer le niveau de gravité pour toutes les règles de l’analyseur, y compris les règles de [qualité du code](quality-rules/index.md) et les règles de [style de code](style-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb8-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span> <span data-ttu-id="d9bb8-108">Par exemple, pour activer une règle en tant qu’avertissement, vous pouvez ajouter la paire clé-valeur suivante à un EditorConfig fichier.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-108">For example, to enable a rule as a warning, you can add the following key-value pair to an EditorConfig file.</span></span>

`dotnet_diagnostic.<rule ID>.severity = warning`

<span data-ttu-id="d9bb8-109">Vous pouvez également configurer des options supplémentaires pour personnaliser le comportement de la règle :</span><span class="sxs-lookup"><span data-stu-id="d9bb8-109">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="d9bb8-110">Les règles de qualité du code comportent [des options supplémentaires](code-quality-rule-options.md) pour configurer le comportement, telles que les noms des méthodes auxquelles une règle doit s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-110">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="d9bb8-111">Les règles de style de code ont des [options de style de code personnalisées](code-style-rule-options.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb8-111">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="d9bb8-112">Les règles de l’analyseur tiers peuvent définir leurs propres options de configuration, avec des noms de clé personnalisés et des formats de valeur.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-112">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="d9bb8-113">La syntaxe de configuration de la gravité d’une règle spécifique dans un fichier de configuration de l' [analyseur](configuration-files.md) est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d9bb8-113">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="d9bb8-114">Options générales</span><span class="sxs-lookup"><span data-stu-id="d9bb8-114">General options</span></span>

<span data-ttu-id="d9bb8-115">Ces options s’appliquent à l’analyse du code dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-115">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="d9bb8-116">Ils ne peuvent pas être appliqués uniquement à une seule règle ou à un ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-116">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="d9bb8-117">Exclure le code généré</span><span class="sxs-lookup"><span data-stu-id="d9bb8-117">Exclude generated code</span></span>

<span data-ttu-id="d9bb8-118">Vous pouvez configurer d’autres fichiers et dossiers à traiter comme du code généré en ajoutant une `generated_code = true | false` entrée à votre [fichier de configuration](configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb8-118">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="d9bb8-119">Les avertissements de l’analyseur de code .NET ne sont pas utiles pour les fichiers de code générés, tels que les fichiers générés par le concepteur, que les utilisateurs ne peuvent pas modifier pour corriger les violations.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-119">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="d9bb8-120">Dans la plupart des cas, les analyseurs de code ignorent les fichiers de code générés et ne signalent pas de violations sur ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-120">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="d9bb8-121">Par défaut, les fichiers avec des extensions de fichier ou des en-têtes de fichiers générés automatiquement sont traités comme des fichiers de code générés.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-121">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="d9bb8-122">Par exemple, un nom de fichier se terminant par `.designer.cs` ou `.generated.cs` est considéré comme du code généré.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-122">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="d9bb8-123">Cette option de configuration vous permet de spécifier des modèles de nommage supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-123">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="d9bb8-124">Par exemple, pour traiter tous les fichiers dont le nom se termine par `.MyGenerated.cs` comme code généré, ajoutez l’entrée suivante :</span><span class="sxs-lookup"><span data-stu-id="d9bb8-124">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="d9bb8-125">Options spécifiques à la règle</span><span class="sxs-lookup"><span data-stu-id="d9bb8-125">Rule-specific options</span></span>

<span data-ttu-id="d9bb8-126">Les options spécifiques aux règles peuvent être appliquées à une seule règle, à un ensemble de règles ou à toutes les règles.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-126">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="d9bb8-127">Les options spécifiques à la règle sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d9bb8-127">The rule-specific options include:</span></span>

- [<span data-ttu-id="d9bb8-128">Niveau de gravité de la règle</span><span class="sxs-lookup"><span data-stu-id="d9bb8-128">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="d9bb8-129">Options spécifiques aux règles de *qualité du code*</span><span class="sxs-lookup"><span data-stu-id="d9bb8-129">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="d9bb8-130">Niveau de gravité</span><span class="sxs-lookup"><span data-stu-id="d9bb8-130">Severity level</span></span>

<span data-ttu-id="d9bb8-131">Le tableau suivant présente les différents types de gravité de règle que vous pouvez configurer pour toutes les règles de l’analyseur, y compris la [qualité du code](quality-rules/index.md) et les règles de [style de code](style-rules/index.md) .</span><span class="sxs-lookup"><span data-stu-id="d9bb8-131">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="d9bb8-132">Gravité</span><span class="sxs-lookup"><span data-stu-id="d9bb8-132">Severity</span></span> | <span data-ttu-id="d9bb8-133">Comportement au moment de la génération</span><span class="sxs-lookup"><span data-stu-id="d9bb8-133">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="d9bb8-134">Les violations apparaissent comme des *Erreurs* de build et entraînent l’échec des builds.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-134">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="d9bb8-135">Les violations apparaissent en tant qu' *avertissements* de build, mais ne provoquent pas l’échec des builds (sauf si vous avez une option définie pour traiter les avertissements comme des erreurs).</span><span class="sxs-lookup"><span data-stu-id="d9bb8-135">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="d9bb8-136">Les violations s’affichent sous la forme de *messages* de génération et sous forme de suggestions dans l’IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-136">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="d9bb8-137">Les violations ne sont pas visibles pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-137">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="d9bb8-138">La règle est entièrement supprimée.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-138">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="d9bb8-139">La gravité par défaut de la règle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-139">The default severity of the rule is used.</span></span> |

> [!TIP]
> <span data-ttu-id="d9bb8-140">Pour plus d’informations sur la façon dont les niveaux de gravité de la règle s’affichent dans Visual Studio, consultez [niveaux de gravité](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span><span class="sxs-lookup"><span data-stu-id="d9bb8-140">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="d9bb8-141">Étendue</span><span class="sxs-lookup"><span data-stu-id="d9bb8-141">Scope</span></span>

<span data-ttu-id="d9bb8-142">Pour définir la gravité de la règle pour une seule règle, utilisez la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-142">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="d9bb8-143">Pour définir la gravité de la règle par défaut pour une catégorie de règles d’analyseur, utilisez la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-143">To set the default rule severity for a category of analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="d9bb8-144">Pour définir la gravité de la règle par défaut pour toutes les règles de l’analyseur, utilisez la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-144">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a><span data-ttu-id="d9bb8-145">Priorité</span><span class="sxs-lookup"><span data-stu-id="d9bb8-145">Precedence</span></span>

<span data-ttu-id="d9bb8-146">Si vous avez plusieurs entrées de configuration de gravité qui peuvent être appliquées au même ID de règle, la priorité est choisie dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="d9bb8-146">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="d9bb8-147">Une entrée pour une règle individuelle par ID est prioritaire sur une entrée pour une catégorie.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-147">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="d9bb8-148">Une entrée pour une catégorie est prioritaire sur une entrée pour toutes les règles de l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-148">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="d9bb8-149">Prenons l’exemple suivant, où [CA1822](/visualstudio/code-quality/ca1822) a la catégorie « performance » :</span><span class="sxs-lookup"><span data-stu-id="d9bb8-149">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="d9bb8-150">Dans l’exemple précédent, les trois entrées de gravité sont applicables à CA1822.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-150">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="d9bb8-151">Toutefois, à l’aide des règles de précédence spécifiées, la première entrée basée sur l’ID de règle gagne sur les entrées suivantes.</span><span class="sxs-lookup"><span data-stu-id="d9bb8-151">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="d9bb8-152">Dans cet exemple, CA1822 aura une gravité effective de `error` .</span><span class="sxs-lookup"><span data-stu-id="d9bb8-152">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="d9bb8-153">Toutes les autres règles de la catégorie « performance » auront une gravité de `warning` .</span><span class="sxs-lookup"><span data-stu-id="d9bb8-153">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="d9bb8-154">Pour plus d’informations sur la façon dont la précédence entre fichiers est décidée, consultez la [section priorité de l’article fichiers de configuration](configuration-files.md#precedence).</span><span class="sxs-lookup"><span data-stu-id="d9bb8-154">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>

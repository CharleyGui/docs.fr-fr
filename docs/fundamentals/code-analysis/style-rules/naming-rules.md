---
title: Règles d’attribution de noms de style de code
description: En savoir plus sur les règles de style de code .NET pour nommer les éléments de code.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE1006
- naming rules
helpviewer_keywords:
- IDE1006
- naming code style rules [EditorConfig]
- naming rules
- EditorConfig naming conventions
ms.openlocfilehash: 8ce209e64ee7f9f9028c221daedef8fc6a993ef7
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96588714"
---
# <a name="naming-rules"></a><span data-ttu-id="e2837-103">Règles d’affectation des noms</span><span class="sxs-lookup"><span data-stu-id="e2837-103">Naming rules</span></span>

<span data-ttu-id="e2837-104">Les règles de nommage concernent le nom des éléments de code du langage de programmation .NET, tels que les classes, les propriétés et les méthodes.</span><span class="sxs-lookup"><span data-stu-id="e2837-104">Naming rules concern the naming of .NET programming language code elements, such as classes, properties, and methods.</span></span> <span data-ttu-id="e2837-105">Par exemple, vous pouvez spécifier que les membres publics doivent être en majuscules ou que les champs privés doivent commencer par `_` .</span><span class="sxs-lookup"><span data-stu-id="e2837-105">For example, you can specify that public members must be capitalized or that private fields must begin with `_`.</span></span>

<span data-ttu-id="e2837-106">Une règle de nommage se compose de trois parties :</span><span class="sxs-lookup"><span data-stu-id="e2837-106">A naming rule has three parts:</span></span>

* <span data-ttu-id="e2837-107">Groupe de symboles auquel il s’applique.</span><span class="sxs-lookup"><span data-stu-id="e2837-107">The group of symbols it applies to.</span></span>
* <span data-ttu-id="e2837-108">Style d’affectation de noms à associer à la règle.</span><span class="sxs-lookup"><span data-stu-id="e2837-108">The naming style to associate with the rule.</span></span>
* <span data-ttu-id="e2837-109">Gravité de l’application de la Convention.</span><span class="sxs-lookup"><span data-stu-id="e2837-109">The severity for enforcing the convention.</span></span>

<span data-ttu-id="e2837-110">Vous définissez des règles d’affectation de noms dans un fichier baEditorConfig.</span><span class="sxs-lookup"><span data-stu-id="e2837-110">You define naming rules in an EditorConfig file.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="e2837-111">Syntaxe générale</span><span class="sxs-lookup"><span data-stu-id="e2837-111">General syntax</span></span>

<span data-ttu-id="e2837-112">Pour définir une règle de nommage, un groupe de symboles ou un style de nom, définissez une ou plusieurs propriétés à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="e2837-112">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<prefix>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="e2837-113">Chaque propriété ne doit être définie qu’une seule fois, mais certains paramètres autorisent plusieurs valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="e2837-113">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="e2837-114">L’ordre des propriétés n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="e2837-114">The order of the properties is not important.</span></span>

### \<prefix>

<span data-ttu-id="e2837-115">**\<prefix>** Spécifie le type d’élément défini comme &mdash; règle de nommage, groupe de symboles ou style de nom &mdash; et doit être l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e2837-115">**\<prefix>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="e2837-116">Pour définir une propriété pour</span><span class="sxs-lookup"><span data-stu-id="e2837-116">To set a property for</span></span> | <span data-ttu-id="e2837-117">Utiliser le préfixe</span><span class="sxs-lookup"><span data-stu-id="e2837-117">Use the prefix</span></span> | <span data-ttu-id="e2837-118"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e2837-118">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="e2837-119">Règle de nommage</span><span class="sxs-lookup"><span data-stu-id="e2837-119">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="e2837-120">Groupe de symboles</span><span class="sxs-lookup"><span data-stu-id="e2837-120">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="e2837-121">Style de nommage</span><span class="sxs-lookup"><span data-stu-id="e2837-121">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="e2837-122">Chaque type de &mdash; [règle d’attribution de noms](#naming-rule-properties)de définitions, de groupe de [symboles](#symbol-group-properties)ou de [style de nom](#naming-style-properties) &mdash; possède ses propres propriétés prises en charge, comme décrit dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="e2837-122">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="e2837-123">**\<title>** est un nom descriptif que vous choisissez qui associe plusieurs paramètres de propriété dans une définition unique.</span><span class="sxs-lookup"><span data-stu-id="e2837-123">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="e2837-124">Par exemple, les propriétés suivantes produisent deux définitions de groupe de symboles, `interface` et `types` , chacune d’entre elles ayant deux propriétés définies.</span><span class="sxs-lookup"><span data-stu-id="e2837-124">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="e2837-125">Propriétés de la règle d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="e2837-125">Naming rule properties</span></span>

<span data-ttu-id="e2837-126">Toutes les propriétés de règle de nommage sont requises pour que la règle prenne effet.</span><span class="sxs-lookup"><span data-stu-id="e2837-126">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="e2837-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="e2837-127">Property</span></span> | <span data-ttu-id="e2837-128">Description</span><span class="sxs-lookup"><span data-stu-id="e2837-128">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="e2837-129">Titre du groupe de symboles, définissant les symboles auxquels cette règle doit être appliquée</span><span class="sxs-lookup"><span data-stu-id="e2837-129">The title of the symbol group, defining the symbols to which this rule should be applied</span></span> |
| `style` | <span data-ttu-id="e2837-130">Titre du style d’affectation de noms qui doit être associé à cette règle</span><span class="sxs-lookup"><span data-stu-id="e2837-130">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="e2837-131">Définit la gravité avec laquelle appliquer la règle de nommage.</span><span class="sxs-lookup"><span data-stu-id="e2837-131">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="e2837-132">Définissez la valeur associée sur l’un des [niveaux de gravité](https://docs.microsoft.com/dotnet/fundamentals/code-analysis/configuration-options#severity-level)disponibles. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e2837-132">Set the associated value to one of the available [severity levels](https://docs.microsoft.com/dotnet/fundamentals/code-analysis/configuration-options#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="e2837-133">**Remarques :**</span><span class="sxs-lookup"><span data-stu-id="e2837-133">**Notes:**</span></span>

1. <span data-ttu-id="e2837-134">La spécification de gravité dans une règle de nommage n’est respectée que dans des environnements IDE de développement, tels que Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2837-134">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="e2837-135">Ce paramètre n’est pas compris par les compilateurs C# ou VB, il n’est donc pas respecté pendant la génération.</span><span class="sxs-lookup"><span data-stu-id="e2837-135">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="e2837-136">Au lieu de cela, pour appliquer des règles de style d’affectation de noms à la build, vous devez définir la gravité en utilisant la configuration de gravité basée sur l’ID de règle, comme expliqué dans [cette section](#rule-id-ide1006-naming-rule-violation).</span><span class="sxs-lookup"><span data-stu-id="e2837-136">Instead, to enforce naming style rules on build, you should set the severity by using the rule ID-based severity configuration as explained in [this section](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="e2837-137">Pour plus d’informations, consultez ce [problème GitHub](https://github.com/dotnet/roslyn/issues/44201).</span><span class="sxs-lookup"><span data-stu-id="e2837-137">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="rule-order"></a><span data-ttu-id="e2837-138">Ordre des règles</span><span class="sxs-lookup"><span data-stu-id="e2837-138">Rule order</span></span>

<span data-ttu-id="e2837-139">L’ordre dans lequel les règles d’affectation de noms sont définies dans un fichier EditorConfig n’a pas d’importance.</span><span class="sxs-lookup"><span data-stu-id="e2837-139">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="e2837-140">Les règles d’affectation de noms sont automatiquement triées en fonction de la définition des règles proprement dites.</span><span class="sxs-lookup"><span data-stu-id="e2837-140">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="e2837-141">L' [extension du service de langage EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) peut analyser un fichier EditorConfig et signaler les cas où l’ordonnancement des règles dans le fichier est différent de ce que le compilateur utilisera au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e2837-141">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="e2837-142">Si vous utilisez une version de Visual Studio antérieure à Visual Studio 2019 version 16,2, les règles de nommage doivent être classées de la plus spécifique à la moins spécifique dans le fichier EditorConfig.</span><span class="sxs-lookup"><span data-stu-id="e2837-142">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="e2837-143">La première règle applicable rencontrée est la seule règle appliquée.</span><span class="sxs-lookup"><span data-stu-id="e2837-143">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="e2837-144">Toutefois, s’il existe plusieurs *propriétés* de règle portant le même nom, la propriété la plus récemment trouvée portant ce nom est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="e2837-144">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="e2837-145">Pour plus d’informations, consultez [Priorité et hiérarchie des fichiers](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span><span class="sxs-lookup"><span data-stu-id="e2837-145">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="e2837-146">Propriétés du groupe de symboles</span><span class="sxs-lookup"><span data-stu-id="e2837-146">Symbol group properties</span></span>

<span data-ttu-id="e2837-147">Vous pouvez définir les propriétés suivantes pour les groupes de symboles, afin de limiter les symboles inclus dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="e2837-147">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="e2837-148">Pour spécifier plusieurs valeurs dans un même paramètre de propriété, séparez-les par une virgule.</span><span class="sxs-lookup"><span data-stu-id="e2837-148">To specify multiple values in a single property setting, separate them with a comma.</span></span>

| <span data-ttu-id="e2837-149">Propriété</span><span class="sxs-lookup"><span data-stu-id="e2837-149">Property</span></span> | <span data-ttu-id="e2837-150">Description</span><span class="sxs-lookup"><span data-stu-id="e2837-150">Description</span></span> | <span data-ttu-id="e2837-151">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="e2837-151">Allowed values</span></span> | <span data-ttu-id="e2837-152">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="e2837-152">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="e2837-153">Genres de symboles dans le groupe <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e2837-153">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="e2837-154">`*` (Utilisez cette valeur pour spécifier tous les symboles.)</span><span class="sxs-lookup"><span data-stu-id="e2837-154">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="e2837-155">Oui</span><span class="sxs-lookup"><span data-stu-id="e2837-155">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="e2837-156">Niveaux d’accessibilité des symboles dans le groupe</span><span class="sxs-lookup"><span data-stu-id="e2837-156">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="e2837-157">`*` (Utilisez cette valeur pour spécifier tous les niveaux d’accessibilité.)</span><span class="sxs-lookup"><span data-stu-id="e2837-157">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="e2837-158">`internal` ou `friend`</span><span class="sxs-lookup"><span data-stu-id="e2837-158">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="e2837-159">`protected_internal` ou `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="e2837-159">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="e2837-160">`local` (pour les symboles définis dans une méthode)</span><span class="sxs-lookup"><span data-stu-id="e2837-160">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="e2837-161">Oui</span><span class="sxs-lookup"><span data-stu-id="e2837-161">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="e2837-162">Faire correspondre uniquement les symboles avec _tous_ les modificateurs spécifiés <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="e2837-162">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="e2837-163">`abstract` ou `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="e2837-163">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="e2837-164">`static` ou `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e2837-164">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="e2837-165">Non</span><span class="sxs-lookup"><span data-stu-id="e2837-165">No</span></span> |

<span data-ttu-id="e2837-166">**Remarques :**</span><span class="sxs-lookup"><span data-stu-id="e2837-166">**Notes:**</span></span>

1. <span data-ttu-id="e2837-167">Les membres de tuple ne sont actuellement pas pris en charge dans `applicable_kinds` .</span><span class="sxs-lookup"><span data-stu-id="e2837-167">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="e2837-168">Le groupe de symboles correspond à _tous_ les modificateurs de la `required_modifiers` propriété.</span><span class="sxs-lookup"><span data-stu-id="e2837-168">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="e2837-169">Si vous omettez cette propriété, aucun modificateur spécifique n’est requis pour une correspondance.</span><span class="sxs-lookup"><span data-stu-id="e2837-169">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="e2837-170">Cela signifie que les modificateurs d’un symbole n’ont aucun effet sur l’application ou non de cette règle.</span><span class="sxs-lookup"><span data-stu-id="e2837-170">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="e2837-171">Si votre groupe possède `static` ou `shared` dans la `required_modifiers` propriété, le groupe inclut également des `const` symboles, car ils sont implicitement `static` / `Shared` .</span><span class="sxs-lookup"><span data-stu-id="e2837-171">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="e2837-172">Toutefois, si vous ne souhaitez pas que la `static` règle d’affectation de noms s’applique aux `const` symboles, vous pouvez créer une nouvelle règle de nommage avec un groupe de symboles `const` .</span><span class="sxs-lookup"><span data-stu-id="e2837-172">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="e2837-173">Propriétés de style de nom</span><span class="sxs-lookup"><span data-stu-id="e2837-173">Naming style properties</span></span>

<span data-ttu-id="e2837-174">Un style d’affectation de noms définit les conventions que vous souhaitez appliquer à la règle.</span><span class="sxs-lookup"><span data-stu-id="e2837-174">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="e2837-175">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e2837-175">For example:</span></span>

* <span data-ttu-id="e2837-176">Mettre en majuscules `PascalCase`</span><span class="sxs-lookup"><span data-stu-id="e2837-176">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="e2837-177">Commence par `m_`</span><span class="sxs-lookup"><span data-stu-id="e2837-177">Starts with `m_`</span></span>
* <span data-ttu-id="e2837-178">Se termine par `_g`</span><span class="sxs-lookup"><span data-stu-id="e2837-178">Ends with `_g`</span></span>
* <span data-ttu-id="e2837-179">Séparer les mots avec `__`</span><span class="sxs-lookup"><span data-stu-id="e2837-179">Separate words with `__`</span></span>

<span data-ttu-id="e2837-180">Vous pouvez définir les propriétés suivantes pour un style d’affectation de noms :</span><span class="sxs-lookup"><span data-stu-id="e2837-180">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="e2837-181">Propriété</span><span class="sxs-lookup"><span data-stu-id="e2837-181">Property</span></span> | <span data-ttu-id="e2837-182">Description</span><span class="sxs-lookup"><span data-stu-id="e2837-182">Description</span></span> | <span data-ttu-id="e2837-183">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="e2837-183">Allowed values</span></span> | <span data-ttu-id="e2837-184">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="e2837-184">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="e2837-185">Style de mise en majuscules pour les mots dans le symbole</span><span class="sxs-lookup"><span data-stu-id="e2837-185">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="e2837-186">Oui<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e2837-186">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="e2837-187">Doit commencer par ces caractères</span><span class="sxs-lookup"><span data-stu-id="e2837-187">Must begin with these characters</span></span> | | <span data-ttu-id="e2837-188">Non</span><span class="sxs-lookup"><span data-stu-id="e2837-188">No</span></span> |
| `required_suffix` | <span data-ttu-id="e2837-189">Doit se terminer par ces caractères</span><span class="sxs-lookup"><span data-stu-id="e2837-189">Must end with these characters</span></span> | | <span data-ttu-id="e2837-190">Non</span><span class="sxs-lookup"><span data-stu-id="e2837-190">No</span></span> |
| `word_separator` | <span data-ttu-id="e2837-191">Les mots contenus dans le symbole doivent être séparés par ce caractère</span><span class="sxs-lookup"><span data-stu-id="e2837-191">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="e2837-192">Non</span><span class="sxs-lookup"><span data-stu-id="e2837-192">No</span></span> |

<span data-ttu-id="e2837-193">**Remarques :**</span><span class="sxs-lookup"><span data-stu-id="e2837-193">**Notes:**</span></span>

1. <span data-ttu-id="e2837-194">Vous devez spécifier un style de mise en majuscules dans le cadre de votre style de nommage, sans quoi votre style de nommage risque d’être ignoré.</span><span class="sxs-lookup"><span data-stu-id="e2837-194">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="e2837-195">Styles de dénomination par défaut</span><span class="sxs-lookup"><span data-stu-id="e2837-195">Default naming styles</span></span>

<span data-ttu-id="e2837-196">Si vous ne spécifiez aucune règle de nommage personnalisée, les styles par défaut suivants sont utilisés :</span><span class="sxs-lookup"><span data-stu-id="e2837-196">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="e2837-197">Pour les classes, structures, énumérations, propriétés et événements avec l’accessibilité `public`, `private`, `internal`, `protected` ou `protected_internal`, le style de dénomination par défaut est la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="e2837-197">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="e2837-198">Pour les interfaces avec l’accessibilité `public`, `private`, `internal`, `protected` ou `protected_internal`, le style de dénomination par défaut est la casse Pascal avec le préfixe **I** requis.</span><span class="sxs-lookup"><span data-stu-id="e2837-198">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="example"></a><span data-ttu-id="e2837-199"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e2837-199">Example</span></span>

<span data-ttu-id="e2837-200">Le fichier *.editorconfig* suivant contient une convention de nommage qui spécifie que les propriétés publiques, les méthodes, les champs, les événements et les délégués doivent être mis en majuscules.</span><span class="sxs-lookup"><span data-stu-id="e2837-200">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="e2837-201">Notez que cette convention de nommage spécifie plusieurs types de symboles auxquels appliquer la règle, en utilisant une virgule pour séparer les valeurs.</span><span class="sxs-lookup"><span data-stu-id="e2837-201">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

```ini
[*.{cs,vb}]

# Defining the 'public_symbols' symbol group
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

# Defining the `first_word_upper_case_style` naming style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

# Defining the `public_members_must_be_capitalized` naming rule, by setting the symbol group to the 'public symbols' symbol group,
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
# setting the naming style to the `first_word_upper_case_style` naming style,
dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
# and setting the severity.
dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

## <a name="rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="e2837-202">ID de règle : « IDE1006 » (violation de règle de nommage)</span><span class="sxs-lookup"><span data-stu-id="e2837-202">Rule ID: "IDE1006" (Naming rule violation)</span></span>

<span data-ttu-id="e2837-203">Toutes les options d’attribution de noms ont un ID `IDE1006` et un titre de règle `Naming rule violation` .</span><span class="sxs-lookup"><span data-stu-id="e2837-203">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="e2837-204">Vous pouvez configurer le niveau de gravité des violations de nom globalement dans un fichier EditorConfig avec la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="e2837-204">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="e2837-205">La valeur de gravité doit être ou doit être `warning` `error` [appliquée lors de la génération](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="e2837-205">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="e2837-206">Pour toutes les valeurs de gravité possibles, consultez [niveau de gravité](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="e2837-206">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2837-207">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2837-207">See also</span></span>

- [<span data-ttu-id="e2837-208">Règles de langage</span><span class="sxs-lookup"><span data-stu-id="e2837-208">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="e2837-209">Règles de mise en forme</span><span class="sxs-lookup"><span data-stu-id="e2837-209">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="e2837-210">Règles d’affectation de noms Roslyn</span><span class="sxs-lookup"><span data-stu-id="e2837-210">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [<span data-ttu-id="e2837-211">Référence des règles de style de code .NET</span><span class="sxs-lookup"><span data-stu-id="e2837-211">.NET code style rules reference</span></span>](index.md)

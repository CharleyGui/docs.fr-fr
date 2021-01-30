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
ms.openlocfilehash: 1fce275204b729b4d23729ca432e06a5a249620d
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065133"
---
# <a name="naming-rules"></a><span data-ttu-id="898b4-103">Règles d’affectation des noms</span><span class="sxs-lookup"><span data-stu-id="898b4-103">Naming rules</span></span>

<span data-ttu-id="898b4-104">Dans votre `.editorconfig` fichier, vous pouvez définir des **règles d’affectation de noms** pour la façon dont les éléments de code du langage de programmation .NET &mdash; tels que les classes, les propriétés et les méthodes &mdash; doivent être nommés.</span><span class="sxs-lookup"><span data-stu-id="898b4-104">In your `.editorconfig` file, you can define **naming rules** for how .NET programming language code elements&mdash;such as classes, properties, and methods&mdash;should be named.</span></span> <span data-ttu-id="898b4-105">Par exemple, vous pouvez spécifier que les membres publics doivent être en majuscules ou que les champs privés doivent commencer par `_` .</span><span class="sxs-lookup"><span data-stu-id="898b4-105">For example, you can specify that public members must be capitalized, or that private fields must begin with `_`.</span></span>

<span data-ttu-id="898b4-106">Une règle de nommage comporte trois composants :</span><span class="sxs-lookup"><span data-stu-id="898b4-106">A naming rule has three components:</span></span>

* <span data-ttu-id="898b4-107">**Groupe** &mdash; de symboles auquel la règle s’applique.</span><span class="sxs-lookup"><span data-stu-id="898b4-107">The **symbol group**&mdash;the group of symbols the rule applies to.</span></span>
* <span data-ttu-id="898b4-108">**Style d’affectation de noms** à associer à la règle.</span><span class="sxs-lookup"><span data-stu-id="898b4-108">The **naming style** to associate with the rule.</span></span>
* <span data-ttu-id="898b4-109">Gravité de l’application de la Convention.</span><span class="sxs-lookup"><span data-stu-id="898b4-109">The severity for enforcing the convention.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="898b4-110">Syntaxe générale</span><span class="sxs-lookup"><span data-stu-id="898b4-110">General syntax</span></span>

<span data-ttu-id="898b4-111">Pour définir une règle de nommage, un groupe de symboles ou un style de nom, définissez une ou plusieurs propriétés à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="898b4-111">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="898b4-112">Chaque propriété ne doit être définie qu’une seule fois, mais certains paramètres autorisent plusieurs valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="898b4-112">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="898b4-113">L’ordre des propriétés n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="898b4-113">The order of the properties is not important.</span></span>

### \<kind>

<span data-ttu-id="898b4-114">**\<kind>** Spécifie le type d’élément défini comme &mdash; règle de nommage, groupe de symboles ou style de nom &mdash; et doit être l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="898b4-114">**\<kind>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="898b4-115">Pour définir une propriété pour</span><span class="sxs-lookup"><span data-stu-id="898b4-115">To set a property for</span></span> | <span data-ttu-id="898b4-116">Utilisez la \<kind> valeur</span><span class="sxs-lookup"><span data-stu-id="898b4-116">Use the \<kind> value</span></span> | <span data-ttu-id="898b4-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="898b4-117">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="898b4-118">Règle de nommage</span><span class="sxs-lookup"><span data-stu-id="898b4-118">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="898b4-119">Groupe de symboles</span><span class="sxs-lookup"><span data-stu-id="898b4-119">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="898b4-120">Style de nommage</span><span class="sxs-lookup"><span data-stu-id="898b4-120">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="898b4-121">Chaque type de &mdash; [règle d’attribution de noms](#naming-rule-properties)de définitions, de groupe de [symboles](#symbol-group-properties)ou de [style de nom](#naming-style-properties) &mdash; possède ses propres propriétés prises en charge, comme décrit dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="898b4-121">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="898b4-122">**\<title>** est un nom descriptif que vous choisissez qui associe plusieurs paramètres de propriété dans une définition unique.</span><span class="sxs-lookup"><span data-stu-id="898b4-122">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="898b4-123">Par exemple, les propriétés suivantes produisent deux définitions de groupe de symboles, `interface` et `types` , chacune d’entre elles ayant deux propriétés définies.</span><span class="sxs-lookup"><span data-stu-id="898b4-123">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="898b4-124">Propriétés de la règle d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="898b4-124">Naming rule properties</span></span>

<span data-ttu-id="898b4-125">Toutes les propriétés de règle de nommage sont requises pour que la règle prenne effet.</span><span class="sxs-lookup"><span data-stu-id="898b4-125">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="898b4-126">Propriété</span><span class="sxs-lookup"><span data-stu-id="898b4-126">Property</span></span> | <span data-ttu-id="898b4-127">Description</span><span class="sxs-lookup"><span data-stu-id="898b4-127">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="898b4-128">Titre d’un groupe de symboles ; la règle d’affectation de noms sera appliquée aux symboles de ce groupe</span><span class="sxs-lookup"><span data-stu-id="898b4-128">The title of a symbol group; the naming rule will be applied to the symbols in this group</span></span> |
| `style` | <span data-ttu-id="898b4-129">Titre du style d’affectation de noms qui doit être associé à cette règle</span><span class="sxs-lookup"><span data-stu-id="898b4-129">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="898b4-130">Définit la gravité avec laquelle appliquer la règle de nommage.</span><span class="sxs-lookup"><span data-stu-id="898b4-130">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="898b4-131">Définissez la valeur associée sur l’un des [niveaux de gravité](../configuration-options.md#severity-level)disponibles. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="898b4-131">Set the associated value to one of the available [severity levels](../configuration-options.md#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="898b4-132">**Remarques :**</span><span class="sxs-lookup"><span data-stu-id="898b4-132">**Notes:**</span></span>

1. <span data-ttu-id="898b4-133">La spécification de gravité dans une règle de nommage n’est respectée que dans des environnements IDE de développement, tels que Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="898b4-133">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="898b4-134">Ce paramètre n’est pas compris par les compilateurs C# ou VB, il n’est donc pas respecté pendant la génération.</span><span class="sxs-lookup"><span data-stu-id="898b4-134">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="898b4-135">Pour appliquer des règles de style d’affectation de noms à la build, vous devez définir la gravité à l’aide de la configuration de gravité de la [règle de code](#rule-id-ide1006-naming-rule-violation).</span><span class="sxs-lookup"><span data-stu-id="898b4-135">To enforce naming style rules on build, you should instead set the severity by using [code rule severity configuration](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="898b4-136">Pour plus d’informations, consultez ce [problème GitHub](https://github.com/dotnet/roslyn/issues/44201).</span><span class="sxs-lookup"><span data-stu-id="898b4-136">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="898b4-137">Propriétés du groupe de symboles</span><span class="sxs-lookup"><span data-stu-id="898b4-137">Symbol group properties</span></span>

<span data-ttu-id="898b4-138">Vous pouvez définir les propriétés suivantes pour les groupes de symboles, afin de limiter les symboles inclus dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="898b4-138">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="898b4-139">Pour spécifier plusieurs valeurs pour une seule propriété, séparez les valeurs par une virgule.</span><span class="sxs-lookup"><span data-stu-id="898b4-139">To specify multiple values for a single property, separate the values with a comma.</span></span>

| <span data-ttu-id="898b4-140">Propriété</span><span class="sxs-lookup"><span data-stu-id="898b4-140">Property</span></span> | <span data-ttu-id="898b4-141">Description</span><span class="sxs-lookup"><span data-stu-id="898b4-141">Description</span></span> | <span data-ttu-id="898b4-142">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="898b4-142">Allowed values</span></span> | <span data-ttu-id="898b4-143">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="898b4-143">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="898b4-144">Genres de symboles dans le groupe <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="898b4-144">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="898b4-145">`*` (Utilisez cette valeur pour spécifier tous les symboles.)</span><span class="sxs-lookup"><span data-stu-id="898b4-145">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="898b4-146">Oui</span><span class="sxs-lookup"><span data-stu-id="898b4-146">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="898b4-147">Niveaux d’accessibilité des symboles dans le groupe</span><span class="sxs-lookup"><span data-stu-id="898b4-147">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="898b4-148">`*` (Utilisez cette valeur pour spécifier tous les niveaux d’accessibilité.)</span><span class="sxs-lookup"><span data-stu-id="898b4-148">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="898b4-149">`internal` ou `friend`</span><span class="sxs-lookup"><span data-stu-id="898b4-149">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="898b4-150">`protected_internal` ou `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="898b4-150">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="898b4-151">`local` (pour les symboles définis dans une méthode)</span><span class="sxs-lookup"><span data-stu-id="898b4-151">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="898b4-152">Oui</span><span class="sxs-lookup"><span data-stu-id="898b4-152">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="898b4-153">Faire correspondre uniquement les symboles avec _tous_ les modificateurs spécifiés <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="898b4-153">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="898b4-154">`abstract` ou `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="898b4-154">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="898b4-155">`static` ou `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="898b4-155">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="898b4-156">Non</span><span class="sxs-lookup"><span data-stu-id="898b4-156">No</span></span> |

<span data-ttu-id="898b4-157">**Remarques :**</span><span class="sxs-lookup"><span data-stu-id="898b4-157">**Notes:**</span></span>

1. <span data-ttu-id="898b4-158">Les membres de tuple ne sont actuellement pas pris en charge dans `applicable_kinds` .</span><span class="sxs-lookup"><span data-stu-id="898b4-158">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="898b4-159">Le groupe de symboles correspond à _tous_ les modificateurs de la `required_modifiers` propriété.</span><span class="sxs-lookup"><span data-stu-id="898b4-159">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="898b4-160">Si vous omettez cette propriété, aucun modificateur spécifique n’est requis pour une correspondance.</span><span class="sxs-lookup"><span data-stu-id="898b4-160">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="898b4-161">Cela signifie que les modificateurs d’un symbole n’ont aucun effet sur l’application ou non de cette règle.</span><span class="sxs-lookup"><span data-stu-id="898b4-161">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="898b4-162">Si votre groupe possède `static` ou `shared` dans la `required_modifiers` propriété, le groupe inclut également des `const` symboles, car ils sont implicitement `static` / `Shared` .</span><span class="sxs-lookup"><span data-stu-id="898b4-162">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="898b4-163">Toutefois, si vous ne souhaitez pas que la `static` règle d’affectation de noms s’applique aux `const` symboles, vous pouvez créer une nouvelle règle de nommage avec un groupe de symboles `const` .</span><span class="sxs-lookup"><span data-stu-id="898b4-163">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="898b4-164">Propriétés de style de nom</span><span class="sxs-lookup"><span data-stu-id="898b4-164">Naming style properties</span></span>

<span data-ttu-id="898b4-165">Un style d’affectation de noms définit les conventions que vous souhaitez appliquer à la règle.</span><span class="sxs-lookup"><span data-stu-id="898b4-165">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="898b4-166">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="898b4-166">For example:</span></span>

* <span data-ttu-id="898b4-167">Mettre en majuscules `PascalCase`</span><span class="sxs-lookup"><span data-stu-id="898b4-167">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="898b4-168">Commence par `m_`</span><span class="sxs-lookup"><span data-stu-id="898b4-168">Starts with `m_`</span></span>
* <span data-ttu-id="898b4-169">Se termine par `_g`</span><span class="sxs-lookup"><span data-stu-id="898b4-169">Ends with `_g`</span></span>
* <span data-ttu-id="898b4-170">Séparer les mots avec `__`</span><span class="sxs-lookup"><span data-stu-id="898b4-170">Separate words with `__`</span></span>

<span data-ttu-id="898b4-171">Vous pouvez définir les propriétés suivantes pour un style d’affectation de noms :</span><span class="sxs-lookup"><span data-stu-id="898b4-171">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="898b4-172">Propriété</span><span class="sxs-lookup"><span data-stu-id="898b4-172">Property</span></span> | <span data-ttu-id="898b4-173">Description</span><span class="sxs-lookup"><span data-stu-id="898b4-173">Description</span></span> | <span data-ttu-id="898b4-174">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="898b4-174">Allowed values</span></span> | <span data-ttu-id="898b4-175">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="898b4-175">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="898b4-176">Style de mise en majuscules pour les mots dans le symbole</span><span class="sxs-lookup"><span data-stu-id="898b4-176">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="898b4-177">Oui<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="898b4-177">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="898b4-178">Doit commencer par ces caractères</span><span class="sxs-lookup"><span data-stu-id="898b4-178">Must begin with these characters</span></span> | | <span data-ttu-id="898b4-179">Non</span><span class="sxs-lookup"><span data-stu-id="898b4-179">No</span></span> |
| `required_suffix` | <span data-ttu-id="898b4-180">Doit se terminer par ces caractères</span><span class="sxs-lookup"><span data-stu-id="898b4-180">Must end with these characters</span></span> | | <span data-ttu-id="898b4-181">Non</span><span class="sxs-lookup"><span data-stu-id="898b4-181">No</span></span> |
| `word_separator` | <span data-ttu-id="898b4-182">Les mots contenus dans le symbole doivent être séparés par ce caractère</span><span class="sxs-lookup"><span data-stu-id="898b4-182">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="898b4-183">Non</span><span class="sxs-lookup"><span data-stu-id="898b4-183">No</span></span> |

<span data-ttu-id="898b4-184">**Remarques :**</span><span class="sxs-lookup"><span data-stu-id="898b4-184">**Notes:**</span></span>

1. <span data-ttu-id="898b4-185">Vous devez spécifier un style de mise en majuscules dans le cadre de votre style de nommage, sans quoi votre style de nommage risque d’être ignoré.</span><span class="sxs-lookup"><span data-stu-id="898b4-185">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="rule-order"></a><span data-ttu-id="898b4-186">Ordre des règles</span><span class="sxs-lookup"><span data-stu-id="898b4-186">Rule order</span></span>

<span data-ttu-id="898b4-187">L’ordre dans lequel les règles d’affectation de noms sont définies dans un fichier EditorConfig n’a pas d’importance.</span><span class="sxs-lookup"><span data-stu-id="898b4-187">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="898b4-188">Les règles d’affectation de noms sont automatiquement triées en fonction de la définition des règles proprement dites.</span><span class="sxs-lookup"><span data-stu-id="898b4-188">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="898b4-189">L' [extension du service de langage EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) peut analyser un fichier EditorConfig et signaler les cas où l’ordonnancement des règles dans le fichier est différent de ce que le compilateur utilisera au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="898b4-189">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="898b4-190">Si vous utilisez une version de Visual Studio antérieure à Visual Studio 2019 version 16,2, les règles de nommage doivent être classées de la plus spécifique à la moins spécifique dans le fichier EditorConfig.</span><span class="sxs-lookup"><span data-stu-id="898b4-190">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="898b4-191">La première règle applicable rencontrée est la seule règle appliquée.</span><span class="sxs-lookup"><span data-stu-id="898b4-191">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="898b4-192">Toutefois, s’il existe plusieurs *propriétés* de règle portant le même nom, la propriété la plus récemment trouvée portant ce nom est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="898b4-192">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="898b4-193">Pour plus d’informations, consultez [Priorité et hiérarchie des fichiers](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span><span class="sxs-lookup"><span data-stu-id="898b4-193">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="898b4-194">Styles de dénomination par défaut</span><span class="sxs-lookup"><span data-stu-id="898b4-194">Default naming styles</span></span>

<span data-ttu-id="898b4-195">Si vous ne spécifiez aucune règle de nommage personnalisée, les styles par défaut suivants sont utilisés :</span><span class="sxs-lookup"><span data-stu-id="898b4-195">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="898b4-196">Pour les classes, structures, énumérations, propriétés et événements avec l’accessibilité `public`, `private`, `internal`, `protected` ou `protected_internal`, le style de dénomination par défaut est la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="898b4-196">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="898b4-197">Pour les interfaces avec l’accessibilité `public`, `private`, `internal`, `protected` ou `protected_internal`, le style de dénomination par défaut est la casse Pascal avec le préfixe **I** requis.</span><span class="sxs-lookup"><span data-stu-id="898b4-197">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="898b4-198">ID de règle de code : `IDE1006 (Naming rule violation)`</span><span class="sxs-lookup"><span data-stu-id="898b4-198">Code Rule ID: `IDE1006 (Naming rule violation)`</span></span>

<span data-ttu-id="898b4-199">Toutes les options d’attribution de noms ont un ID `IDE1006` et un titre de règle `Naming rule violation` .</span><span class="sxs-lookup"><span data-stu-id="898b4-199">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="898b4-200">Vous pouvez configurer le niveau de gravité des violations de nom globalement dans un fichier EditorConfig avec la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="898b4-200">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="898b4-201">La valeur de gravité doit être ou doit être `warning` `error` [appliquée lors de la génération](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="898b4-201">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="898b4-202">Pour toutes les valeurs de gravité possibles, consultez [niveau de gravité](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="898b4-202">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="example"></a><span data-ttu-id="898b4-203">Exemple</span><span class="sxs-lookup"><span data-stu-id="898b4-203">Example</span></span>

<span data-ttu-id="898b4-204">Le fichier *.editorconfig* suivant contient une convention de nommage qui spécifie que les propriétés publiques, les méthodes, les champs, les événements et les délégués doivent être mis en majuscules.</span><span class="sxs-lookup"><span data-stu-id="898b4-204">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="898b4-205">Notez que cette convention de nommage spécifie plusieurs types de symboles auxquels appliquer la règle, en utilisant une virgule pour séparer les valeurs.</span><span class="sxs-lookup"><span data-stu-id="898b4-205">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="898b4-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="898b4-206">See also</span></span>

- [<span data-ttu-id="898b4-207">Règles de langage</span><span class="sxs-lookup"><span data-stu-id="898b4-207">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="898b4-208">Règles de mise en forme</span><span class="sxs-lookup"><span data-stu-id="898b4-208">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="898b4-209">Règles d’affectation de noms Roslyn</span><span class="sxs-lookup"><span data-stu-id="898b4-209">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [<span data-ttu-id="898b4-210">Référence des règles de style de code .NET</span><span class="sxs-lookup"><span data-stu-id="898b4-210">.NET code style rules reference</span></span>](index.md)

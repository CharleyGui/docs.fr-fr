---
title: Nouveautés de C# 7.1
description: Vue d’ensemble des nouvelles fonctionnalités de C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: 5d2d6f51b6422f5b4db5c6bd275b5ffce1f695f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399706"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="c5778-103">Nouveautés de C# 7.1</span><span class="sxs-lookup"><span data-stu-id="c5778-103">What's new in C# 7.1</span></span>

<span data-ttu-id="c5778-104">C# 7.1 est la première version mineure pour le langage C#.</span><span class="sxs-lookup"><span data-stu-id="c5778-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="c5778-105">Elle marque une cadence de publication accrue pour le langage.</span><span class="sxs-lookup"><span data-stu-id="c5778-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="c5778-106">Vous pouvez utiliser les nouvelles fonctionnalités plus tôt, dans l’idéal quand chaque nouvelle fonctionnalité est prête.</span><span class="sxs-lookup"><span data-stu-id="c5778-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="c5778-107">C# 7.1 ajoute la possibilité de configurer le compilateur pour le faire correspondre à une version spécifiée du langage.</span><span class="sxs-lookup"><span data-stu-id="c5778-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="c5778-108">Ceci vous permet de séparer la décision de mettre à niveau les outils de la décision de mettre à niveau les versions du langage.</span><span class="sxs-lookup"><span data-stu-id="c5778-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="c5778-109">C# 7.1 ajoute l’élément de configuration de [sélection de la version du langage](../language-reference/configure-language-version.md), trois nouvelles fonctionnalités du langage et un nouveau comportement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="c5778-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="c5778-110">Les nouvelles fonctionnalités de langage de cette version sont :</span><span class="sxs-lookup"><span data-stu-id="c5778-110">The new language features in this release are:</span></span>

- [<span data-ttu-id="c5778-111">`async``Main` méthode</span><span class="sxs-lookup"><span data-stu-id="c5778-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="c5778-112">Le point d’entrée pour une application peut avoir le modificateur `async`.</span><span class="sxs-lookup"><span data-stu-id="c5778-112">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="c5778-113">`default`expressions littérales</span><span class="sxs-lookup"><span data-stu-id="c5778-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="c5778-114">Vous pouvez utiliser des expressions littérales default dans les expressions de valeur par défaut quand le type cible peut être inféré.</span><span class="sxs-lookup"><span data-stu-id="c5778-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="c5778-115">Noms des éléments de tuple inférés</span><span class="sxs-lookup"><span data-stu-id="c5778-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="c5778-116">Les noms des éléments de tuple peuvent être inférés dans de nombreux cas à partir de l’initialisation du tuple.</span><span class="sxs-lookup"><span data-stu-id="c5778-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
- [<span data-ttu-id="c5778-117">Critères spéciaux sur les paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="c5778-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="c5778-118">Il est possible d’utiliser des expressions de critères spéciaux sur les variables dont le type est un paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="c5778-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="c5778-119">Enfin, le compilateur a deux options, `-refout` et `-refonly`, qui contrôlent la [génération d’assemblys de références](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="c5778-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="c5778-120">Pour utiliser les fonctionnalités les plus récentes dans une version mineure, vous devez [configurer la version du langage du compilateur](../language-reference/configure-language-version.md) et sélectionner la version.</span><span class="sxs-lookup"><span data-stu-id="c5778-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="c5778-121">Le reste de cet article présente une vue d’ensemble de chaque fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="c5778-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="c5778-122">Vous découvrirez la logique de chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="c5778-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="c5778-123">Vous allez apprendre leur syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c5778-123">You'll learn the syntax.</span></span> <span data-ttu-id="c5778-124">Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :</span><span class="sxs-lookup"><span data-stu-id="c5778-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="c5778-125">Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).</span><span class="sxs-lookup"><span data-stu-id="c5778-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="c5778-126">Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="c5778-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="c5778-127">Définissez le répertoire actuel sur le sous-répertoire *csharp7* pour le référentiel *try-samples*.</span><span class="sxs-lookup"><span data-stu-id="c5778-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="c5778-128">Exécutez `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="c5778-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="c5778-129">Async main</span><span class="sxs-lookup"><span data-stu-id="c5778-129">Async main</span></span>

<span data-ttu-id="c5778-130">Une méthode *async main* vous permet d’utiliser `await` dans votre méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="c5778-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="c5778-131">Auparavant, vous deviez écrire :</span><span class="sxs-lookup"><span data-stu-id="c5778-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="c5778-132">Vous pouvez désormais écrire :</span><span class="sxs-lookup"><span data-stu-id="c5778-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="c5778-133">Si votre programme ne retourne pas de code de sortie, vous pouvez déclarer une méthode `Main` qui retourne une <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="c5778-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="c5778-134">Pour plus d’informations, voir l’article [async main](../programming-guide/main-and-command-args/index.md) du guide de programmation.</span><span class="sxs-lookup"><span data-stu-id="c5778-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="c5778-135">Expressions littérales par défaut</span><span class="sxs-lookup"><span data-stu-id="c5778-135">Default literal expressions</span></span>

<span data-ttu-id="c5778-136">Les expressions littérales par défaut sont une amélioration des expressions de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c5778-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="c5778-137">Ces expressions initialisent une variable à la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c5778-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="c5778-138">Vous deviez écrire auparavant :</span><span class="sxs-lookup"><span data-stu-id="c5778-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="c5778-139">Vous pouvez désormais omettre le type du côté droit de l’initialisation :</span><span class="sxs-lookup"><span data-stu-id="c5778-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="c5778-140">Pour plus d’informations, voir la section [littéral par défaut](../language-reference/operators/default.md#default-literal) de l’article [opérateur par défaut](../language-reference/operators/default.md).</span><span class="sxs-lookup"><span data-stu-id="c5778-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="c5778-141">Noms des éléments de tuple inférés</span><span class="sxs-lookup"><span data-stu-id="c5778-141">Inferred tuple element names</span></span>

<span data-ttu-id="c5778-142">Cette fonctionnalité est une petite amélioration de la fonctionnalité des tuples introduite dans C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="c5778-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="c5778-143">Très souvent, quand vous initialisez un tuple, les variables utilisées pour le côté droit de l’affectation sont identiques aux noms que vous souhaitez pour les éléments du tuple :</span><span class="sxs-lookup"><span data-stu-id="c5778-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="c5778-144">Dans C# 7.1, les noms des éléments du tuple peuvent être inférés à partir des variables utilisées pour initialiser le tuple :</span><span class="sxs-lookup"><span data-stu-id="c5778-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="c5778-145">Pour plus d’informations sur cette fonctionnalité, voir l’article [Tuples](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="c5778-145">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="c5778-146">Critères spéciaux sur les paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="c5778-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="c5778-147">À compter de C# 7.1, l’expression de modèle de `is` et du modèle de type `switch` peut avoir le type d’un paramètre de type générique,</span><span class="sxs-lookup"><span data-stu-id="c5778-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="c5778-148">ce qui peut se révéler particulièrement utile pour vérifier des types potentiellement `struct` ou `class` tout en évitant le boxing.</span><span class="sxs-lookup"><span data-stu-id="c5778-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="c5778-149">Génération d’assemblys de références</span><span class="sxs-lookup"><span data-stu-id="c5778-149">Reference assembly generation</span></span>

<span data-ttu-id="c5778-150">Il existe deux nouvelles options de compilateur qui génèrent *des assemblages de référence seulement*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) et [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c5778-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="c5778-151">Les articles en lien décrivent plus en détail ces options et les assemblys de références.</span><span class="sxs-lookup"><span data-stu-id="c5778-151">The linked articles explain these options and reference assemblies in more detail.</span></span>

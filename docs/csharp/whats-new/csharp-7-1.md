---
title: Nouveautés de C# 7.1
description: Vue d’ensemble des nouvelles fonctionnalités de C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: 4b7bd96e428f990b2db91a4cfd45da01dc133aac
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881545"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="3bed2-103">Nouveautés de C# 7.1</span><span class="sxs-lookup"><span data-stu-id="3bed2-103">What's new in C# 7.1</span></span>

<span data-ttu-id="3bed2-104">C# 7.1 est la première version mineure pour le langage C#.</span><span class="sxs-lookup"><span data-stu-id="3bed2-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="3bed2-105">Elle marque une cadence de publication accrue pour le langage.</span><span class="sxs-lookup"><span data-stu-id="3bed2-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="3bed2-106">Vous pouvez utiliser les nouvelles fonctionnalités plus tôt, dans l’idéal quand chaque nouvelle fonctionnalité est prête.</span><span class="sxs-lookup"><span data-stu-id="3bed2-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="3bed2-107">C# 7.1 ajoute la possibilité de configurer le compilateur pour le faire correspondre à une version spécifiée du langage.</span><span class="sxs-lookup"><span data-stu-id="3bed2-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="3bed2-108">Ceci vous permet de séparer la décision de mettre à niveau les outils de la décision de mettre à niveau les versions du langage.</span><span class="sxs-lookup"><span data-stu-id="3bed2-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="3bed2-109">C# 7.1 ajoute l’élément de configuration de [sélection de la version du langage](../language-reference/configure-language-version.md), trois nouvelles fonctionnalités du langage et un nouveau comportement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="3bed2-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="3bed2-110">Les nouvelles fonctionnalités de langage de cette version sont :</span><span class="sxs-lookup"><span data-stu-id="3bed2-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="3bed2-111">Méthode `async` `Main`</span><span class="sxs-lookup"><span data-stu-id="3bed2-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="3bed2-112">Le point d’entrée pour une application peut avoir le modificateur `async`.</span><span class="sxs-lookup"><span data-stu-id="3bed2-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="3bed2-113">Expressions littérales `default`</span><span class="sxs-lookup"><span data-stu-id="3bed2-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="3bed2-114">Vous pouvez utiliser des expressions littérales default dans les expressions de valeur par défaut quand le type cible peut être inféré.</span><span class="sxs-lookup"><span data-stu-id="3bed2-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="3bed2-115">Noms des éléments de tuple inférés</span><span class="sxs-lookup"><span data-stu-id="3bed2-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="3bed2-116">Les noms des éléments de tuple peuvent être inférés dans de nombreux cas à partir de l’initialisation du tuple.</span><span class="sxs-lookup"><span data-stu-id="3bed2-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
* [<span data-ttu-id="3bed2-117">Critères spéciaux sur les paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="3bed2-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="3bed2-118">Il est possible d’utiliser des expressions de critères spéciaux sur les variables dont le type est un paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="3bed2-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="3bed2-119">Enfin, le compilateur a deux options, `-refout` et `-refonly`, qui contrôlent la [génération d’assemblys de références](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="3bed2-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="3bed2-120">Pour utiliser les fonctionnalités les plus récentes dans une version mineure, vous devez [configurer la version du langage du compilateur](../language-reference/configure-language-version.md) et sélectionner la version.</span><span class="sxs-lookup"><span data-stu-id="3bed2-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

## <a name="async-main"></a><span data-ttu-id="3bed2-121">Async main</span><span class="sxs-lookup"><span data-stu-id="3bed2-121">Async main</span></span>

<span data-ttu-id="3bed2-122">Une méthode *async main* vous permet d’utiliser `await` dans votre méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="3bed2-122">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="3bed2-123">Auparavant, vous deviez écrire :</span><span class="sxs-lookup"><span data-stu-id="3bed2-123">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="3bed2-124">Vous pouvez désormais écrire :</span><span class="sxs-lookup"><span data-stu-id="3bed2-124">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="3bed2-125">Si votre programme ne retourne pas de code de sortie, vous pouvez déclarer une méthode `Main` qui retourne une <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="3bed2-125">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="3bed2-126">Pour plus d’informations, voir l’article [async main](../programming-guide/main-and-command-args/index.md) du guide de programmation.</span><span class="sxs-lookup"><span data-stu-id="3bed2-126">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="3bed2-127">Expressions littérales par défaut</span><span class="sxs-lookup"><span data-stu-id="3bed2-127">Default literal expressions</span></span>

<span data-ttu-id="3bed2-128">Les expressions littérales par défaut sont une amélioration des expressions de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3bed2-128">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="3bed2-129">Ces expressions initialisent une variable à la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3bed2-129">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="3bed2-130">Vous deviez écrire auparavant :</span><span class="sxs-lookup"><span data-stu-id="3bed2-130">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="3bed2-131">Vous pouvez désormais omettre le type du côté droit de l’initialisation :</span><span class="sxs-lookup"><span data-stu-id="3bed2-131">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="3bed2-132">Pour plus d’informations sur cette amélioration, voir l’article [Expressions de valeur par défaut](../programming-guide/statements-expressions-operators/default-value-expressions.md) du guide de programmation C#.</span><span class="sxs-lookup"><span data-stu-id="3bed2-132">You can learn more about this enhancement in the C# Programming Guide article on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="3bed2-133">Cette amélioration change également certaines des règles d’analyse pour le [mot clé default](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="3bed2-133">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="3bed2-134">Noms des éléments de tuple inférés</span><span class="sxs-lookup"><span data-stu-id="3bed2-134">Inferred tuple element names</span></span>

<span data-ttu-id="3bed2-135">Cette fonctionnalité est une petite amélioration de la fonctionnalité des tuples introduite dans C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="3bed2-135">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="3bed2-136">Très souvent, quand vous initialisez un tuple, les variables utilisées pour le côté droit de l’affectation sont identiques aux noms que vous souhaitez pour les éléments du tuple :</span><span class="sxs-lookup"><span data-stu-id="3bed2-136">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="3bed2-137">Dans C# 7.1, les noms des éléments du tuple peuvent être inférés à partir des variables utilisées pour initialiser le tuple :</span><span class="sxs-lookup"><span data-stu-id="3bed2-137">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="3bed2-138">Pour plus d’informations sur cette fonctionnalité, voir l’article [Tuples](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="3bed2-138">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="3bed2-139">Critères spéciaux sur les paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="3bed2-139">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="3bed2-140">À compter de C# 7.1, l’expression de modèle de `is` et du modèle de type `switch` peut avoir le type d’un paramètre de type générique,</span><span class="sxs-lookup"><span data-stu-id="3bed2-140">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="3bed2-141">ce qui peut se révéler particulièrement utile pour vérifier des types potentiellement `struct` ou `class` tout en évitant le boxing.</span><span class="sxs-lookup"><span data-stu-id="3bed2-141">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="3bed2-142">Génération d’assemblys de références</span><span class="sxs-lookup"><span data-stu-id="3bed2-142">Reference assembly generation</span></span>

<span data-ttu-id="3bed2-143">Il existe deux nouvelles options du compilateur qui génèrent des *assemblys de références uniquement* : [-refout](../language-reference/compiler-options/refout-compiler-option.md) et [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3bed2-143">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="3bed2-144">Les articles en lien décrivent plus en détail ces options et les assemblys de références.</span><span class="sxs-lookup"><span data-stu-id="3bed2-144">The linked articles explain these options and reference assemblies in more detail.</span></span>

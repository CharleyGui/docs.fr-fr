---
title: new, modificateur - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 529d77b0a66a8a3cedfe7a400af0fb34dd653322
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795168"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="98b19-102">new, modificateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="98b19-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="98b19-103">En cas d'utilisation comme un modificateur de déclaration, le mot clé `new` masque explicitement un membre qui est hérité d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="98b19-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="98b19-104">Lorsque vous masquez un membre hérité, la version dérivée du membre remplace la version de classe de base.</span><span class="sxs-lookup"><span data-stu-id="98b19-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="98b19-105">Bien que vous puissiez masquer des membres sans utiliser le modificateur `new`, vous obtenez un avertissement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="98b19-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="98b19-106">Si vous utilisez `new` pour masquer explicitement un membre, il supprime cet avertissement.</span><span class="sxs-lookup"><span data-stu-id="98b19-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="98b19-107">Vous pouvez également utiliser le mot clé `new` pour [créer une instance d’un type](../operators/new-operator.md) ou l’utiliser comme une [contrainte de type générique](./new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="98b19-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="98b19-108">Pour masquer un membre hérité, déclarez-le dans la classe dérivée en utilisant le même nom de membre, puis modifiez-le à l'aide du mot-clé `new`.</span><span class="sxs-lookup"><span data-stu-id="98b19-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="98b19-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="98b19-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="98b19-110">Dans cet exemple, `BaseC.Invoke` est masqué par `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="98b19-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="98b19-111">Le champ `x` n'est pas affecté parce qu'il n'est pas masqué par un nom semblable.</span><span class="sxs-lookup"><span data-stu-id="98b19-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="98b19-112">Le masquage de noms par le biais de l'héritage peut prendre l'une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="98b19-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="98b19-113">En général, une constante, un champ, une propriété ou un type qui est introduit dans une classe ou une structure masque tous les membres de la classe de base qui partagent son nom.</span><span class="sxs-lookup"><span data-stu-id="98b19-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="98b19-114">Il existe des cas spéciaux.</span><span class="sxs-lookup"><span data-stu-id="98b19-114">There are special cases.</span></span> <span data-ttu-id="98b19-115">Par exemple, si vous déclarez un nouveau champ avec le nom `N` pour avoir un type qui n'est pas invocable, et qu'un type de base déclare `N` en tant que méthode, le nouveau champ ne masquera pas la déclaration de base dans la syntaxe d'appel.</span><span class="sxs-lookup"><span data-stu-id="98b19-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="98b19-116">Pour plus d’informations, consultez la section [Recherche de membres](~/_csharplang/spec/expressions.md#member-lookup) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="98b19-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="98b19-117">Une méthode introduite dans une classe ou une structure masque les propriétés, les champs et les types qui partagent ce nom, dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="98b19-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="98b19-118">Cela masque également toutes les méthodes de la classe de base ayant la même signature.</span><span class="sxs-lookup"><span data-stu-id="98b19-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="98b19-119">Un indexeur introduit dans une classe ou un struct masque tous les indexeurs de la classe de base ayant la même signature.</span><span class="sxs-lookup"><span data-stu-id="98b19-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="98b19-120">L’utilisation des opérateurs `new` et [override](override.md) sur le même membre est une erreur, car ces deux modificateurs ont des significations qui s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="98b19-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="98b19-121">Le modificateur `new` crée un nouveau membre avec le même nom et entraîne le masquage du membre d'origine.</span><span class="sxs-lookup"><span data-stu-id="98b19-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="98b19-122">Le modificateur `override` étend l'implémentation pour un membre hérité.</span><span class="sxs-lookup"><span data-stu-id="98b19-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="98b19-123">L'utilisation du modificateur `new` dans une déclaration qui ne masque pas un membre hérité génère un avertissement.</span><span class="sxs-lookup"><span data-stu-id="98b19-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="98b19-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="98b19-124">Example</span></span>

<span data-ttu-id="98b19-125">Dans cet exemple, une classe de base, `BaseC` et une classe dérivée, `DerivedC`, utilisent le même nom de champ `x`, masquant ainsi la valeur du champ hérité.</span><span class="sxs-lookup"><span data-stu-id="98b19-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="98b19-126">Cet exemple illustre l'utilisation du modificateur `new`.</span><span class="sxs-lookup"><span data-stu-id="98b19-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="98b19-127">Il montre aussi comment accéder aux membres masqués de la classe de base en utilisant leurs noms complets.</span><span class="sxs-lookup"><span data-stu-id="98b19-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="98b19-128"> Exemple</span><span class="sxs-lookup"><span data-stu-id="98b19-128">Example</span></span>

<span data-ttu-id="98b19-129">Dans cet exemple, une classe imbriquée masque une classe du même nom dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="98b19-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="98b19-130">Cet exemple illustre l'utilisation du modificateur `new` pour éliminer le message d'avertissement, ainsi que l'accès aux membres de la classe masquée à l'aide de leurs noms complets.</span><span class="sxs-lookup"><span data-stu-id="98b19-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="98b19-131">Si vous supprimez le modificateur `new`, le programme peut encore être compilé et exécuté, mais vous obtiendrez l'avertissement suivant :</span><span class="sxs-lookup"><span data-stu-id="98b19-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="98b19-132">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="98b19-132">C# language specification</span></span>

<span data-ttu-id="98b19-133">Pour plus d’informations, consultez la section [Modificateur new](~/_csharplang/spec/classes.md#the-new-modifier) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="98b19-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="98b19-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98b19-134">See also</span></span>

- [<span data-ttu-id="98b19-135">Référence C#</span><span class="sxs-lookup"><span data-stu-id="98b19-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="98b19-136">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="98b19-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="98b19-137">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="98b19-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="98b19-138">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="98b19-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="98b19-139">Versioning avec les mots clés override et new</span><span class="sxs-lookup"><span data-stu-id="98b19-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="98b19-140">Savoir quand utiliser les mots clés override et new</span><span class="sxs-lookup"><span data-stu-id="98b19-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)

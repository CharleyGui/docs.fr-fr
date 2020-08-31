---
description: new, opérateur - Référence C#
title: new, opérateur - Référence C#
ms.date: 06/25/2019
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 88ec929317d4e6c6651233c1a1aa0ce8a8cce611
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118271"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="4fac3-103">new, opérateur (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="4fac3-103">new operator (C# reference)</span></span>

<span data-ttu-id="4fac3-104">L’opérateur `new` crée une nouvelle instance d’un type.</span><span class="sxs-lookup"><span data-stu-id="4fac3-104">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="4fac3-105">Vous pouvez également utiliser le mot clé `new` comme [modificateur de déclaration de membre](../keywords/new-modifier.md) ou [contrainte de type générique](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="4fac3-105">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="4fac3-106">Appel du constructeur</span><span class="sxs-lookup"><span data-stu-id="4fac3-106">Constructor invocation</span></span>

<span data-ttu-id="4fac3-107">Pour créer une nouvelle instance d’un type, vous appelez généralement l’un des [constructeurs](../../programming-guide/classes-and-structs/constructors.md) de ce type, à l’aide de l’opérateur `new` :</span><span class="sxs-lookup"><span data-stu-id="4fac3-107">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

<span data-ttu-id="4fac3-108">Vous pouvez utiliser un [initialiseur d’objet ou de collection](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) avec l’opérateur `new` pour instancier et initialiser un objet dans une instruction, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4fac3-108">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="4fac3-109">Création de tableau</span><span class="sxs-lookup"><span data-stu-id="4fac3-109">Array creation</span></span>

<span data-ttu-id="4fac3-110">Vous utilisez également l’opérateur `new` pour créer une instance de tableau, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4fac3-110">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

<span data-ttu-id="4fac3-111">Utilisez la syntaxe d’initialisation de tableau pour créer une instance de tableau et la remplir avec des éléments dans une instruction.</span><span class="sxs-lookup"><span data-stu-id="4fac3-111">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="4fac3-112">L’exemple suivant montre différentes façons de procéder :</span><span class="sxs-lookup"><span data-stu-id="4fac3-112">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="4fac3-113">Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="4fac3-113">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="4fac3-114">Instanciation des types anonymes</span><span class="sxs-lookup"><span data-stu-id="4fac3-114">Instantiation of anonymous types</span></span>

<span data-ttu-id="4fac3-115">Pour créer une instance d’un [type anonyme](../../programming-guide/classes-and-structs/anonymous-types.md), utilisez l’opérateur `new` et la syntaxe d’initialiseur d’objet :</span><span class="sxs-lookup"><span data-stu-id="4fac3-115">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="4fac3-116">Destruction des instances de type</span><span class="sxs-lookup"><span data-stu-id="4fac3-116">Destruction of type instances</span></span>

<span data-ttu-id="4fac3-117">Vous n’êtes pas obligé de détruire les instances de type précédemment créées.</span><span class="sxs-lookup"><span data-stu-id="4fac3-117">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="4fac3-118">Les instances de types référence et valeur sont détruites automatiquement.</span><span class="sxs-lookup"><span data-stu-id="4fac3-118">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="4fac3-119">Les instances de types valeur sont détruites dès que le contexte dans lequel elles se trouvent est détruit.</span><span class="sxs-lookup"><span data-stu-id="4fac3-119">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="4fac3-120">Les instances de types référence sont détruites par le [garbage collector](../../../standard/garbage-collection/index.md) à une heure non spécifiée après la suppression de la dernière référence.</span><span class="sxs-lookup"><span data-stu-id="4fac3-120">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="4fac3-121">Pour les instances de type qui contiennent des ressources non managées, par exemple, un descripteur de fichier, il est recommandé d’utiliser le nettoyage déterministe pour s’assurer que les ressources qu’ils contiennent sont libérées dès que possible.</span><span class="sxs-lookup"><span data-stu-id="4fac3-121">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="4fac3-122">Pour plus d’informations, consultez la référence d’API <xref:System.IDisposable?displayProperty=nameWithType> et l’article [using, instruction](../keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4fac3-122">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4fac3-123">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="4fac3-123">Operator overloadability</span></span>

<span data-ttu-id="4fac3-124">Un type défini par l’utilisateur ne peut pas surcharger l’opérateur `new`.</span><span class="sxs-lookup"><span data-stu-id="4fac3-124">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4fac3-125">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4fac3-125">C# language specification</span></span>

<span data-ttu-id="4fac3-126">Pour plus d’informations, consultez la section [Opérateur new](~/_csharplang/spec/expressions.md#the-new-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4fac3-126">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4fac3-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fac3-127">See also</span></span>

- [<span data-ttu-id="4fac3-128">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="4fac3-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4fac3-129">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="4fac3-129">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="4fac3-130">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="4fac3-130">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)

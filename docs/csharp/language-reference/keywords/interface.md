---
title: interface - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 058d6b96e96a3237ebac2ca079807fd154715d68
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608653"
---
# <a name="interface-c-reference"></a><span data-ttu-id="cabd3-102">interface (référence C#)</span><span class="sxs-lookup"><span data-stu-id="cabd3-102">interface (C# Reference)</span></span>

<span data-ttu-id="cabd3-103">Une interface contient uniquement des signatures de [méthodes](../../programming-guide/classes-and-structs/methods.md), de [propriétés](../../programming-guide/classes-and-structs/properties.md), d’[événements](../../programming-guide/events/index.md) ou d’[indexeurs](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="cabd3-103">An interface contains only the signatures of [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [events](../../programming-guide/events/index.md) or [indexers](../../programming-guide/indexers/index.md).</span></span> <span data-ttu-id="cabd3-104">Une classe ou un struct qui implémente l’interface doit implémenter les membres de l’interface qui sont spécifiés dans la définition de l’interface.</span><span class="sxs-lookup"><span data-stu-id="cabd3-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="cabd3-105">Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="cabd3-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="cabd3-106">Pour plus d’informations et d’exemples, consultez [Interfaces](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="cabd3-106">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="cabd3-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="cabd3-107">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="cabd3-108">Une interface peut être membre d’un espace de noms ou d’une classe, et peut contenir les signatures des membres suivants :</span><span class="sxs-lookup"><span data-stu-id="cabd3-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>

- [<span data-ttu-id="cabd3-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="cabd3-109">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="cabd3-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="cabd3-110">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)

- [<span data-ttu-id="cabd3-111">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="cabd3-111">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)

- [<span data-ttu-id="cabd3-112">Événements</span><span class="sxs-lookup"><span data-stu-id="cabd3-112">Events</span></span>](event.md)

<span data-ttu-id="cabd3-113">Une interface peut hériter d’une ou de plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="cabd3-113">An interface can inherit from one or more base interfaces.</span></span>

<span data-ttu-id="cabd3-114">Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.</span><span class="sxs-lookup"><span data-stu-id="cabd3-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="cabd3-115">Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface.</span><span class="sxs-lookup"><span data-stu-id="cabd3-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="cabd3-116">Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface.</span><span class="sxs-lookup"><span data-stu-id="cabd3-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>

<span data-ttu-id="cabd3-117">Pour plus d’informations et plus d’exemples sur l’implémentation explicite des interfaces, consultez [Implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="cabd3-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="cabd3-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="cabd3-118">Example</span></span>

<span data-ttu-id="cabd3-119">L’exemple suivant montre une implémentation d’interface.</span><span class="sxs-lookup"><span data-stu-id="cabd3-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="cabd3-120">Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="cabd3-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="cabd3-121">Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.</span><span class="sxs-lookup"><span data-stu-id="cabd3-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="cabd3-122">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="cabd3-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cabd3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cabd3-123">See also</span></span>

- [<span data-ttu-id="cabd3-124">Référence C#</span><span class="sxs-lookup"><span data-stu-id="cabd3-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cabd3-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cabd3-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cabd3-126">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="cabd3-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cabd3-127">Types référence</span><span class="sxs-lookup"><span data-stu-id="cabd3-127">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="cabd3-128">Interfaces</span><span class="sxs-lookup"><span data-stu-id="cabd3-128">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="cabd3-129">Utilisation de propriétés</span><span class="sxs-lookup"><span data-stu-id="cabd3-129">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="cabd3-130">Utilisation d’indexeurs</span><span class="sxs-lookup"><span data-stu-id="cabd3-130">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="cabd3-131">class</span><span class="sxs-lookup"><span data-stu-id="cabd3-131">class</span></span>](class.md)
- [<span data-ttu-id="cabd3-132">struct</span><span class="sxs-lookup"><span data-stu-id="cabd3-132">struct</span></span>](struct.md)
- [<span data-ttu-id="cabd3-133">Interfaces</span><span class="sxs-lookup"><span data-stu-id="cabd3-133">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

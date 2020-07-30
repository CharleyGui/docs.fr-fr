---
title: Indexeurs dans les interfaces - Guide de programmation C#
description: Les indexeurs peuvent être déclarés sur une interface en C#. Découvrez comment les accesseurs d’indexeurs d’interface diffèrent des accesseurs d’indexeurs de classe.
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303099"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="33f8f-104">Indexeurs dans les interfaces (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="33f8f-104">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="33f8f-105">Des indexeurs peuvent être déclarés dans une [interface](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="33f8f-105">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="33f8f-106">Les accesseurs d’indexeurs d’interface se distinguent sur plusieurs plans des accesseurs d’indexeurs de [classe](../../language-reference/keywords/class.md), à savoir :</span><span class="sxs-lookup"><span data-stu-id="33f8f-106">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="33f8f-107">Les accesseurs d’interface n’utilisent pas de modificateurs.</span><span class="sxs-lookup"><span data-stu-id="33f8f-107">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="33f8f-108">Un accesseur d’interface n’a généralement pas de corps.</span><span class="sxs-lookup"><span data-stu-id="33f8f-108">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="33f8f-109">L’objectif de l’accesseur est d’indiquer si l’indexeur est en lecture-écriture, en lecture seule ou en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="33f8f-109">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="33f8f-110">Vous pouvez fournir une implémentation pour un indexeur défini dans une interface, mais cela est rare.</span><span class="sxs-lookup"><span data-stu-id="33f8f-110">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="33f8f-111">Les indexeurs définissent généralement une API pour accéder aux champs de données, et les champs de données ne peuvent pas être définis dans une interface.</span><span class="sxs-lookup"><span data-stu-id="33f8f-111">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="33f8f-112">L’exemple ci-dessous porte sur un accesseur d’indexeur d’interface :</span><span class="sxs-lookup"><span data-stu-id="33f8f-112">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="33f8f-113">La signature d’un indexeur doit se distinguer de tous les autres indexeurs déclarés dans la même interface.</span><span class="sxs-lookup"><span data-stu-id="33f8f-113">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="33f8f-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="33f8f-114">Example</span></span>

<span data-ttu-id="33f8f-115">L’exemple suivant montre comment implémenter des indexeurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="33f8f-115">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="33f8f-116">Dans l’exemple précédent, vous pouvez utiliser l’implémentation de membre d’interface explicite en utilisant le nom qualifié complet du membre d’interface.</span><span class="sxs-lookup"><span data-stu-id="33f8f-116">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="33f8f-117">Par exemple</span><span class="sxs-lookup"><span data-stu-id="33f8f-117">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="33f8f-118">Cependant, le nom qualifié complet est seulement nécessaire pour éviter toute ambiguïté quand la classe implémente plusieurs interfaces avec la même signature d’indexeur.</span><span class="sxs-lookup"><span data-stu-id="33f8f-118">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="33f8f-119">Par exemple, si une classe `Employee` implémente deux interfaces, `ICitizen` et `IEmployee`, et que les deux interfaces ont la même signature d’indexeur, l’implémentation de membre d’interface explicite est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="33f8f-119">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="33f8f-120">Autrement dit, la déclaration d’indexeur suivante :</span><span class="sxs-lookup"><span data-stu-id="33f8f-120">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="33f8f-121">implémente l’indexeur dans l’interface `IEmployee`, alors que la déclaration suivante :</span><span class="sxs-lookup"><span data-stu-id="33f8f-121">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="33f8f-122">implémente l’interface dans l’interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="33f8f-122">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="33f8f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33f8f-123">See also</span></span>

- [<span data-ttu-id="33f8f-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="33f8f-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="33f8f-125">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="33f8f-125">Indexers</span></span>](./index.md)
- [<span data-ttu-id="33f8f-126">Propriétés</span><span class="sxs-lookup"><span data-stu-id="33f8f-126">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="33f8f-127">Interfaces</span><span class="sxs-lookup"><span data-stu-id="33f8f-127">Interfaces</span></span>](../interfaces/index.md)

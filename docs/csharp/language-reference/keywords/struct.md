---
title: struct - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 5317ea403575dca7ed64a5784fa9c993fa8d2f64
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633842"
---
# <a name="struct-c-reference"></a><span data-ttu-id="50f76-102">struct (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="50f76-102">struct (C# Reference)</span></span>

<span data-ttu-id="50f76-103">Un type `struct` est un type valeur utilisé pour encapsuler de petits groupes de variables liées, par exemple les coordonnées d'un rectangle ou les caractéristiques d'un élément dans un inventaire.</span><span class="sxs-lookup"><span data-stu-id="50f76-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="50f76-104">L'exemple suivant illustre une déclaration struct simple :</span><span class="sxs-lookup"><span data-stu-id="50f76-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="50f76-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="50f76-105">Remarks</span></span>

<span data-ttu-id="50f76-106">Les structs peuvent également contenir des [constructeurs](../../programming-guide/classes-and-structs/constructors.md), des [constantes](../../programming-guide/classes-and-structs/constants.md), des [champs](../../programming-guide/classes-and-structs/fields.md), des [méthodes](../../programming-guide/classes-and-structs/methods.md), des [propriétés](../../programming-guide/classes-and-structs/properties.md), des [indexeurs](../../programming-guide/indexers/index.md), des [opérateurs](../../programming-guide/statements-expressions-operators/operators.md), des [événements](../../programming-guide/events/index.md) et des [types imbriqués](../../programming-guide/classes-and-structs/nested-types.md). Toutefois, si plusieurs membres sont nécessaires, il est conseillé de plutôt utiliser une classe.</span><span class="sxs-lookup"><span data-stu-id="50f76-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../../programming-guide/statements-expressions-operators/operators.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="50f76-107">Pour obtenir des exemples, consultez [Utilisation de structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="50f76-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="50f76-108">Les structs peuvent implémenter une interface, mais ne peuvent pas hériter d'un autre struct.</span><span class="sxs-lookup"><span data-stu-id="50f76-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="50f76-109">C'est pourquoi, les membres struct ne peuvent pas être déclarés en tant que `protected`.</span><span class="sxs-lookup"><span data-stu-id="50f76-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="50f76-110">Pour plus d’informations, consultez [Structs](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="50f76-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="50f76-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="50f76-111">Examples</span></span>

<span data-ttu-id="50f76-112">Pour obtenir des exemples et des informations supplémentaires, consultez [Utilisation de structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="50f76-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="50f76-113">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="50f76-113">C# language specification</span></span>

<span data-ttu-id="50f76-114">Pour obtenir des exemples, consultez [Utilisation de structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="50f76-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="50f76-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50f76-115">See also</span></span>

- [<span data-ttu-id="50f76-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="50f76-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="50f76-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="50f76-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="50f76-118">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="50f76-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="50f76-119">Tableau des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="50f76-119">Default Values Table</span></span>](default-values-table.md)
- [<span data-ttu-id="50f76-120">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="50f76-120">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="50f76-121">Types</span><span class="sxs-lookup"><span data-stu-id="50f76-121">Types</span></span>](types.md)
- [<span data-ttu-id="50f76-122">Types valeur</span><span class="sxs-lookup"><span data-stu-id="50f76-122">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="50f76-123">class</span><span class="sxs-lookup"><span data-stu-id="50f76-123">class</span></span>](class.md)
- [<span data-ttu-id="50f76-124">interface</span><span class="sxs-lookup"><span data-stu-id="50f76-124">interface</span></span>](interface.md)
- [<span data-ttu-id="50f76-125">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="50f76-125">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)

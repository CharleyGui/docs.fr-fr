---
title: struct - Référence C#
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 8d9a23a0813423571c894758257b284ad67a72e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744648"
---
# <a name="struct-c-reference"></a><span data-ttu-id="8251f-102">struct (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="8251f-102">struct (C# Reference)</span></span>

<span data-ttu-id="8251f-103">Un type `struct` est un type valeur utilisé pour encapsuler de petits groupes de variables liées, par exemple les coordonnées d'un rectangle ou les caractéristiques d'un élément dans un inventaire.</span><span class="sxs-lookup"><span data-stu-id="8251f-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="8251f-104">L'exemple suivant illustre une déclaration struct simple :</span><span class="sxs-lookup"><span data-stu-id="8251f-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="8251f-105">Notes</span><span class="sxs-lookup"><span data-stu-id="8251f-105">Remarks</span></span>

<span data-ttu-id="8251f-106">Les structs peuvent également contenir des [constructeurs](../../programming-guide/classes-and-structs/constructors.md), des [constantes](../../programming-guide/classes-and-structs/constants.md), des [champs](../../programming-guide/classes-and-structs/fields.md), des [méthodes](../../programming-guide/classes-and-structs/methods.md), des [propriétés](../../programming-guide/classes-and-structs/properties.md), des [indexeurs](../../programming-guide/indexers/index.md), des [opérateurs](../operators/index.md), des [événements](../../programming-guide/events/index.md) et des [types imbriqués](../../programming-guide/classes-and-structs/nested-types.md). Toutefois, si plusieurs membres sont nécessaires, il est conseillé de plutôt utiliser une classe.</span><span class="sxs-lookup"><span data-stu-id="8251f-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../operators/index.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="8251f-107">Pour obtenir des exemples, consultez [Utilisation de structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="8251f-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="8251f-108">Les structs peuvent implémenter une interface, mais ne peuvent pas hériter d'un autre struct.</span><span class="sxs-lookup"><span data-stu-id="8251f-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="8251f-109">C'est pourquoi, les membres struct ne peuvent pas être déclarés en tant que `protected`.</span><span class="sxs-lookup"><span data-stu-id="8251f-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="8251f-110">Pour plus d’informations, consultez [Structs](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="8251f-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="8251f-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="8251f-111">Examples</span></span>

<span data-ttu-id="8251f-112">Pour obtenir des exemples et des informations supplémentaires, consultez [Utilisation de structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="8251f-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8251f-113">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8251f-113">C# language specification</span></span>

<span data-ttu-id="8251f-114">Pour obtenir des exemples, consultez [Utilisation de structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="8251f-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8251f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8251f-115">See also</span></span>

- [<span data-ttu-id="8251f-116">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="8251f-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8251f-117">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="8251f-117">C# keywords</span></span>](index.md)
- [<span data-ttu-id="8251f-118">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="8251f-118">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="8251f-119">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="8251f-119">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="8251f-120">class</span><span class="sxs-lookup"><span data-stu-id="8251f-120">class</span></span>](class.md)
- [<span data-ttu-id="8251f-121">interface</span><span class="sxs-lookup"><span data-stu-id="8251f-121">interface</span></span>](interface.md)
- [<span data-ttu-id="8251f-122">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="8251f-122">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)

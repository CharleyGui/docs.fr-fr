---
description: value, mot clé contextuel - Référence C#
title: value, mot clé contextuel - Référence C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: ad2eb6f12d8c295dc5203994d6c570cd2377e3ee
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828914"
---
# <a name="value-c-reference"></a><span data-ttu-id="58a4d-103">value (référence C#)</span><span class="sxs-lookup"><span data-stu-id="58a4d-103">value (C# Reference)</span></span>

<span data-ttu-id="58a4d-104">Le mot clé contextuel `value` est utilisé dans l' `set` accesseur dans les déclarations de [propriété](../../programming-guide/classes-and-structs/properties.md) et d' [indexeur](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="58a4d-104">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="58a4d-105">Elle est similaire à un paramètre d’entrée d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="58a4d-105">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="58a4d-106">Le mot `value` fait référence à la valeur que le code client tente d’assigner à la propriété ou à l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="58a4d-106">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="58a4d-107">Dans l’exemple suivant, `MyDerivedClass` a une propriété appelée `Name` qui utilise le paramètre `value` pour assigner une nouvelle chaîne au `name` du champ de stockage.</span><span class="sxs-lookup"><span data-stu-id="58a4d-107">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="58a4d-108">Du point de vue du code client, l’opération est écrite comme une assignation simple.</span><span class="sxs-lookup"><span data-stu-id="58a4d-108">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="58a4d-109">Pour plus d’informations, consultez les articles [Propriétés](../../programming-guide/classes-and-structs/properties.md) et [indexeurs](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="58a4d-109">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexers](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="58a4d-110">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="58a4d-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="58a4d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58a4d-111">See also</span></span>

- [<span data-ttu-id="58a4d-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="58a4d-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="58a4d-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="58a4d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="58a4d-114">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="58a4d-114">C# Keywords</span></span>](index.md)

---
title: value, mot clé contextuel - Référence C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712895"
---
# <a name="value-c-reference"></a><span data-ttu-id="bcf4a-102">value (référence C#)</span><span class="sxs-lookup"><span data-stu-id="bcf4a-102">value (C# Reference)</span></span>

<span data-ttu-id="bcf4a-103">Le mot clé contextuel `value` est utilisé dans l’accesseur `set` dans les déclarations de [propriété](../../programming-guide/classes-and-structs/properties.md) et d' [indexeur](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="bcf4a-103">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="bcf4a-104">Elle est similaire à un paramètre d’entrée d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="bcf4a-104">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="bcf4a-105">Le mot `value` fait référence à la valeur que le code client tente d’assigner à la propriété ou à l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="bcf4a-105">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="bcf4a-106">Dans l’exemple suivant, `MyDerivedClass` a une propriété appelée `Name` qui utilise le paramètre `value` pour assigner une nouvelle chaîne au `name` du champ de stockage.</span><span class="sxs-lookup"><span data-stu-id="bcf4a-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="bcf4a-107">Du point de vue du code client, l’opération est écrite comme une assignation simple.</span><span class="sxs-lookup"><span data-stu-id="bcf4a-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="bcf4a-108">Pour plus d’informations, consultez les articles [Propriétés](../../programming-guide/classes-and-structs/properties.md) et [Indexeres](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="bcf4a-108">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bcf4a-109">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bcf4a-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bcf4a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcf4a-110">See also</span></span>

- [<span data-ttu-id="bcf4a-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="bcf4a-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bcf4a-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bcf4a-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bcf4a-113">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="bcf4a-113">C# Keywords</span></span>](index.md)

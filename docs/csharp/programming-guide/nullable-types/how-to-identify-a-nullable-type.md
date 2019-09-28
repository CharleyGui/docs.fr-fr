---
title: 'Comment : identifier un guide de C# programmation de type valeur Nullable'
ms.custom: seodec18
description: Découvrez comment déterminer si un type est un type valeur Nullable ou si une instance est d’un type valeur Nullable
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 15b1ffedf57648955ee5a004514841a5d140292b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392609"
---
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a><span data-ttu-id="96360-103">Comment : identifier un type valeur Nullable (guideC# de programmation)</span><span class="sxs-lookup"><span data-stu-id="96360-103">How to: identify a nullable value type (C# Programming Guide)</span></span>

<span data-ttu-id="96360-104">L’exemple suivant montre comment déterminer si une instance <xref:System.Type?displayProperty=nameWithType> représente un type valeur Nullable générique fermé, autrement dit, le type <xref:System.Nullable%601?displayProperty=nameWithType> avec un paramètre de type spécifié `T` :</span><span class="sxs-lookup"><span data-stu-id="96360-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="96360-105">Comme l’illustre l’exemple, vous utilisez l’opérateur [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) pour créer un objet <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="96360-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="96360-106">Si vous souhaitez déterminer si une instance est d’un type de valeur Nullable, n’utilisez pas la méthode <xref:System.Object.GetType%2A?displayProperty=nameWithType> pour obtenir une instance <xref:System.Type> à tester avec le code précédent.</span><span class="sxs-lookup"><span data-stu-id="96360-106">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="96360-107">Quand vous appelez la méthode <xref:System.Object.GetType%2A?displayProperty=nameWithType> sur une instance d’un type valeur Nullable, l’instance est [convertie](using-nullable-types.md#boxing-and-unboxing) en <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="96360-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="96360-108">La conversion boxing d’une instance non null d’un type valeur Nullable équivaut au boxing d’une valeur du type sous-jacent, <xref:System.Object.GetType%2A> retourne un objet <xref:System.Type> qui représente le type sous-jacent d’un type valeur Nullable :</span><span class="sxs-lookup"><span data-stu-id="96360-108">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="96360-109">N’utilisez pas l’opérateur [is](../../language-reference/keywords/is.md) pour déterminer si une instance est d’un type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="96360-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="96360-110">Comme le montre l’exemple suivant, vous ne pouvez pas distinguer les types d’instances d’un type valeur Nullable et son type sous-jacent à l’aide de l’opérateur `is` :</span><span class="sxs-lookup"><span data-stu-id="96360-110">As the following example shows, you cannot distinguish types of instances of a nullable value type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="96360-111">Vous pouvez utiliser le code présenté dans l’exemple suivant pour déterminer si une instance est d’un type valeur Nullable :</span><span class="sxs-lookup"><span data-stu-id="96360-111">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a><span data-ttu-id="96360-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96360-112">See also</span></span>

- [<span data-ttu-id="96360-113">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="96360-113">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="96360-114">Utilisation des types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="96360-114">Using nullable value types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>

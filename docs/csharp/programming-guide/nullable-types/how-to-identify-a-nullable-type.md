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
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a>Comment : identifier un type valeur Nullable (guideC# de programmation)

L’exemple suivant montre comment déterminer si une instance <xref:System.Type?displayProperty=nameWithType> représente un type valeur Nullable générique fermé, autrement dit, le type <xref:System.Nullable%601?displayProperty=nameWithType> avec un paramètre de type spécifié `T` :

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Comme l’illustre l’exemple, vous utilisez l’opérateur [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) pour créer un objet <xref:System.Type?displayProperty=nameWithType>.

Si vous souhaitez déterminer si une instance est d’un type de valeur Nullable, n’utilisez pas la méthode <xref:System.Object.GetType%2A?displayProperty=nameWithType> pour obtenir une instance <xref:System.Type> à tester avec le code précédent. Quand vous appelez la méthode <xref:System.Object.GetType%2A?displayProperty=nameWithType> sur une instance d’un type valeur Nullable, l’instance est [convertie](using-nullable-types.md#boxing-and-unboxing) en <xref:System.Object>. La conversion boxing d’une instance non null d’un type valeur Nullable équivaut au boxing d’une valeur du type sous-jacent, <xref:System.Object.GetType%2A> retourne un objet <xref:System.Type> qui représente le type sous-jacent d’un type valeur Nullable :

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

N’utilisez pas l’opérateur [is](../../language-reference/keywords/is.md) pour déterminer si une instance est d’un type valeur Nullable. Comme le montre l’exemple suivant, vous ne pouvez pas distinguer les types d’instances d’un type valeur Nullable et son type sous-jacent à l’aide de l’opérateur `is` :

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Vous pouvez utiliser le code présenté dans l’exemple suivant pour déterminer si une instance est d’un type valeur Nullable :

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a>Voir aussi

- [Types valeur Nullable](index.md)
- [Utilisation des types valeur Nullable](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>

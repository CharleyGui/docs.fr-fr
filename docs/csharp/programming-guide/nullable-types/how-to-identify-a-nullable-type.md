---
title: 'Procédure : Identifier un type Nullable - Guide de programmation C#'
ms.custom: seodec18
description: Découvrez comment déterminer si un type est un type Nullable ou si une instance est d’un type Nullable.
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 43a35874b8c9f52c4b98a93e1217994980e1b223
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567381"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Procédure : Identifier un type Nullable (Guide de programmation C#)

L’exemple suivant montre comment déterminer si une instance <xref:System.Type?displayProperty=nameWithType> représente un type nullable générique fermé, autrement dit, le type <xref:System.Nullable%601?displayProperty=nameWithType> avec un paramètre de type spécifié `T` :

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Comme l’illustre l’exemple, vous utilisez l’opérateur [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) pour créer un objet <xref:System.Type?displayProperty=nameWithType>.  
  
Si vous souhaitez déterminer si une instance est d’un type Nullable, n’utilisez pas la méthode <xref:System.Object.GetType%2A?displayProperty=nameWithType> pour obtenir une instance <xref:System.Type> à tester avec le code précédent. Quand vous appelez la méthode <xref:System.Object.GetType%2A?displayProperty=nameWithType> sur une instance d’un type Nullable, l’instance est [boxed](using-nullable-types.md#boxing-and-unboxing) à <xref:System.Object>. Comme le boxing d’une instance non nulle d’un type Nullable équivaut au boxing d’une valeur du type sous-jacent, <xref:System.Object.GetType%2A> retourne un objet <xref:System.Type> qui représente le type sous-jacent d’un type Nullable :

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

N’utilisez pas l’opérateur [is](../../language-reference/keywords/is.md) pour déterminer si une instance est d’un type Nullable. Comme le montre l’exemple suivant, vous ne pouvez pas distinguer les types des instances d’un type Nullable et son type sous-jacent à l’aide de l’opérateur `is` :

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Vous pouvez utiliser le code présenté dans l’exemple suivant pour déterminer si une instance est d’un type Nullable :

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>Voir aussi

- [Types Nullable](index.md)
- [Utilisation de types Nullable](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>

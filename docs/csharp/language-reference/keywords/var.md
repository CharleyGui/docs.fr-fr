---
title: var - Référence C#
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712882"
---
# <a name="var-c-reference"></a>var (référence C#)

Depuis Visual C# 3.0, les variables déclarées à la portée de la méthode peuvent avoir un type implicite `var`. Une variable locale implicitement typée est fortement typée comme si vous aviez déclaré vous-même le type, alors que c’est le compilateur qui détermine le type. Les deux déclarations suivantes d’`i` sont équivalentes fonctionnellement :

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Pour de plus amples renseignements, voir les variables locales et les [relations de type dactylographiées implicitement dans les opérations de requête LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)

## <a name="example"></a> Exemple

L’exemple suivant présente deux expressions de requête. Dans la première expression, l’utilisation de `var` est autorisée, mais n’est pas obligatoire parce que le type du résultat de la requête peut être déclaré explicitement en tant que `IEnumerable<string>`. Toutefois, dans la deuxième expression où `var` est utilisé, le résultat peut être une collection de types anonymes, et le nom de ce type n’est pas accessible sauf par le compilateur. Si vous utilisez `var`, vous n’avez pas besoin de créer une classe pour le résultat. Notez que, dans le deuxième exemple, la variable d’itération `foreach``item` doit également être implicitement typée.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Variables locales implicitement dactylographiques](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)

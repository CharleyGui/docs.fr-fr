---
description: var-référence C#
title: var-référence C#
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d04bea9bcf5be726d3e81a1a53abed31f59330a0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608710"
---
# <a name="var-c-reference"></a>var (référence C#)

À compter de C# 3, les variables déclarées au niveau de la portée de la méthode peuvent avoir un « type » implicite `var` . Une variable locale implicitement typée est fortement typée comme si vous aviez déclaré vous-même le type, alors que c’est le compilateur qui détermine le type. Les deux déclarations suivantes d’`i` sont équivalentes fonctionnellement :

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> Quand `var` est utilisé avec les [types référence Nullable](../builtin-types/nullable-reference-types.md) activés, il implique toujours un type référence Nullable même si le type d’expression n’accepte pas la valeur null.

Le `var` mot clé est couramment utilisé avec les expressions d’appel de constructeur. L’utilisation de `var` vous permet de ne pas répéter un nom de type dans une déclaration de variable et une instanciation d’objet, comme le montre l’exemple suivant :

```csharp
var xs = new List<int>();
```

À compter de C# 9,0, vous pouvez utiliser une [ `new` expression](../operators/new-operator.md) de type cible comme alternative :

```csharp
List<int> xs = new();
List<int>? ys = new();
```

## <a name="example"></a> Exemple

L’exemple suivant présente deux expressions de requête. Dans la première expression, l’utilisation de `var` est autorisée, mais n’est pas obligatoire parce que le type du résultat de la requête peut être déclaré explicitement en tant que `IEnumerable<string>`. Toutefois, dans la deuxième expression où `var` est utilisé, le résultat peut être une collection de types anonymes, et le nom de ce type n’est pas accessible sauf par le compilateur. Si vous utilisez `var`, vous n’avez pas besoin de créer une classe pour le résultat. Notez que, dans le deuxième exemple, la variable d’itération `foreach``item` doit également être implicitement typée.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Variables locales implicitement typées](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [Relations de types dans les opérations de requête LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)

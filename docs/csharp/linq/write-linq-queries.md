---
title: Écrire des requêtes LINQ en C#
description: Découvrez comment écrire des requêtes LINQ en C#.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: ed32543b0422e0664a8577f2c27f7c7c00a719a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632874"
---
# <a name="write-linq-queries-in-c"></a>Écrire des requêtes LINQ en C\#

Cet article présente les trois façons d’écrire une requête LINQ en C# :

1. Utilisez la syntaxe de requête.

2. Utilisez la syntaxe de méthode.

3. Utilisez une combinaison de syntaxe de requête et de syntaxe de méthode.

Les exemples suivants montrent des requêtes LINQ simples en utilisant chaque approche répertoriée précédemment. En général, la règle consiste à utiliser (1) dès que possible et à utiliser (2) et (3) dès que cela est nécessaire.

> [!NOTE]
> Ces requêtes fonctionnent sur les collections simples en mémoire ; toutefois, la syntaxe de base est identique à celle utilisée dans LINQ to Entities et LINQ to XML.

## <a name="example---query-syntax"></a>Exemple – Syntaxe de requête

La méthode recommandée pour écrire la plupart des requêtes consiste à utiliser la *syntaxe de requête* pour créer des *expressions de requête*. L’exemple suivant présente trois expressions de requête. La première expression de requête montre comment filtrer ou restreindre des résultats en appliquant des conditions avec une clause `where`. Tous les éléments de la séquence source dont la valeur est supérieure à 7 ou inférieure à 3 sont retournés. La deuxième expression montre comment classer les résultats retournés. La troisième expression montre comment regrouper des résultats en fonction d’une clé. Cette requête retourne deux groupes en fonction de la première lettre du mot.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Notez que le type des requêtes est <xref:System.Collections.Generic.IEnumerable%601>. Toutes ces requêtes pourraient être écrites à l’aide de `var`, comme illustré dans l’exemple suivant :

`var query = from num in numbers...`

Dans chacun des exemples précédents, les requêtes ne s’exécutent pas réellement tant vous n’avez pas itéré la variable de requête dans une instruction `foreach` ou une autre instruction. Pour plus d’informations, voir [Introduction aux requêtes LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="example---method-syntax"></a>Exemple – Syntaxe de méthode

Certaines opérations de requête doivent être exprimées comme un appel de méthode. Les plus répandues de ces méthodes retournent des valeurs numériques uniques, telles que <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, et ainsi de suite. Ces méthodes doivent toujours être appelées en dernier dans toutes les requêtes, car elles ne représentent qu’une valeur unique et ne peuvent pas servir de source pour une opération de requête supplémentaire. L’exemple suivant présente un appel de méthode dans une expression de requête :

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Si la méthode a des paramètres Action ou Func, ceux-ci sont fournis sous la forme d’une expression [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md), comme dans l’exemple suivant :

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

Dans les requêtes précédentes, seule la requête 4 s’exécute immédiatement. Cela s’explique par le fait qu’elle retourne une valeur unique et non une collection <xref:System.Collections.Generic.IEnumerable%601> générique. La méthode elle-même doit utiliser `foreach` pour calculer sa valeur.

Chacune des requêtes précédentes peut être écrite en utilisant des types implicites avec [var](../language-reference/keywords/var.md), comme dans l’exemple suivant :

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Exemple – Syntaxe de méthode et de requête mixte

Cet exemple montre comment utiliser la syntaxe de méthode sur les résultats d’une clause de requête. Encadrez simplement l’expression de requête entre parenthèses, puis appliquez l’opérateur point et appelez la méthode. Dans l’exemple suivant, la requête 7 retourne les nombres dont la valeur est comprise entre 3 et 7. Toutefois, il est généralement préférable d’utiliser une deuxième variable pour stocker le résultat de l’appel de méthode. De cette manière, il est moins probable que la requête ne soit confondue avec les résultats de la requête.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Comme la requête 7 retourne une valeur unique et non une collection, la requête s’exécute immédiatement.

La requête précédente peut être écrite en utilisant des types implicites avec `var`, comme suit :

```csharp
var numCount = (from num in numbers...
```

Elle peut être écrite dans la syntaxe de méthode comme suit :

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

Elle peut être écrite en utilisant des types explicites, comme suit :

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : écriture de requêtes en C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Requête intégrée linguistique (LINQ)](index.md)
- [où la clause](../language-reference/keywords/where-clause.md)

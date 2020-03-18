---
title: Types de frameworks prenant en charge les arborescences d’expressions
description: En savoir plus sur les types de frameworks prenant en charge les arborescences d’expressions, la création d’arborescences d’expressions et les techniques d’utilisation des API d’arborescences d’expressions.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 8483c46dde3ea97138e55ab84a5924a3d2578730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146084"
---
# <a name="framework-types-supporting-expression-trees"></a>Types de frameworks prenant en charge les arborescences d’expressions

[Précédent – Explication des arborescences d’expressions](expression-trees-explained.md)

Il existe une longue liste de classes dans le framework .NET Core qui fonctionnent avec des arborescences d’expressions.
Vous pouvez voir la liste complète dans <xref:System.Linq.Expressions>.
Au lieu de parcourir la liste complète, essayons de comprendre comment les classes du framework ont été conçues.

Dans la conception du langage, une expression est un corps de code qui évalue et retourne une valeur. Les expressions peuvent être très simples : l’expression constante `1` retourne la valeur constante 1. Elles peuvent être plus compliquées : l’expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` retourne une racine pour une équation quadratique (dans le cas où l’équation a une solution).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Tout commence par System.Linq.Expression

L’une des complexités liées à l’utilisation des arborescences d’expressions est que de nombreuses sortes d’expressions sont valides à de nombreux endroits dans les programmes. Prenez par exemple une expression d’assignation. La partie droite d’une assignation peut être une valeur constante, une variable, une expression d’appel de méthode ou autre. Cette flexibilité linguistique signifie que vous pouvez rencontrer de nombreux types d’expressions différents à n’importe quel endroit dans les nœuds d’une arborescence quand vous parcourez une arborescence d’expressions. Ainsi, quand vous pouvez travailler avec le type d’expression de base, c’est le moyen le plus simple de procéder. Cependant, vous devez parfois en savoir plus.
La classe Expression de base contient une propriété `NodeType` à cet effet.
Elle retourne un `ExpressionType` qui est une énumération des types d’expressions possibles.
Une fois que vous connaissez le type du nœud, vous pouvez le caster en ce type et effectuer des actions spécifiques. Vous pouvez rechercher certains types de nœuds, puis utiliser les propriétés spécifiques de ce genre d’expression.

Par exemple, ce code imprime le nom d’une variable pour une expression d’accès à la variable. J’ai suivi la pratique qui consiste à vérifier le type de nœud, à caster en une expression d’accès à la variable, puis à vérifier les propriétés du type d’expression spécifique :

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a>Création d’arborescences d’expressions

La classe `System.Linq.Expression` contient également de nombreuses méthodes statiques pour créer des expressions. Ces méthodes créent un nœud d’expression en utilisant les arguments fournis pour ses enfants. De cette façon, vous générez une expression à partir de ses nœuds terminaux. Par exemple, ce code génère une expression Add :

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Vous pouvez constater d’après cet exemple simple que de nombreux types sont impliqués dans la création et l’utilisation des arborescences d’expressions. Cette complexité est nécessaire pour fournir les fonctionnalités du vocabulaire enrichi fourni par le langage C#.

## <a name="navigating-the-apis"></a>Navigation dans les API
Il existe des types de nœuds Expression qui mappent à presque tous les éléments de syntaxe du langage C#. Chaque type a des méthodes spécifiques pour ce type d’élément de langage. Cela fait beaucoup de choses à mémoriser en même temps. Plutôt que d’essayer de mémoriser tout, voici les techniques que je vous conseille d’appliquer quand vous travaillez avec des arborescences d’expressions :

1. Examinez les membres de l’énumération `ExpressionType` pour déterminer les éventuels nœuds à examiner. Cela aide vraiment quand vous souhaitez parcourir et comprendre une arborescence d’expressions.
2. Examinez les membres statiques de la classe `Expression` pour générer une expression. Ces méthodes peuvent générer tout type d’expression à partir d’un ensemble de ses nœuds enfants.
3. Examinez la classe `ExpressionVisitor` pour générer une arborescence d’expressions modifiée.

Vous trouverez davantage de choses à mesure que vous examinez chacune de ces trois zones. Vous trouverez invariablement ce dont vous avez besoin si vous commencez avec l’une de ces trois étapes.

 [Suivant – Exécution d’arborescences d’expressions](expression-trees-execution.md)

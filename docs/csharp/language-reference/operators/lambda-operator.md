---
title: Opérateur >= - Référence C#
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: a7fea9810cb02269278638ec71cd106463b029e9
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025014"
---
# <a name="-operator-c-reference"></a>Opérateur >= (référence C#)

Le jeton `=>` est pris en charge sous deux formes : comme opérateur lambda, et comme séparateur d’un nom de membre et de l’implémentation de membre dans une définition de corps d’expression.

## <a name="lambda-operator"></a>Opérateur lamdba

Dans les [expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), l’opérateur lambda `=>` sépare les variables d’entrée du côté gauche et le corps lambda du côté droit.

L’exemple suivant utilise la fonctionnalité [LINQ](../../programming-guide/concepts/linq/index.md) avec la syntaxe de méthode pour illustrer l’utilisation d’expressions lambda :

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Les variables d’entrée des expressions lambda sont fortement typées au moment de la compilation. Quand le compilateur peut déduire les types des variables d’entrée, comme dans l’exemple précédent, vous pouvez omettre les déclarations de type. Si vous avez besoin de spécifier le type des variables d’entrée, vous devez le faire pour chaque variable, comme le montre l’exemple suivant :

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

L’exemple suivant illustre comment définir une expression lambda sans variable d’entrée :

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Pour plus d’informations, consultez [Expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Définition de corps d’expression

La syntaxe générale d’une définition de corps d’expression est la suivante :

```csharp
member => expression;
```

où *expression* est une expression valide. Notez que *expression* peut être une *expression d’instruction* seulement si le type de retour du membre est `void`, ou si le membre est un constructeur, un finaliseur ou un accesseur de propriété `set`.

L’exemple suivant montre une définition de corps d’expression pour une méthode `Person.ToString` :

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Il s’agit d’une version raccourcie de la définition de méthode suivante :

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

Les définitions de corps d’expression pour les méthodes et les propriétés en lecture seule sont prises en charge à compter de C# 6. Les définitions de corps d’expression pour les constructeurs, les finaliseurs, les accesseurs de propriétés et les indexeurs sont prises en charge à compter de C# 7.0.

Pour plus d’informations, consultez [Membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

L’opérateur `=>` ne peut pas être surchargé.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Expressions de fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](../language-specification/index.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)

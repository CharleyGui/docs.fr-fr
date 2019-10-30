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
ms.openlocfilehash: b8d1a4e3971eb30e76bf543497931ce029c5541d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036379"
---
# <a name="-operator-c-reference"></a>Opérateur >= (référence C#)

Le jeton `=>` est pris en charge sous deux formes : comme [opérateur lambda](#lambda-operator) et comme séparateur d’un nom de membre et l’implémentation de membre dans une [définition de corps d’expression](#expression-body-definition).

## <a name="lambda-operator"></a>Opérateur lamdba

Dans les [expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), l’opérateur lambda `=>` sépare les paramètres d’entrée du côté gauche du corps lambda situé à droite.

L’exemple suivant utilise la fonctionnalité [LINQ](../../programming-guide/concepts/linq/index.md) avec la syntaxe de méthode pour illustrer l’utilisation d’expressions lambda :

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Les paramètres d’entrée d’une expression lambda sont fortement typés au moment de la compilation. Lorsque le compilateur peut déduire les types de paramètres d’entrée, comme dans l’exemple précédent, vous pouvez omettre des déclarations de type. Si vous devez spécifier le type des paramètres d’entrée, vous devez le faire pour chaque paramètre, comme le montre l’exemple suivant :

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

L’exemple suivant montre comment définir une expression lambda sans paramètres d’entrée :

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Pour plus d’informations, consultez [Expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Définition de corps d’expression

La syntaxe générale d’une définition de corps d’expression est la suivante :

```csharp
member => expression;
```

où `expression` est une expression valide. Le type de retour de `expression` doit être implicitement convertible en type de retour du membre. Si le type de retour du membre est `void` ou si le membre est un constructeur, un finaliseur ou un accesseur de propriété `set`, `expression` doit être une [*expression d’instruction*](~/_csharplang/spec/statements.md#expression-statements), qui peut être de n’importe quel type.

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

Les définitions de corps d’expression pour les méthodes, les opérateurs et les propriétés en lecture C# seule sont prises en charge à partir de 6. Les définitions de corps d’expression pour les constructeurs, les finaliseurs et les accesseurs de propriété et d' C# indexeur sont pris en charge à partir de 7,0.

Pour plus d’informations, consultez [Membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

L’opérateur `=>` ne peut pas être surchargé.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations sur l’opérateur lambda, consultez la section [expressions de fonction anonymes](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)

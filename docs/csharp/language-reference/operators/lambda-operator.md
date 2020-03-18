---
title: Opérateur >= - Référence C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846249"
---
# <a name="-operator-c-reference"></a>Opérateur >= (référence C#)

Le `=>` jeton est pris en charge sous deux formes : en tant [qu’opérateur lambda](#lambda-operator) et en tant que séparateur d’un nom de membre et la mise en œuvre du membre dans une [définition d’organe d’expression](#expression-body-definition).

## <a name="lambda-operator"></a>Opérateur lamdba

Dans [les expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) `=>` , l’opérateur lambda sépare les paramètres d’entrée sur le côté gauche du corps lambda sur le côté droit.

L’exemple suivant utilise la fonctionnalité [LINQ](../../programming-guide/concepts/linq/index.md) avec la syntaxe de méthode pour illustrer l’utilisation d’expressions lambda :

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

Les paramètres d’entrée d’une expression lambda sont fortement tapés au moment de la compilation. Lorsque le compilateur peut déduire les types de paramètres d’entrée, comme dans l’exemple précédent, vous pouvez omettre des déclarations de type. Si vous devez spécifier le type de paramètres d’entrée, vous devez le faire pour chaque paramètre, comme le montre l’exemple suivant :

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

L’exemple suivant montre comment définir une expression lambda sans paramètres d’entrée :

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

Pour plus d’informations, consultez [Expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Définition de corps d’expression

La syntaxe générale d’une définition de corps d’expression est la suivante :

```csharp
member => expression;
```

où `expression` est une expression valide. Le type de retour de `expression` doit être implicitement convertible en type de retour du membre. Si le type de `void` déclaration du membre est ou si le membre `set` est un `expression` constructeur, un finalisateur, ou un accessoir de propriété, doit être une [*expression de déclaration*](~/_csharplang/spec/statements.md#expression-statements), qui peut être de n’importe quel type.

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

Les définitions de corps d’expression pour les méthodes, les opérateurs, et les propriétés de lecture-seulement sont prises en charge commençant par C 6. Les définitions d’organisme d’expression pour les constructeurs, les finalisateurs et les accesseurs de propriété et d’indexeur sont prises en charge en commençant par C 7.0.

Pour plus d’informations, consultez [Membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

L’opérateur `=>` ne peut pas être surchargé.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations sur l’opérateur lambda, consultez la section expressions de [fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la spécification linguistique [C .](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)

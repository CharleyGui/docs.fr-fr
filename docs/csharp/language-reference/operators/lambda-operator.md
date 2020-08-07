---
title: Opérateur >= - Référence C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: b72b058c1709e7a643a70233cc3289d5d9165ca4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916803"
---
# <a name="-operator-c-reference"></a>Opérateur >= (référence C#)

Le `=>` jeton est pris en charge sous deux formes : comme [opérateur lambda](#lambda-operator) et comme séparateur d’un nom de membre et l’implémentation de membre dans une [définition de corps d’expression](#expression-body-definition).

## <a name="lambda-operator"></a>Opérateur lamdba

Dans les [expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), l’opérateur lambda `=>` sépare les paramètres d’entrée sur le côté gauche du corps lambda du côté droit.

L’exemple suivant utilise la fonctionnalité [LINQ](../../programming-guide/concepts/linq/index.md) avec la syntaxe de méthode pour illustrer l’utilisation d’expressions lambda :

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

Les paramètres d’entrée d’une expression lambda sont fortement typés au moment de la compilation. Lorsque le compilateur peut déduire les types de paramètres d’entrée, comme dans l’exemple précédent, vous pouvez omettre des déclarations de type. Si vous devez spécifier le type des paramètres d’entrée, vous devez le faire pour chaque paramètre, comme le montre l’exemple suivant :

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

L’exemple suivant montre comment définir une expression lambda sans paramètres d’entrée :

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

Pour plus d’informations, consultez [Expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Définition de corps d’expression

La syntaxe générale d’une définition de corps d’expression est la suivante :

```csharp
member => expression;
```

où `expression` est une expression valide. Le type de retour de `expression` doit être implicitement convertible en type de retour du membre. Si le type de retour du membre est `void` ou si le membre est un constructeur, un finaliseur ou un accesseur de propriété ou d’indexeur `set` , `expression` doit être une [*expression d’instruction*](~/_csharplang/spec/statements.md#expression-statements). Étant donné que le résultat de l’expression est ignoré, le type de retour de cette expression peut être n’importe quel type.

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

Les définitions de corps d’expression pour les méthodes, les opérateurs et les propriétés en lecture seule sont prises en charge à partir de C# 6. Les définitions de corps d’expression pour les constructeurs, les finaliseurs et les accesseurs de propriété et d’indexeur sont pris en charge à compter de C# 7,0.

Pour plus d’informations, consultez [Membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

L’opérateur `=>` ne peut pas être surchargé.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations sur l’opérateur lambda, consultez la section [expressions de fonction anonymes](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)

---
title: 'Opérateur ?: - Référence C#'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399517"
---
# <a name="-operator-c-reference"></a>Opérateur ?: (référence C#)

L’opérateur `?:`conditionnel , également connu sous le nom d’opérateur conditionnel ternaire, évalue une expression Boolean et `true` renvoie le résultat de l’une des deux expressions, selon que l’expression Boolean évalue ou `false`.

Voici la syntaxe de l'opérateur conditionnel :

```csharp
condition ? consequent : alternative
```

L'expression `condition` doit donner `true` ou `false`. Si `condition` prend la valeur `true`, l’expression `consequent` est évaluée et son résultat devient le résultat de l’opération. Si `condition` prend la valeur `false`, l’expression `alternative` est évaluée et son résultat devient le résultat de l’opération. Soit `consequent`, soit `alternative` est évaluée.

Il faut que `consequent` et `alternative` soient du même type ou bien qu’une conversion implicite existe d’un type à l’autre.

L’opérateur conditionnel est associatif à droite ; autrement dit, une expression de la forme :

```csharp
a ? b : c ? d : e
```

est évaluée comme étant

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> Vous pouvez utiliser l’appareil mnémonique suivant pour vous souvenir du mode d’évaluation de l’opérateur conditionnel :
>
> ```text
> is this condition true ? yes : no
> ```

L’exemple suivant illustre l’utilisation de l’opérateur conditionnel :

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Expression ref conditionnelle

Commençant par C 7.2, une variable [locale ou réadsible d’arbitre](../keywords/ref.md#ref-locals) peut être assignée [conditionnellement](../keywords/ref.md#ref-readonly-locals) avec l’expression conditionnelle de l’arbitre. Vous pouvez également utiliser l’expression conditionnelle de ref comme valeur [de retour de référence](../keywords/ref.md#reference-return-values) ou comme argument [ `ref` de méthode.](../keywords/ref.md#passing-an-argument-by-reference)

Voici la syntaxe de l'expression ref conditionnelle :

```csharp
condition ? ref consequent : ref alternative
```

Comme l’opérateur conditionnel d’origine, l’expression ref conditionnelle n’évalue qu’une des deux expressions : soit `consequent`, soit `alternative`.

Dans le cas de l’expression ref conditionnelle, `consequent` et `alternative` doivent être du même type.

L’exemple suivant illustre l’utilisation de l’expression ref conditionnelle :

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Opérateur conditionnel et instruction `if..else`

L’utilisation de l’opérateur conditionnel au lieu d’une déclaration [if-else](../keywords/if-else.md) peut entraîner un code plus concis dans les cas où vous avez besoin conditionnellement pour calculer une valeur. L’exemple suivant montre deux façons de classer un entier comme négatif ou non :

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur ne peut pas surcharger l’opérateur conditionnel.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Opérateur conditionnel](~/_csharplang/spec/expressions.md#conditional-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur l’expression de l’arbitre conditionnel, voir la [note de proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [if-else, instruction](../keywords/if-else.md)
- [Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)
- [?? Et?? - opérateurs](null-coalescing-operator.md)
- [ref, mot clé](../keywords/ref.md)

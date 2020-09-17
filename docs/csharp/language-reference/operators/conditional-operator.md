---
description: 'Opérateur ?: - Référence C#'
title: 'Opérateur ?: - Référence C#'
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: b6add045983619169bed0cd9f32eb27dba0a0338
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738877"
---
# <a name="-operator-c-reference"></a>Opérateur ?: (référence C#)

L’opérateur conditionnel `?:` , également appelé opérateur conditionnel ternaire, évalue une expression booléenne et retourne le résultat de l’une des deux expressions, selon que l’expression booléenne a pour valeur `true` ou `false` .

Voici la syntaxe de l'opérateur conditionnel :

```csharp
condition ? consequent : alternative
```

L'expression `condition` doit donner `true` ou `false`. Si `condition` prend la valeur `true`, l’expression `consequent` est évaluée et son résultat devient le résultat de l’opération. Si `condition` prend la valeur `false`, l’expression `alternative` est évaluée et son résultat devient le résultat de l’opération. Soit `consequent`, soit `alternative` est évaluée.

À compter de C# 9,0, les expressions conditionnelles sont de type cible. Autrement dit, si un type cible d’une expression conditionnelle est connu, les types de `consequent` et `alternative` doivent être implicitement convertibles en type cible, comme le montre l’exemple suivant :

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

Si le type cible d’une expression conditionnelle est inconnu (par exemple, lorsque vous utilisez le [`var`](../keywords/var.md) mot clé) ou en C# 8,0 et les versions antérieures, le type de `consequent` et `alternative` doit être identique ou il doit y avoir une conversion implicite d’un type à l’autre :

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

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

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Expression ref conditionnelle

À compter de C# 7,2, une variable locale Ref [locale](../keywords/ref.md#ref-locals) ou [ref ReadOnly](../keywords/ref.md#ref-readonly-locals) peut être assignée de manière conditionnelle avec une expression Ref conditionnelle. Vous pouvez également utiliser une expression Ref conditionnelle comme [valeur de retour de référence](../keywords/ref.md#reference-return-values) ou comme [ `ref` argument de méthode](../keywords/ref.md#passing-an-argument-by-reference).

La syntaxe d’une expression Ref conditionnelle est la suivante :

```csharp
condition ? ref consequent : ref alternative
```

À l’instar de l’opérateur conditionnel d’origine, une expression Ref conditionnelle évalue uniquement l’une des deux expressions : `consequent` ou `alternative` .

Dans le cas d’une expression Ref conditionnelle, le type de `consequent` et `alternative` doit être identique. Les expressions Ref conditionnelles ne sont pas de type cible.

L’exemple suivant illustre l’utilisation d’une expression Ref conditionnelle :

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Opérateur conditionnel et instruction `if..else`

L’utilisation de l’opérateur conditionnel au lieu d’une instruction [if-else](../keywords/if-else.md) peut entraîner un code plus concis dans les cas où vous avez besoin de calculer une valeur de manière conditionnelle. L’exemple suivant montre deux façons de classer un entier comme négatif ou non :

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur ne peut pas surcharger l’opérateur conditionnel.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Opérateur conditionnel](~/_csharplang/spec/expressions.md#conditional-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur les fonctionnalités ajoutées dans C# 7,2 et versions ultérieures, consultez les notes de proposition de fonctionnalités suivantes :

- [Expressions Ref conditionnelles (C# 7,2)](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [Expression conditionnelle typée cible (C# 9,0)](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [if-else, instruction](../keywords/if-else.md)
- [Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)
- [?? et ?? =, opérateurs](null-coalescing-operator.md)
- [ref, mot clé](../keywords/ref.md)

---
title: Opérateurs arithmétiques - Référence C#
description: Découvrez les opérateurs C# qui effectuent des opérations de multiplication, division, reste, addition et soustraction avec des types numériques.
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
- '%=_CSharpKeyword'
- '*=_CSharpKeyword'
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: 4ddd71e41ff70d4287f474cc91255a5aae51b132
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855242"
---
# <a name="arithmetic-operators-c-reference"></a>Opérateurs arithmétiques (référence C#)

Les opérateurs suivants effectuent des opérations arithmétiques avec des opérandes de types numériques :

- Opérateurs unaires [ `++` (incrémentation](#increment-operator-)), [ `--` (décrémentation)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators)et [ `-` (moins)](#unary-plus-and-minus-operators)
- Opérateurs binaires [ `*` (multiplication](#multiplication-operator-)), ( [ `/` Division)](#division-operator-), [ `%` (reste)](#remainder-operator-), [ `+` (addition)](#addition-operator-)et [ `-` (soustraction)](#subtraction-operator--)

Ces opérateurs sont pris en charge par tous les types numériques [intégraux](../builtin-types/integral-numeric-types.md) et [à virgule flottante](../builtin-types/floating-point-numeric-types.md) .

Dans le cas des types intégraux, ces opérateurs (à l’exception des `++` `--` opérateurs et) sont définis pour les `int` `uint` types,, `long` et `ulong` . Lorsque les opérandes sont d’autres types intégraux ( `sbyte` , `byte` ,, `short` `ushort` ou `char` ), leurs valeurs sont converties vers le `int` type, qui est également le type de résultat d’une opération. Quand les opérandes sont de types intégraux ou à virgule flottante différents, leurs valeurs sont converties dans le type conteneur le plus proche, si un tel type existe. Pour plus d’informations, consultez la section [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md). Les `++` `--` opérateurs et sont définis pour tous les types numériques intégraux et à virgule flottante, ainsi que le type [char](../builtin-types/char.md) .

## <a name="increment-operator-"></a>Opérateur d’incrémentation ++

L’opérateur d’incrémentation unaire `++` incrémente son opérande de 1. L’opérande doit être une variable, un accès [propriété](../../programming-guide/classes-and-structs/properties.md) ou un accès [indexeur](../../programming-guide/indexers/index.md).

L’opérateur d’incrémentation est pris en charge sous deux formes : l’opérateur d’incrémentation suffixé, `x++`, et l’opérateur d’incrémentation préfixé, `++x`.

### <a name="postfix-increment-operator"></a>Opérateur d'incrément suffixé

Le résultat de `x++` est la valeur de `x` *avant* l’opération, comme le montre l’exemple suivant :

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Opérateur d'incrémentation préfixé

Le résultat de `++x` est la valeur de `x` *après* l’opération, comme le montre l’exemple suivant :

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Opérateur de décrémentation --

L’opérateur de décrémentation unaire `--` décrémente son opérande de 1. L’opérande doit être une variable, un accès [propriété](../../programming-guide/classes-and-structs/properties.md) ou un accès [indexeur](../../programming-guide/indexers/index.md).

L’opérateur de décrémentation est pris en charge sous deux formes : l’opérateur de décrémentation suffixé, `x--`, et l’opérateur de décrémentation préfixé, `--x`.

### <a name="postfix-decrement-operator"></a>Opérateur de décrémentation suffixé

Le résultat de `x--` est la valeur de `x` *avant* l’opération, comme le montre l’exemple suivant :

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Opérateur de décrémentation préfixé

Le résultat de `--x` est la valeur de `x` *après* l’opération, comme le montre l’exemple suivant :

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Opérateurs plus et moins unaires

L’opérateur unaire `+` retourne la valeur de son opérande. L’opérateur unaire `-` calcule la négation numérique de son opérande.

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Le type [ULong](../builtin-types/integral-numeric-types.md) ne prend pas en charge l’opérateur unaire `-` .

## <a name="multiplication-operator-"></a>Opérateur de multiplication *

L’opérateur de multiplication `*` calcule le produit de ses opérandes :

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

L’opérateur unaire `*` est [l’opérateur d’indirection de pointeur](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Opérateur de division /

L’opérateur de division `/` divise son opérande de partie gauche par son opérande de partie droite.

### <a name="integer-division"></a>Division d'entier

Pour les opérandes des types entiers, le résultat de l’opérateur `/` est de type entier et égal au quotient de deux opérandes arrondis vers le zéro :

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

Pour obtenir le quotient de deux opérandes comme un nombre à virgule flottante, utilisez le type `float`, `double` ou `decimal` :

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Division à virgule flottante

Pour les types `float`, `double` et `decimal`, le résultat de l’opérateur `/` est le quotient de deux opérandes :

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

Si l’un des opérandes est `decimal`, un autre opérande ne peut être `float` ni `double`, car ni `float` ni `double` ne sont implicitement convertibles en `decimal`. Vous devez convertir explicitement l’opérande `float` ou `double` en type `decimal`. Pour plus d’informations sur les conversions entre les types numériques, consultez [conversions numériques intégrées](../builtin-types/numeric-conversions.md).

## <a name="remainder-operator-"></a>Opérateur de reste %

L’opérateur restant `%` calcule le reste après la division de son opérande de partie gauche par son opérande de partie droite.

### <a name="integer-remainder"></a>Reste entier

Pour les opérandes des types entiers, le résultat de `a % b` est la valeur produite par `a - (a / b) * b`. Le signe du reste non zéro est le même que celui de l’opérande de partie gauche, comme l’indique l’exemple suivant :

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

Utilisez la méthode <xref:System.Math.DivRem%2A?displayProperty=nameWithType> pour calculer à la fois la division entière et les résultats du reste.

### <a name="floating-point-remainder"></a>Reste à virgule flottante

En ce qui concerne les opérandes `float` et `double`, le résultat de `x % y` pour le `x` et le `y` finis est la valeur `z` afin que

- Le signe de `z`, s’il est différent de zéro, soit identique au signe de `x`.
- La valeur absolue de `z` soit la valeur produite par `|x| - n * |y|`, où `n` représente le plus grand entier possible inférieur ou égal à `|x| / |y|`, et où `|x|` et `|y|` sont les valeurs absolues de `x` et `y`, respectivement.

> [!NOTE]
> Cette méthode de calcul du reste est analogue à celle utilisée pour les opérandes entiers, mais différente de la spécification IEEE 754. Si vous avez besoin de l’opération de reste qui est conforme à la spécification IEEE 754, utilisez la <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> méthode.

Pour plus d’informations sur le comportement de l’opérateur `%` avec des opérandes non finis, consultez la section [Opérateur de reste](~/_csharplang/spec/expressions.md#remainder-operator) dans la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour les opérandes `decimal`, l’opérateur de reste `%` équivaut à l’[opérateur de reste](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) de type <xref:System.Decimal?displayProperty=nameWithType>.

L’exemple suivant illustre le comportement de l’opérateur de reste pour les opérandes à virgule flottante :

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Opérateur d’addition +

L’opérateur d’addition `+` calcule la somme de ses opérandes :

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

Vous pouvez également utiliser l' `+` opérateur pour la concaténation de chaînes et la combinaison de délégués. Pour plus d’informations, consultez l’article [ `+` `+=` opérateurs et](addition-operator.md) .

## <a name="subtraction-operator--"></a>Opérateur de soustraction -

L’opérateur de soustraction `-` soustrait son opérande de partie droite de son opérande de partie gauche :

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

Vous pouvez également utiliser l' `-` opérateur pour la suppression d’un délégué. Pour plus d’informations, consultez l’article [ `-` `-=` opérateurs et](subtraction-operator.md) .

## <a name="compound-assignment"></a>Assignation composée

Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire

```csharp
x op= y
```

équivaut à :

```csharp
x = x op y
```

sauf que `x` n’est évalué qu’une seule fois.

L’exemple suivant illustre l’utilisation de l’assignation composée avec des opérateurs arithmétiques :

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

En raison des [promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions), le résultat de l’opération `op` risque de ne pas être implicitement convertible en type `T` de `x`. Dans ce cas, si `op` est un opérateur prédéfini et que le résultat de l’opération est explicitement convertible en type `T` de `x`, une expression d’assignation composée de la forme `x op= y` équivaut à `x = (T)(x op y)`, sauf que `x` n’est évalué qu’une seule fois. L’exemple suivant illustre ce comportement :

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Vous pouvez également utiliser `+=` les `-=` opérateurs et pour vous abonner et vous désabonner d’un [événement](../keywords/event.md), respectivement. Pour plus d’informations, consultez [Comment s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-precedence-and-associativity"></a>Priorité des opérateurs et associativité

La liste suivante présente les opérateurs arithmétiques de la priorité la plus élevée à la plus basse :

- Opérateurs suffixés d’incrémentation `x++` et de décrémentation `x--`
- Opérateurs préfixés d’incrémentation `++x` et de décrémentation `--x` et opérateurs unaires `+` et `-`
- Opérateurs multiplicatifs `*`, `/` et `%`
- Opérateurs additifs `+` et `-`

Les opérateurs arithmétiques binaires sont associatifs sur leur gauche. Autrement dit, les opérateurs de même niveau de priorité sont évalués de gauche à droite.

Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la priorité et l’associativité de l’opérateur.

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez la section [priorité d’opérateur](index.md#operator-precedence) de l’article [opérateurs c#](index.md) .

## <a name="arithmetic-overflow-and-division-by-zero"></a>Débordement arithmétique et division par zéro

Quand le résultat d’une opération arithmétique n’est pas compris dans la plage de valeurs finies possibles du type numérique impliqué, le comportement d’un opérateur arithmétique varie selon le type de ses opérandes.

### <a name="integer-arithmetic-overflow"></a>Débordement arithmétique entier

La division d'un entier par zéro lève toujours une exception <xref:System.DivideByZeroException>.

En cas de débordement arithmétique entier, un contexte de vérification de débordement, qui peut être [vérifié ou non vérifié](../keywords/checked-and-unchecked.md), contrôle le comportement qui en résulte :

- Dans un contexte vérifié, si le débordement se produit dans une expression constante, une erreur de compilation se produit. Sinon, un <xref:System.OverflowException> est levé quand l’opération est effectuée au moment de l’exécution.
- Dans un contexte non vérifié, le résultat est tronqué en supprimant tous les bits de poids fort qui ne tiennent pas dans le type destinataire.

Avec les instructions [vérifiées et non vérifiées](../keywords/checked-and-unchecked.md), vous pouvez utiliser les opérateurs `checked` et `unchecked` pour contrôler le contexte de vérification de débordement, dans lequel une expression est évaluée :

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

Par défaut, les opérations arithmétiques se produisent dans un contexte *unchecked*.

### <a name="floating-point-arithmetic-overflow"></a>Débordement arithmétique à virgule flottante

Les opérations arithmétiques avec les types `float` et `double` ne lèvent jamais d’exceptions. Le résultat des opérations arithmétiques avec ces types peut être une des valeurs spéciales qui représentent l’infini et non un nombre :

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

Pour les opérandes du type `decimal`, le débordement arithmétique lève toujours un <xref:System.OverflowException> et la division par zéro lève toujours un <xref:System.DivideByZeroException>.

## <a name="round-off-errors"></a>Erreurs d’arrondi

En raison des limitations générales de la représentation à virgule flottante des nombres réels et de l’arithmétique à virgule flottante, des erreurs d’arrondi peuvent se produire dans les calculs avec des types à virgule flottante. Autrement dit, le résultat d’une expression peut différer du résultat mathématique attendu. L’exemple suivant illustre plusieurs cas de ce genre :

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

Pour plus d’informations, consultez la section Notes sur les pages de référence System. [double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)ou [System. Decimal](/dotnet/api/system.decimal#remarks) .

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les `++` opérateurs arithmétiques unaires (,, `--` `+` et `-` ) et binaires ( `*` ,,, `/` `%` `+` et `-` ). Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé. Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Opérateurs suffixés d’incrémentation et de décrémentation](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Opérateurs préfixés d’incrémentation et de décrémentation](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Opérateur plus unaire](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Opérateur moins unaire](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Opérateur de multiplication](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Opérateur de division](~/_csharplang/spec/expressions.md#division-operator)
- [Remainder (opérateur)](~/_csharplang/spec/expressions.md#remainder-operator)
- [Opérateur d’addition](~/_csharplang/spec/expressions.md#addition-operator)
- [Opérateur de soustraction](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Assignation composée](~/_csharplang/spec/expressions.md#compound-assignment)
- [Opérateurs vérifiés et non vérifiés](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [Valeurs numériques dans .NET](../../../standard/numerics.md)

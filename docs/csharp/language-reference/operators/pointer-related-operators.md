---
title: Opérateurs associés au pointeur - Référence C#
description: Découvrez les opérateurs C# que vous pouvez utiliser avec les pointeurs.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 6196cb52cb1b42b3354bc7f8836a171397d0af1e
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758101"
---
# <a name="pointer-related-operators-c-reference"></a>Opérateurs associés au pointeur (référence C#)

Vous pouvez utiliser les opérateurs suivants avec les pointeurs :

- Opérateur unaire [`&` (address-of)](#address-of-operator-) : pour obtenir l’adresse d’une variable
- Opérateur unaire [`*` (indirection du pointeur)](#pointer-indirection-operator-) : pour obtenir la variable pointée par un pointeur
- Opérateurs [`->` (accès aux membres)](#pointer-member-access-operator--) et [`[]` (accès aux éléments)](#pointer-element-access-operator-)
- Opérateurs arithmétiques [`+`, `-`, `++` et `--`](#pointer-arithmetic-operators)
- Opérateurs de comparaison [`==`, `!=`, `<`, `>`, `<=` et `>=`](#pointer-comparison-operators)

Pour plus d’informations sur les types de pointeurs, consultez [Types pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Toutes les opérations impliquant des pointeurs nécessitent un contexte [unsafe](../keywords/unsafe.md). Le code qui contient des blocs unsafe doit être compilé avec l’option de compilateur [`-unsafe`](../compiler-options/unsafe-compiler-option.md).

## <a name="address-of-operator-amp"></a>Opérateur address-of &amp;

L’opérateur unaire `&` retourne l’adresse de son opérande :

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

L’opérande de l’opérateur `&` doit être une variable fixe. Les variables *fixes* se trouvent dans des emplacements de stockage qui ne sont pas affectés par le [récupérateur de mémoire](../../../standard/garbage-collection/index.md). Dans l’exemple précédent, la variable locale `number` est une variable fixe, car elle se trouve dans la pile. Les variables qui se trouvent dans des emplacements de stockage pouvant être affectés par le récupérateur de mémoire (par exemple, en étant déplacés) sont appelées variables *déplaçables*. Les champs d’objet et les éléments de tableau sont des exemples de variables déplaçables. Vous pouvez obtenir l’adresse d’une variable déplaçable en la fixant (ou en l’épinglant) à l’aide de l’instruction [fixed](../keywords/fixed-statement.md). L’adresse obtenue est valide uniquement pendant la durée du bloc d’instructions `fixed`. L’exemple suivant montre comment utiliser l’instruction `fixed` et l’opérateur `&` :

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

Vous ne pouvez pas obtenir l’adresse d’une constante ou d’une valeur.

Pour plus d’informations sur les variables fixes et déplaçables, consultez la section [Variables fixes et déplaçables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

L’opérateur binaire `&` calcule la [logique AND](boolean-logical-operators.md#logical-and-operator-) de ses opérandes booléens, ou la [logique AND au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes de type intégral.

## <a name="pointer-indirection-operator-"></a>Opérateur d’indirection de pointeur *

L’opérateur unaire d’indirection de pointeur `*` permet d’obtenir la variable vers laquelle pointe son opérande. Il est également appelé « opérateur de déréférence ». L’opérande de l’opérateur `*` doit être un type de pointeur.

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

Vous ne pouvez pas appliquer l’opérateur `*` à une expression de type `void*`.

L’opérateur binaire `*` calcule le [produit](arithmetic-operators.md#multiplication-operator-) de ses opérandes numériques.

## <a name="pointer-member-access-operator--"></a>Opérateur d’accès aux membres de pointeur ->

L’opérateur `->` associe l’[indirection de pointeur](#pointer-indirection-operator-) à l’[accès aux membres](member-access-operators.md#member-access-operator-). C’est-à-dire que si `x` est un pointeur de type `T*` et `y` un membre accessible de `T`, une expression au format

```csharp
x->y
```

est équivalent à

```csharp
(*x).y
```

L’exemple suivant illustre l’utilisation de l’opérateur `->` :

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

Vous ne pouvez pas appliquer l’opérateur `->` à une expression de type `void*`.

## <a name="pointer-element-access-operator-"></a>Opérateur d’accès aux éléments de pointeur []

Pour une expression `p` d’un type pointeur, l’accès à un élément de pointeur au format `p[n]` est évalué comme `*(p + n)`, où `n` doit être d’un type implicitement convertible en `int`, `uint`, `long` ou `ulong`. Pour plus d’informations sur le comportement de l’opérateur `+` avec les pointeurs, consultez la section [Addition ou soustraction d’une valeur intégrale dans un pointeur](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer).

L’exemple suivant montre comment accéder à des éléments tableau avec un pointeur et l’opérateur `[]` :

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

L’exemple utilise l’[opérateur `stackalloc`](../keywords/stackalloc.md) pour allouer un bloc de mémoire à la pile.

> [!NOTE]
> L’opérateur d’accès aux éléments de pointeur ne recherche pas les erreurs de dépassement des limites.

Vous ne pouvez pas utiliser `[]` pour l’accès aux éléments de pointeur avec une expression de type `void*`.

Vous pouvez également utiliser l’opérateur `[]` pour l’[accès aux éléments de tableau ou à l’indexeur](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Opérateurs arithmétiques de pointeur

Vous pouvez effectuer les opérations arithmétiques suivantes avec des pointeurs :

- Ajouter ou soustraire une valeur intégrale dans un pointeur
- Soustraire deux pointeurs
- Incrémenter ou décrémenter un pointeur

Vous ne pouvez pas effectuer ces opérations avec des pointeurs de type `void*`.

Pour plus d’informations sur les opérations arithmétiques prises en charge avec les types numériques, consultez [Opérateurs arithmétiques](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Ajout ou soustraction d’une valeur intégrale dans un pointeur

Pour un pointeur `p` de type `T*` et une expression `n` d’un type implicitement convertible en `int`, `uint`, `long` ou `ulong`, l’addition et la soustraction sont définies de la façon suivante :

- Les expressions `p + n` et `n + p` produisent un pointeur de type `T*` qui est obtenu en ajoutant `n * sizeof(T)` à l’adresse fournie par `p`.
- L’expression `p - n` produit un pointeur de type `T*` qui est obtenu en soustrayant `n * sizeof(T)` de l’adresse fournie par `p`.

L’[opérateur `sizeof`](../keywords/sizeof.md) permet d’obtenir la taille d’un type en octets.

L’exemple suivant illustre l’utilisation de l’opérateur `+` avec un pointeur :

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Soustraction de pointeur

Pour deux pointeurs `p1` et `p2` de type `T*`, l’expression `p1 - p2` produit la différence entre les adresses fournies par `p1` et `p2`, divisée par `sizeof(T)`. Le type du résultat est `long`. C’est -à-dire que `p1 - p2`est calculé en tant que `((long)(p1) - (long)(p2)) / sizeof(T)`.

L’exemple suivant montre la soustraction d’un pointeur :

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Incrémenter et décrémenter des pointeurs

L’opérateur d’incrémentation `++` [ajoute](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 à son opérande de pointeur. L’opérateur de décrémentation `--` [soustrait](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 de son opérande de pointeur.

Les deux opérateurs sont pris en charge sous deux formes : suffixée (`p++` et `p--`) et préfixée (`++p` et `--p`). Le résultat de `p++` et `p--` correspond à la valeur de `p` *avant* l’opération. Le résultat de `++p` et `--p` correspond à la valeur de `p` *après* l’opération.

L’exemple suivant montre le comportement des opérateurs d’incrémentation suffixés et préfixés :

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Opérateurs de comparaison de pointeur

Vous pouvez utiliser les opérateurs `==`, `!=`, `<`, `>`, `<=` et `>=` pour comparer des opérandes de tout type de pointeur, y compris `void*`. Ces opérateurs comparent les adresses fournies par les deux opérandes comme s’il s’agissait d’entiers non signés.

Pour plus d’informations sur le comportement de ces opérateurs pour les opérandes d’autres types, consultez les articles [Opérateurs d’égalité](equality-operators.md) et [Opérateurs de comparaison](comparison-operators.md).

## <a name="operator-precedence"></a>Précédence des opérateurs

La liste suivante présente les opérateurs relatifs aux pointeurs par ordre de précédence, de la plus élevée à la plus basse :

- Opérateurs suffixés d’incrémentation`x++` et de décrémentation `x--`, ainsi que les opérateurs `->` et `[]`
- Opérateurs préfixés d’incrémentation`++x` et de décrémentation `--x`, ainsi que les opérateurs `&` et `*`
- Opérateurs additifs `+` et `-`
- Opérateurs de comparaison `<`, `>`, `<=` et `>=`
- Opérateurs d’égalité `==` et `!=`

Utilisez des parenthèses (`()`) pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs.

Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](index.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur ne peut pas surcharger les opérateurs de pointeur `&`, `*`, `->` et `[]`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Variables fixes et déplaçables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [address-of, opérateur](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [Indirection de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [Accès aux membres de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [Accès aux éléments de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [Arithmétique sur les pointeurs](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [Incrémentation et décrémentation des pointeurs](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [Comparaison de pointeurs](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Opérateurs C#](index.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Mot clé `unsafe`](../keywords/unsafe.md)
- [Mot clé `fixed`](../keywords/fixed-statement.md)
- [`stackalloc`, opérateur](../keywords/stackalloc.md)
- [`sizeof`, opérateur](../keywords/sizeof.md)

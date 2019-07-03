---
title: Opérateur >= - Référence C#
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: ef9c9bab5c1cebb06edf934254507180e2197349
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306565"
---
# <a name="-operator-c-reference"></a>Opérateur >= (référence C#)

L’opérateur d’assignation `=` assigne la valeur de son opérande de droite à une variable, une [propriété](../../programming-guide/classes-and-structs/properties.md) ou un élément [d’indexeur](../../../csharp/programming-guide/indexers/index.md) donné par son opérande de gauche. Le résultat d’une expression d’assignation est la valeur assignée à l’opérande de gauche. L’opérande de droite doit être du même type que l’opérande de gauche, ou implicitement convertible vers le type de l’opérande de gauche.

L’opérateur d’assignation est associatif à droite ; autrement dit, une expression de la forme :

```csharp
a = b = c
```

est évaluée comme étant

```csharp
a = (b = c)
```

L’exemple suivant illustre l’utilisation de l’opérateur d’assignation avec une variable locale, une propriété et un élément d’indexeur comme opérande de gauche :

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>Opérateur d'assignation ref

À partir de C# 7.3, vous pouvez utiliser l’opérateur d’assignation ref `= ref` pour réaffecter une variable [locale ref](../keywords/ref.md#ref-locals) ou une variable [locale ref readonly](../keywords/ref.md#ref-readonly-locals). L’exemple suivant illustre l’utilisation de l’opérateur d’assignation ref :

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

Dans le cas de l’opérateur d’assignation ref, les deux opérandes doivent être du même type.

Pour plus d’informations, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="compound-assignment"></a>Assignation composée

Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire

```csharp
x op= y
```

est équivalent à

```csharp
x = x op y
```

sauf que `x` n’est évalué qu’une seule fois.

L’assignation composée est prise en charge par les opérateurs [arithmétiques](arithmetic-operators.md#compound-assignment), [logiques booléens](boolean-logical-operators.md#compound-assignment) et [logiques au niveau du bit et du décalage](bitwise-and-shift-operators.md#compound-assignment).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur ne peut pas surcharger l’opérateur d’assignation. Toutefois, il peut définir une conversion implicite vers un autre type. Ainsi, la valeur d’un type défini par l’utilisateur peut être assignée à une variable, une propriété ou un élément d’indexeur d’un autre type. Pour plus d'informations, voir l’article [implicit, mot clé](../keywords/implicit.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Opérateurs d’assignation](~/_csharplang/spec/expressions.md#assignment-operators) de la [spécification du langage C#](../language-specification/index.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [ref, mot clé](../keywords/ref.md)

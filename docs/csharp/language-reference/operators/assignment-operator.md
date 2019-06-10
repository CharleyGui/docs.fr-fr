---
title: =, opérateur - Référence C#
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 85182acb84ea79cb00a9edb315c3954f440305f4
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758352"
---
# <a name="-operator-c-reference"></a>=, opérateur (référence C#)

L’opérateur d’assignation `=` assigne la valeur de son opérande de droite à une variable, une [propriété](../../programming-guide/classes-and-structs/properties.md) ou un élément [d’indexeur](../../../csharp/programming-guide/indexers/index.md) donné par son opérande de gauche. Le résultat d’une expression d’assignation est la valeur assignée à l’opérande de gauche. L’opérande de droite doit être du même type que l’opérande de gauche, ou implicitement convertible vers le type de l’opérande de gauche.

L’opérateur d’assignation est associatif à droite ; autrement dit, une expression de la forme :

```csharp
a = b = c
```

est évaluée comme étant

```csharp
a = (b = c)
```

L’exemple suivant illustre l’utilisation de l’opérateur d’assignation pour assigner des valeurs à une variable locale, une propriété et un élément d’indexeur :

[!code-csharp-interactive[assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a>Opérateur d'assignation ref

À partir de C# 7.3, vous pouvez utiliser l’opérateur d’assignation ref `= ref` pour réaffecter une variable [locale ref](../keywords/ref.md#ref-locals) ou une variable [locale ref readonly](../keywords/ref.md#ref-readonly-locals). L’exemple suivant illustre l’utilisation de l’opérateur d’assignation ref :

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

Dans le cas de l’opérateur d’assignation ref, l’opérande de gauche et l’opérande de droite doivent être du même type.

Pour plus d’informations, voir la [proposition de fonctionnalité](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur ne peut pas surcharger l’opérateur d’assignation. Toutefois, il peut définir une conversion implicite vers un autre type. Ainsi, la valeur d’un type défini par l’utilisateur peut être assignée à une variable, une propriété ou un élément d’indexeur d’un autre type. Pour plus d'informations, voir l’article [implicit, mot clé](../keywords/implicit.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Assignation simple](~/_csharplang/spec/expressions.md#simple-assignment) de la [spécification du langage C#](../language-specification/index.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Opérateurs C#](index.md)
- [ref, mot clé](../keywords/ref.md)

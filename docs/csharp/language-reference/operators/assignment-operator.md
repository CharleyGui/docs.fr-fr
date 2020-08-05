---
title: Opérateurs d’assignation-référence C#
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 7843c15f15debeea7cb3627b3c7576579f0169fb
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555459"
---
# <a name="assignment-operators-c-reference"></a>Opérateurs d’assignation (référence C#)

L’opérateur d’assignation `=` assigne la valeur de son opérande de droite à une variable, une [propriété](../../programming-guide/classes-and-structs/properties.md) ou un élément [d’indexeur](../../programming-guide/indexers/index.md) donné par son opérande de gauche. Le résultat d’une expression d’assignation est la valeur assignée à l’opérande de gauche. L’opérande de droite doit être du même type que l’opérande de gauche, ou implicitement convertible vers le type de l’opérande de gauche.

L’opérateur `=` d’assignation est associatif à droite, autrement dit, une expression de la forme

```csharp
a = b = c
```

est évaluée comme étant

```csharp
a = (b = c)
```

L’exemple suivant illustre l’utilisation de l’opérateur d’assignation avec une variable locale, une propriété et un élément d’indexeur comme opérande de gauche :

[!code-csharp-interactive[simple assignment](snippets/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>Opérateur d'assignation ref

À partir de C# 7.3, vous pouvez utiliser l’opérateur d’assignation ref `= ref` pour réaffecter une variable [locale ref](../keywords/ref.md#ref-locals) ou une variable [locale ref readonly](../keywords/ref.md#ref-readonly-locals). L’exemple suivant illustre l’utilisation de l’opérateur d’assignation ref :

[!code-csharp[ref assignment operator](snippets/AssignmentOperator.cs#RefAssignment)]

Dans le cas de l’opérateur d’assignation de référence, les deux opérandes doivent être du même type.

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

L’assignation composée est prise en charge par les opérateurs [arithmétiques](arithmetic-operators.md#compound-assignment), [logiques booléens](boolean-logical-operators.md#compound-assignment) et [logiques au niveau du bit et du décalage](bitwise-and-shift-operators.md#compound-assignment).

## <a name="null-coalescing-assignment"></a>Assignation de fusion Null

À compter de C# 8,0, vous pouvez utiliser l’opérateur d’assignation de fusion Null `??=` pour assigner la valeur de son opérande droit à son opérande de gauche uniquement si l’opérande de gauche prend la valeur `null` . Pour plus d’informations, consultez [les = l’article Operators](null-coalescing-operator.md) .

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur ne peut pas [surcharger](operator-overloading.md) l’opérateur d’assignation. Toutefois, il peut définir une conversion implicite vers un autre type. Ainsi, la valeur d’un type défini par l’utilisateur peut être assignée à une variable, une propriété ou un élément d’indexeur d’un autre type. Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).

Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée. Toutefois, si un type défini par l’utilisateur surcharge un opérateur binaire `op` , l' `op=` opérateur, s’il existe, est également implicitement surchargé.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Opérateurs d’assignation](~/_csharplang/spec/expressions.md#assignment-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur l’opérateur d’assignation de référence `= ref` , consultez la [Remarque relative](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)à la proposition de fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [ref, mot clé](../keywords/ref.md)

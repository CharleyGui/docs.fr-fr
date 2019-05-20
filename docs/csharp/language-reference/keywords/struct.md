---
title: struct - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 5317ea403575dca7ed64a5784fa9c993fa8d2f64
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633842"
---
# <a name="struct-c-reference"></a>struct (Référence C#)

Un type `struct` est un type valeur utilisé pour encapsuler de petits groupes de variables liées, par exemple les coordonnées d'un rectangle ou les caractéristiques d'un élément dans un inventaire. L'exemple suivant illustre une déclaration struct simple :

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>Remarques

Les structs peuvent également contenir des [constructeurs](../../programming-guide/classes-and-structs/constructors.md), des [constantes](../../programming-guide/classes-and-structs/constants.md), des [champs](../../programming-guide/classes-and-structs/fields.md), des [méthodes](../../programming-guide/classes-and-structs/methods.md), des [propriétés](../../programming-guide/classes-and-structs/properties.md), des [indexeurs](../../programming-guide/indexers/index.md), des [opérateurs](../../programming-guide/statements-expressions-operators/operators.md), des [événements](../../programming-guide/events/index.md) et des [types imbriqués](../../programming-guide/classes-and-structs/nested-types.md). Toutefois, si plusieurs membres sont nécessaires, il est conseillé de plutôt utiliser une classe.

Pour obtenir des exemples, consultez [Utilisation de structs](../../programming-guide/classes-and-structs/using-structs.md).

Les structs peuvent implémenter une interface, mais ne peuvent pas hériter d'un autre struct. C'est pourquoi, les membres struct ne peuvent pas être déclarés en tant que `protected`.

Pour plus d’informations, consultez [Structs](../../programming-guide/classes-and-structs/structs.md).

## <a name="examples"></a>Exemples

Pour obtenir des exemples et des informations supplémentaires, consultez [Utilisation de structs](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour obtenir des exemples, consultez [Utilisation de structs](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Tableau des valeurs par défaut](default-values-table.md)
- [Tableau des types intégrés](built-in-types-table.md)
- [Types](types.md)
- [Types valeur](value-types.md)
- [class](class.md)
- [interface](interface.md)
- [Classes et structs](../../programming-guide/classes-and-structs/index.md)

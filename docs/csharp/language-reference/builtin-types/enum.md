---
title: Types énumération-référence C#
description: En savoir plus sur les types énumération C# qui représentent un choix ou une combinaison de choix
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: a21bdf63247dc5fec95922de017e1d3502e08565
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599432"
---
# <a name="enumeration-types-c-reference"></a>Types énumération (référence C#)

Un type d' *énumération* (ou un *type enum*) est un [type valeur](value-types.md) défini par un ensemble de constantes nommées du type [numérique intégral](integral-numeric-types.md) sous-jacent. Pour définir un type d’énumération, utilisez le `enum` mot clé et spécifiez les noms des *membres enum*:

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Par défaut, les valeurs constantes associées des membres enum sont de type `int` ; elles commencent par zéro et augmentent d’une unité après l’ordre du texte de définition. Vous pouvez spécifier explicitement n’importe quel autre type [numérique intégral](integral-numeric-types.md) en tant que type sous-jacent d’un type énumération. Vous pouvez également spécifier explicitement les valeurs de constante associées, comme le montre l’exemple suivant :

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

Vous ne pouvez pas définir une méthode à l’intérieur de la définition d’un type d’énumération. Pour ajouter des fonctionnalités à un type énumération, créez une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).

La valeur par défaut d’un type énumération `E` est la valeur produite par expression `(E)0` , même si zéro n’a pas le membre enum correspondant.

Vous utilisez un type d’énumération pour représenter un choix à partir d’un ensemble de valeurs s’excluant mutuellement ou d’une combinaison de choix. Pour représenter une combinaison de choix, définissez un type d’énumération en tant qu’indicateurs binaires.

## <a name="enumeration-types-as-bit-flags"></a>Types énumération comme indicateurs binaires

Si vous souhaitez qu’un type énumération représente une combinaison de choix, définissez des membres enum pour ces choix de manière à ce qu’un choix individuel soit un champ de bits. Autrement dit, les valeurs associées à ces membres enum doivent être les puissances de deux. Ensuite, vous pouvez utiliser les [opérateurs logiques au niveau du bit `|` `&` ou](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) combiner des choix ou croiser des combinaisons de choix, respectivement. Pour indiquer qu’un type énumération déclare des champs de bits, appliquez l’attribut [Flags](xref:System.FlagsAttribute) à celui-ci. Comme le montre l’exemple suivant, vous pouvez également inclure des combinaisons typiques dans la définition d’un type énumération.

[!code-csharp[enum flags](snippets/shared/EnumType.cs#Flags)]

Pour obtenir plus d’informations et des exemples, consultez la <xref:System.FlagsAttribute?displayProperty=nameWithType> page de référence de l’API et la section [membres non exclusifs et l’attribut flags](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) de la <xref:System.Enum?displayProperty=nameWithType> page de référence des API.

## <a name="the-systemenum-type-and-enum-constraint"></a>Le type System. Enum et la contrainte enum

Le <xref:System.Enum?displayProperty=nameWithType> type est la classe de base abstraite de tous les types énumération. Il fournit un certain nombre de méthodes pour obtenir des informations sur un type d’énumération et ses valeurs. Pour plus d’informations et d’exemples, consultez la <xref:System.Enum?displayProperty=nameWithType> page de référence des API.

À compter de C# 7,3, vous pouvez utiliser `System.Enum` dans une contrainte de classe de base (appelée [contrainte enum](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) pour spécifier qu’un paramètre de type est un type énumération. Tout type énumération satisfait également `struct` à la contrainte, qui est utilisée pour spécifier qu’un paramètre de type est un type valeur qui n’autorise pas les valeurs NULL.

## <a name="conversions"></a>Conversions

Pour tout type énumération, il existe des conversions explicites entre le type énumération et son type intégral sous-jacent. Si vous [effectuez un cast](../operators/type-testing-and-cast.md#cast-expression) d’une valeur enum en son type sous-jacent, le résultat est la valeur intégrale associée d’un membre Enum.

[!code-csharp[enum conversions](snippets/shared/EnumType.cs#Conversions)]

Utilisez la <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> méthode pour déterminer si un type énumération contient un membre enum avec la certaine valeur associée.

Pour tout type énumération, il existe des conversions [boxing et unboxing](../../programming-guide/types/boxing-and-unboxing.md) vers et à partir du <xref:System.Enum?displayProperty=nameWithType> type, respectivement.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Énumérations](~/_csharplang/spec/enums.md)
- [Valeurs et opérations des énumérations](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Opérateurs logiques d’énumération](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Opérateurs de comparaison d’énumération](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Conversions d’énumération explicites](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Conversions d’énumération implicites](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Chaînes de format d’énumération](../../../standard/base-types/enumeration-format-strings.md)
- [Directives de conception-conception enum](../../../standard/design-guidelines/enum.md)
- [Directives de conception-enum Naming conventions](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [Instruction switch](../keywords/switch.md)

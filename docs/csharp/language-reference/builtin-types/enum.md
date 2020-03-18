---
title: Types d’énumération - Référence C
description: Renseignez-vous sur les types d’énumération CMD qui représentent un choix ou une combinaison de choix
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
ms.openlocfilehash: ab5eb1679f846bf0e25d90a4d0e0a71f0bdb0096
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847705"
---
# <a name="enumeration-types-c-reference"></a>Types d’énumération (référence C)

Un *type d’énumération* (ou *type enum*) est un type de [valeur](value-types.md) défini par un ensemble de constantes nommées du type [numérique intégral](integral-numeric-types.md) sous-jacent. Pour définir un type d’énumération, utilisez le `enum` mot clé et spécifiez les noms des membres *enum*:

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Par défaut, les valeurs constantes associées `int`des membres enum sont de type ; ils commencent par zéro et augmentent d’un à la suite de l’ordre de texte de définition. Vous pouvez spécifier explicitement tout autre type [numérique intégral](integral-numeric-types.md) comme type sous-jacent d’un type d’énumération. Vous pouvez également spécifier explicitement les valeurs constantes associées, comme le montre l’exemple suivant :

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

Vous ne pouvez pas définir une méthode à l’intérieur de la définition d’un type d’énumération. Pour ajouter des fonctionnalités à un type d’énumération, créez une [méthode d’extension.](../../programming-guide/classes-and-structs/extension-methods.md)

La valeur par défaut d’un type `E` d’énumération est la valeur produite par l’expression `(E)0`, même si zéro n’a pas le membre enum correspondant.

Vous utilisez un type d’énumération pour représenter un choix à partir d’un ensemble de valeurs mutuellement exclusives ou d’une combinaison de choix. Pour représenter une combinaison de choix, définissez un type d’énumération comme des drapeaux bit.

## <a name="enumeration-types-as-bit-flags"></a>Types énumération comme indicateurs binaires

Si vous voulez un type d’énumération pour représenter une combinaison de choix, définissez les membres enum pour ces choix de telle sorte qu’un choix individuel est un peu de champ. Autrement dit, les valeurs associées de ces membres enum devraient être les pouvoirs de deux. Ensuite, vous pouvez utiliser [les `|` `&` opérateurs logiques bitwise ou](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) pour combiner des choix ou de croiser des combinaisons de choix, respectivement. Pour indiquer qu’un type d’énumération déclare les champs bits, appliquez l’attribut [drapeaux](xref:System.FlagsAttribute) à elle. Comme le montre l’exemple suivant, vous pouvez également inclure quelques combinaisons typiques dans la définition d’un type d’énumération.

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

Pour plus d’informations <xref:System.FlagsAttribute?displayProperty=nameWithType> et d’exemples, consultez la page de référence <xref:System.Enum?displayProperty=nameWithType> de l’API et les membres non exclusifs et la section [d’attributs Drapeaux](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) de la page de référence API.

## <a name="the-systemenum-type-and-enum-constraint"></a>Le type System.Enum et la contrainte enum

Le <xref:System.Enum?displayProperty=nameWithType> type est la classe de base abstraite de tous les types d’énumération. Il fournit un certain nombre de méthodes pour obtenir des informations sur un type de recensement et ses valeurs. Pour plus d’informations <xref:System.Enum?displayProperty=nameWithType> et d’exemples, consultez la page de référence de l’API.

En commençant par le C 7.3, vous pouvez utiliser `System.Enum` dans une contrainte de classe de base (qui est connue sous le nom de contrainte [d’enum](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) pour spécifier qu’un paramètre de type est un type d’énumération.

## <a name="conversions"></a>Conversions

Pour tout type d’énumération, il existe des conversions explicites entre le type d’énumération et son type intégral sous-jacent. Si vous [lancez](../operators/type-testing-and-cast.md#cast-operator-) une valeur enum à son type sous-jacent, le résultat est la valeur intégrale associée d’un membre enum.

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

Utilisez <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> la méthode pour déterminer si un type d’énumération contient un membre enum avec la valeur associée certaine.

Pour tout type d’énumération, il existe des conversions <xref:System.Enum?displayProperty=nameWithType> de boxe et de [déballage](../../programming-guide/types/boxing-and-unboxing.md) pour et depuis le type, respectivement.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Enums](~/_csharplang/spec/enums.md)
- [Valeurs et opérations des énumérations](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Opérateurs logiques d’énumération](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Opérateurs de comparaison de recensement](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Conversions explicites de recensement](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Conversions implicites de recensement](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Chaînes de format d'énumération](../../../standard/base-types/enumeration-format-strings.md)
- [Lignes directrices de conception - Conception Enum](../../../standard/design-guidelines/enum.md)
- [Lignes directrices de conception - Enum nommant des conventions](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [instruction switch](../keywords/switch.md)

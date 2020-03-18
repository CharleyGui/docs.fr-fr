---
title: Types numériques intégraux - Référence C#
description: Découvrez la plage, la taille de stockage et les différentes utilisations associés à chacun des types numériques intégraux.
ms.date: 10/22/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 394a809a9a2f45f4aee652d0eca892f62f0f2e54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093199"
---
# <a name="integral-numeric-types--c-reference"></a>Types numériques intégraux (référence C#)

Les *types numériques intégrals* représentent les nombres d’intégraires. Tous les types numériques intégral sont [des types de valeur](value-types.md). Ils sont également [des types simples](value-types.md#built-in-value-types) et peuvent être parascés avec des [littérals](#integer-literals). Tous les types numériques intégral prennent en charge [l’arithmétique,](../operators/arithmetic-operators.md) [la logique bitwise,](../operators/bitwise-and-shift-operators.md) [la comparaison,](../operators/comparison-operators.md)et les opérateurs [d’égalité.](../operators/equality-operators.md)

## <a name="characteristics-of-the-integral-types"></a>Caractéristiques des types intégraux

C# prend en charge les types intégraux prédéfinis suivants :

|C# type/mot clé|Plage|Size|Type .NET|
|----------|-----------|----------|-------------|
|`sbyte`|-128 à 127|Entier 8 bits signé|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 à 255|Entier 8 bits non signé|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32 768 à 32 767|Entier 16 bits signé|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 à 65 535|Entier 16 bits non signé|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2 147 483 648 à 2 147 483 647|Entier 32 bits signé|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|de 0 à 4 294 967 295|Entier 32 bits non signé|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|Entier 64 bits signé|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|de 0 à 18 446 744 073 709 551 615|Entier 64 bits non signé|<xref:System.UInt64?displayProperty=nameWithType>|

Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant. Ils sont interchangeables. Par exemple, les déclarations suivantes déclarent des variables du même type :

```csharp
int a = 123;
System.Int32 b = 123;
```

La valeur par défaut pour chaque type intégral est zéro, `0`. Chacun des types intégraux a les constantes `MinValue` et `MaxValue` qui fournissent la valeur minimale et maximale de ce type.

Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé sans limites supérieures ou inférieures.

## <a name="integer-literals"></a>Littéraux d'entier

Les littérals integer peuvent être

- *décimale*: sans préfixe
- *hexadecimal*: `0x` avec `0X` le préfixe ou le préfixe
- *binaire*: `0b` avec `0B` le ou le préfixe (disponible en C 7.0 et plus tard)

Le code suivant montre un exemple de chacun :

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

L’exemple précédent montre `_` également l’utilisation d’un *séparateur à chiffres*, qui est pris en charge à partir de C 7.0. Vous pouvez utiliser le séparateur de chiffre avec toutes sortes de littéral numériques.

Le type d’un littéral integer est déterminé par son suffixe comme suit:

- Si le littéral n’a pas de suffixe, son type est le `int` `uint`premier `long` `ulong`des types suivants dans lesquels sa valeur peut être représentée: , , , .
- Si le littéral est `U` `u`suffixe par ou, son type est le premier des `uint` `ulong`types suivants dans lesquels sa valeur peut être représentée: , .
- Si le littéral est `L` `l`suffixe par ou, son type est le premier des `long` `ulong`types suivants dans lesquels sa valeur peut être représentée: , .

  > [!NOTE]
  > Vous pouvez utiliser la `l` lettre minuscule comme suffixe. Cependant, cela génère un avertissement compilateur parce que la lettre `l` peut être confondue avec le chiffre `1`. Utiliser `L` pour plus de clarté.

- Si le littéral est `UL` `Ul`suffixe par `Lu`, `lu`, `ulong`, `uL` `ul`, `LU`, , `lU`, , ou , son type est .

Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit.

Si le type déterminé d’un `int` littéral integer est et la valeur représentée par le littéral est `sbyte` `byte`dans `short` `ushort`la gamme du type de destination, la valeur peut être implicitement convertie en , , , , `uint`, ou: `ulong`

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Comme l’exemple précédent le montre, si la valeur du littéral n’est pas dans la plage du type de destination, une erreur de compilateur [CS0031](../../misc/cs0031.md) se produit.

Vous pouvez également utiliser un plâtre pour convertir la valeur représentée par un littéral integer au type autre que le type déterminé de littéral:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Conversions

Vous pouvez convertir n’importe quel type numérique intégral à n’importe quel autre type numérique intégral. Si le type de destination peut stocker toutes les valeurs du type source, la conversion est implicite. Sinon, vous devez utiliser [l’opérateur `()` de distribution](../operators/type-testing-and-cast.md#cast-operator-) pour invoquer une conversion explicite. Pour plus d’informations, voir [conversions numériques intégrées](numeric-conversions.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Types intégraux](~/_csharplang/spec/types.md#integral-types)
- [Littéraux d'entier](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Types de valeur](value-types.md)
- [Types virgule flottante](floating-point-numeric-types.md)
- [Chaînes de format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md)
- [Valeurs numériques dans .NET](../../../standard/numerics.md)

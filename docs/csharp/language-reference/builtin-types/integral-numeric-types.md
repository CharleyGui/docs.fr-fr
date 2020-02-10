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
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093199"
---
# <a name="integral-numeric-types--c-reference"></a>Types numériques intégraux (référence C#)

Les *types numériques intégraux* représentent des nombres entiers. Tous les types numériques intégraux sont des [types valeur](value-types.md). Il s’agit également de [types simples](value-types.md#built-in-value-types) qui peuvent être initialisés avec des [littéraux](#integer-literals). Tous les types numériques intégraux prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), de comparaison [logique](../operators/bitwise-and-shift-operators.md), de [comparaison](../operators/comparison-operators.md)et d' [égalité](../operators/equality-operators.md) .

## <a name="characteristics-of-the-integral-types"></a>Caractéristiques des types intégraux

C# prend en charge les types intégraux prédéfinis suivants :

|C# type/mot clé|Plage|Size|Type .NET|
|----------|-----------|----------|-------------|
|`sbyte`|-128 à 127|Entier 8 bits signé|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 à 255|Entier 8 bits non signé|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32 768 à 32 767|Entier 16 bits signé|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 à 65 535|Entier 16 bits non signé|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2 147 483 648 à 2 147 483 647|Entier 32 bits signé|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|de 0 à 4 294 967 295|Entier 32 bits non signé|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|Entier 64 bits signé|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|de 0 à 18 446 744 073 709 551 615|Entier 64 bits non signé|<xref:System.UInt64?displayProperty=nameWithType>|

Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant. Ils sont interchangeables. Par exemple, les déclarations suivantes déclarent des variables du même type :

```csharp
int a = 123;
System.Int32 b = 123;
```

La valeur par défaut pour chaque type intégral est zéro, `0`. Chacun des types intégraux a les constantes `MinValue` et `MaxValue` qui fournissent la valeur minimale et maximale de ce type.

Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé sans limites supérieures ou inférieures.

## <a name="integer-literals"></a>Littéraux d'entier

Les littéraux entiers peuvent être

- *Decimal*: sans préfixe
- *hexadécimal*: avec le préfixe `0x` ou `0X`
- *Binary*: avec le préfixe `0b` ou `0B` (disponible C# dans 7,0 et versions ultérieures)

Le code suivant illustre un exemple de chaque :

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

L’exemple précédent illustre également l’utilisation de `_` comme *séparateur de chiffres*, pris en charge à C# partir de 7,0. Vous pouvez utiliser le séparateur de chiffres avec tous les types de littéraux numériques.

Le type d’un littéral entier est déterminé par son suffixe comme suit :

- Si le littéral n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `int`, `uint`, `long`, `ulong`.
- Si le littéral est précédé d’un suffixe `U` ou `u`, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `uint`, `ulong`.
- Si le littéral est précédé d’un suffixe `L` ou `l`, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `long`, `ulong`.

  > [!NOTE]
  > Vous pouvez utiliser la lettre minuscule `l` comme suffixe. Toutefois, cela génère un avertissement du compilateur, car la lettre `l` peut être confondue avec le chiffre `1`. Utilisez `L` pour plus de clarté.

- Si le littéral est précédé d’un suffixe `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`ou `lu`, son type est `ulong`.

Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit.

Si le type déterminé d’un littéral d’entier est `int` et que la valeur représentée par le littéral est comprise dans la plage du type de destination, la valeur peut être convertie implicitement en `sbyte`, `byte`, `short`, `ushort`, `uint`ou `ulong`:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Comme le montre l’exemple précédent, si la valeur du littéral n’est pas comprise dans la plage du type de destination, une erreur de compilateur [CS0031](../../misc/cs0031.md) se produit.

Vous pouvez également utiliser un cast pour convertir la valeur représentée par un littéral entier en type autre que le type déterminé du littéral :

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Conversions

Vous pouvez convertir n’importe quel type numérique intégral en tout autre type numérique intégral. Si le type de destination peut stocker toutes les valeurs du type source, la conversion est implicite. Dans le cas contraire, vous devez utiliser l' [opérateur de cast `()`](../operators/type-testing-and-cast.md#cast-operator-) pour appeler une conversion explicite. Pour plus d’informations, consultez [conversions numériques intégrées](numeric-conversions.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Types intégraux](~/_csharplang/spec/types.md#integral-types)
- [Littéraux entiers](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types de valeur](value-types.md)
- [Types virgule flottante](floating-point-numeric-types.md)
- [Chaînes de format numériques standard](../../../standard/base-types/standard-numeric-format-strings.md)
- [Valeurs numériques dans .NET](../../../standard/numerics.md)

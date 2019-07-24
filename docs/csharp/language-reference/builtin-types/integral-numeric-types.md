---
title: Types numériques intégraux - Référence C#
description: Découvrez la plage, la taille de stockage et les différentes utilisations associés à chacun des types numériques intégraux.
ms.date: 06/25/2019
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
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236078"
---
# <a name="integral-numeric-types--c-reference"></a>Types numériques intégraux (référence C#)

Les **types numériques intégraux** sont un sous-ensemble des **types simples** et peuvent être initialisés avec des [*littéraux*](#integral-literals). Tous les types intégraux sont également des types valeur. Tous les types numériques intégraux prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), les opérateurs [logiques au niveau du bit](../operators/bitwise-and-shift-operators.md), ainsi que les opérateurs [de comparaison et d’égalité](../operators/equality-operators.md).

## <a name="characteristics-of-the-integral-types"></a>Caractéristiques des types intégraux

C# prend en charge les types intégraux prédéfinis suivants :

|C# type/mot clé|Plage|Size|Type .NET|
|----------|-----------|----------|-------------|
|`sbyte`|-128 à 127|Entier 8 bits signé|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 à 255|Entier 8 bits non signé|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|de -32 768 à 32 767|Entier 16 bits signé|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 à 65 535|Entier 16 bits non signé|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2,147,483,648 en 2,147,483,647|Entier 32 bits signé|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|de 0 à 4 294 967 295|Entier 32 bits non signé|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|Entier 64 bits signé|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|de 0 à 18 446 744 073 709 551 615|Entier 64 bits non signé|<xref:System.UInt64?displayProperty=nameWithType>|

Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant. Ils sont interchangeables. Par exemple, les déclarations suivantes déclarent des variables du même type :

```csharp
int a = 123;
System.Int32 b = 123;
```

La valeur par défaut pour chaque type intégral est zéro, `0`. Chacun des types intégraux a les constantes `MinValue` et `MaxValue` qui fournissent la valeur minimale et maximale de ce type.

Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé sans limites supérieures ou inférieures.

## <a name="integral-literals"></a>Littéraux intégraux

Vous pouvez spécifier les littéraux intégraux en tant que *littéraux décimaux*, *littéraux hexadécimaux* ou *littéraux binaires*. Voici un exemple de chacun de ces littéraux :

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Les littéraux décimaux ne nécessitent aucun préfixe. Les préfixes `x` ou `X` correspondent à un *littéral hexadécimal*. Les préfixes `b` ou `B` correspondent à un *littéral binaire*. La déclaration de `binaryLiteral` illustre l’utilisation de `_` comme un *séparateur numérique*. Vous pouvez aussi utiliser le séparateur numérique avec tous les littéraux numériques. Les littéraux binaires et le séparateur numérique `_` sont pris en charge dans C# 7.0.

### <a name="literal-suffixes"></a>Suffixes littéraux

Les suffixes `l` ou `L` indiquent que le littéral intégral doit être de type `long`. Les suffixes `ul` et `UL` spécifient le type `ulong`. Si le suffixe `L` est utilisé sur un littéral qui est supérieur à 9 223 372 036 854 775 807 (la valeur maximale de `long`), la valeur est convertie vers le type `ulong`. Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit. 

> [!NOTE]
> Vous pouvez utiliser la lettre minuscule « l » comme suffixe. Toutefois, ceci génère un avertissement du compilateur, car la lettre « l » peut être facilement confondue avec le chiffre « 1 ». Utilisez « L » pour plus de clarté.

### <a name="type-of-an-integral-literal"></a>Type d’un littéral intégral

Quand un littéral intégral n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée :

1. `int`
1. `uint`
1. `long`
1. `ulong`

Vous pouvez convertir un littéral intégral en un type ayant une plage plus petite que celle par défaut, à l’aide d’une affectation ou d’un cast :

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

Vous pouvez convertir un littéral intégral en un type ayant une plage plus grande que celle par défaut, à l’aide d’une affectation, d’un cast ou d’un suffixe appliqué au littéral :

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a>Conversions

Entre deux types intégraux, il existe une conversion implicite (appelée *conversion étendue*) où le type de destination peut stocker toutes les valeurs du type source. Par exemple, il existe une conversion implicite de `int` vers `long`, car la plage de valeurs `int` est un sous-ensemble de `long`. Il existe des conversions implicites entre un type intégral non signé plus petit et un type intégral signé plus grand. Il existe également une conversion implicite entre un type intégral et n’importe quel type à virgule flottante.  Il existe une conversion implicite entre un type intégral signé et n’importe quel type intégral non signé.

Vous devez utiliser un cast explicite pour convertir un type intégral en un autre type intégral, lorsqu’une conversion implicite n’est pas définie entre le type source et le type de destination. C’est ce qu’on appelle une *conversion restrictive*. Un scénario explicite est nécessaire, car la conversion peut entraîner une perte de données.

## <a name="see-also"></a>Voir aussi

- [Spécification du langage C# - Types intégraux](~/_csharplang/spec/types.md#integral-types)
- [Informations de référence sur C#](../index.md)
- [Types virgule flottante](floating-point-numeric-types.md)
- [Tableau des valeurs par défaut](../keywords/default-values-table.md)
- [Tableau des formats des résultats numériques](../keywords/formatting-numeric-results-table.md)
- [Tableaux des types intégrés](../keywords/built-in-types-table.md)
- [Valeurs numériques dans .NET](../../../standard/numerics.md)

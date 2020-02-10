---
title: Types numériques à virgule flottante - Référence C#
description: Vue d’ensemble des types virgule flottante C# intégrés
ms.date: 10/22/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 9c8b11f9337ee9de90f2d4d96b5be162713bfcbd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093212"
---
# <a name="floating-point-numeric-types-c-reference"></a>Types numériques à virgule flottante (Référence C#)

Les *types numériques à virgule flottante* représentent des nombres réels. Tous les types numériques à virgule flottante sont des [types valeur](value-types.md). Il s’agit également de [types simples](value-types.md#built-in-value-types) qui peuvent être initialisés avec des [littéraux](#real-literals). Tous les types numériques à virgule flottante prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), de [comparaison](../operators/comparison-operators.md)et d' [égalité](../operators/equality-operators.md) .

## <a name="characteristics-of-the-floating-point-types"></a>Caractéristiques des types à virgule flottante

C# prend en charge les types à virgule flottante prédéfinis suivants :
  
|C# type/mot clé|Plage approximative|Precision|Size|Type .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|±1,5 x 10<sup>−45</sup> à ±3,4 x 10<sup>38</sup>|~6-9 chiffres|4 octets|<xref:System.Single?displayProperty=nameWithType>|
|`double`|De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup>|~15-17 chiffres|8 octets|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1,0 x 10<sup>-28</sup> to ±7,9228 x 10<sup>28</sup>|28 à 29 chiffres|16 octets|<xref:System.Decimal?displayProperty=nameWithType>|

Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant. Ils sont interchangeables. Par exemple, les déclarations suivantes déclarent des variables du même type :

```csharp
double a = 12.3;
System.Double b = 12.3;
```

La valeur par défaut pour tous les types virgule flottante est zéro, `0`. Chacun des types à virgule flottante a les constantes `MinValue` et `MaxValue` qui fournissent la valeur finie minimale et maximale de ce type. Les types `float` et `double` fournissent également des constantes qui représentent des valeurs NaN (Not-a-Number) et d’infini. Par exemple, le type `double` fournit les constantes suivantes : <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> et <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Le type `decimal` fournit une plus grande précision et une plage de valeurs plus petite que `float` et `double`, ce qui le rend particulièrement approprié aux calculs financiers et monétaires.

Vous pouvez combiner des types [intégraux](integral-numeric-types.md) et des types virgule flottante dans une expression. Dans ce cas, les types intégraux sont convertis en types virgule flottante. L’évaluation de l’expression est exécutée d’après les règles suivantes :

- Si l’un des types à virgule flottante est `double`, l’expression prend la valeur `double`, ou la valeur [bool](bool.md) dans les comparaisons d’égalité et relationnelles.
- S’il n’existe aucun type de `double` dans l’expression, l’expression prend la valeur `float`, ou la valeur [bool](bool.md) dans les comparaisons d’égalité et relationnelles.

Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :

- Zéro positif et négatif
- Infini positif et négatif
- Valeur NaN (N’est pas un nombre)
- L’ensemble fini de valeurs différentes de zéro

Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de [l’IEEE](https://www.ieee.org).

Vous pouvez utiliser des [chaînes au format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md) ou des [chaînes au format numérique personnalisées](../../../standard/base-types/custom-numeric-format-strings.md) pour mettre en forme une valeur à virgule flottante.

## <a name="real-literals"></a>Littéraux réels

Le type d’un littéral réel est déterminé par son suffixe comme suit :

- Le littéral sans suffixe ou avec le suffixe `d` ou `D` est de type `double`
- Le littéral avec le suffixe `f` ou `F` est de type `float`
- Le littéral avec le suffixe `m` ou `M` est de type `decimal`

Le code suivant illustre un exemple de chaque :

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

L’exemple précédent illustre également l’utilisation de `_` comme *séparateur de chiffres*, pris en charge à C# partir de 7,0. Vous pouvez utiliser le séparateur de chiffres avec tous les types de littéraux numériques.

Vous pouvez également utiliser la notation scientifique, c’est-à-dire spécifier une partie exposant d’un littéral réel, comme le montre l’exemple suivant :

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Conversions

Il n’existe qu’une seule conversion implicite entre les types numériques à virgule flottante : de `float` à `double`. Toutefois, vous pouvez convertir n’importe quel type à virgule flottante en tout autre type à virgule flottante avec le [cast explicite](../operators/type-testing-and-cast.md#cast-operator-). Pour plus d’informations, consultez [conversions numériques intégrées](numeric-conversions.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Types virgule flottante](~/_csharplang/spec/types.md#floating-point-types)
- [Type décimal](~/_csharplang/spec/types.md#the-decimal-type)
- [Littéraux réels](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types de valeur](value-types.md)
- [Types intégraux](integral-numeric-types.md)
- [Chaînes de format numériques standard](../../../standard/base-types/standard-numeric-format-strings.md)
- [Valeurs numériques dans .NET](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>

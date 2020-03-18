---
title: Types numériques à virgule flottante - Référence C#
description: 'Renseignez-vous sur les types intégrés de points flottants CMD : flotteur, double et décimale'
ms.date: 02/10/2020
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
ms.openlocfilehash: 95b7f266654bbbcdcd0f81e3aa11cfc94af9f0e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77215251"
---
# <a name="floating-point-numeric-types-c-reference"></a>Types numériques à virgule flottante (Référence C#)

Les *types numériques à point flottant* représentent des nombres réels. Tous les types numériques à point flottant sont [des types](value-types.md)de valeur . Ils sont également [des types simples](value-types.md#built-in-value-types) et peuvent être parascés avec des [littérals](#real-literals). Tous les types numériques à point flottant prennent en charge [l’arithmétique,](../operators/arithmetic-operators.md) [la comparaison](../operators/comparison-operators.md)et les opérateurs [d’égalité.](../operators/equality-operators.md)

## <a name="characteristics-of-the-floating-point-types"></a>Caractéristiques des types à virgule flottante

C# prend en charge les types à virgule flottante prédéfinis suivants :
  
|C# type/mot clé|Plage approximative|Precision|Size|Type .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|±1,5 x 10<sup>−45</sup> à ±3,4 x 10<sup>38</sup>|~6-9 chiffres|4 octets|<xref:System.Single?displayProperty=nameWithType>|
|`double`|De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup>|~15-17 chiffres|8 octets|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1,0 x 10<sup>-28</sup> to ±7,9228 x 10<sup>28</sup>|28 à 29 chiffres|16 octets|<xref:System.Decimal?displayProperty=nameWithType>|

Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant. Ils sont interchangeables. Par exemple, les déclarations suivantes déclarent des variables du même type :

```csharp
double a = 12.3;
System.Double b = 12.3;
```

La valeur par défaut pour tous les types virgule flottante est zéro, `0`. Chacun des types à virgule flottante a les constantes `MinValue` et `MaxValue` qui fournissent la valeur finie minimale et maximale de ce type. Les types `float` et `double` fournissent également des constantes qui représentent des valeurs NaN (Not-a-Number) et d’infini. Par exemple, le type `double` fournit les constantes suivantes : <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> et <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Le type `decimal` fournit une plus grande précision et une plage de valeurs plus petite que `float` et `double`, ce qui le rend particulièrement approprié aux calculs financiers et monétaires.

Vous pouvez mélanger les `float` `double` types et les types [intégrals](integral-numeric-types.md) dans une expression. Dans ce cas, les types intégrals sont implicitement convertis en l’un des types de points flottants et, si nécessaire, le `float` type est implicitement converti en `double`. L'expression est évaluée de la manière suivante :

- S’il `double` y a type dans l’expression, l’expression évalue à `double`, ou à [`bool`](bool.md) des comparaisons relationnelles et d’égalité.
- S’il `double` n’y a pas de `float`type dans `bool` l’expression, l’expression évalue à , ou à des comparaisons relationnelles et d’égalité.

Vous pouvez également mélanger `decimal` les types intégrals et le type dans une expression. Dans ce cas, les types intégrals `decimal` sont implicitement convertis au type et l’expression évalue à `decimal`, ou à `bool` des comparaisons relationnelles et d’égalité.

Vous ne `decimal` pouvez pas `float` `double` mélanger le type avec le et les types dans une expression. Dans ce cas, si vous voulez effectuer des opérations d’arithmétique, de comparaison ou `decimal` d’égalité, vous devez convertir explicitement les opérandes, soit du type ou vers le type, comme le montre l’exemple suivant :

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

Vous pouvez utiliser des [chaînes au format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md) ou des [chaînes au format numérique personnalisées](../../../standard/base-types/custom-numeric-format-strings.md) pour mettre en forme une valeur à virgule flottante.

## <a name="real-literals"></a>De vrais littérals

Le type d’un vrai littéral est déterminé par son suffixe comme suit:

- Le littéral sans suffixe ou avec le `d` suffixe ou `D` est de type`double`
- Le littéral `f` `F` avec le suffixe ou est de type`float`
- Le littéral `m` `M` avec le suffixe ou est de type`decimal`

Le code suivant montre un exemple de chacun :

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

L’exemple précédent montre `_` également l’utilisation d’un *séparateur à chiffres*, qui est pris en charge à partir de C 7.0. Vous pouvez utiliser le séparateur de chiffre avec toutes sortes de littéral numériques.

Vous pouvez également utiliser la notation scientifique, c’est-à-dire, spécifier une partie exposante d’un véritable littéral, comme le montre l’exemple suivant :

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Conversions

Il n’y a qu’une seule `float` conversion `double`implicite entre les types numériques à point flottant : de . Cependant, vous pouvez convertir n’importe quel type de point flottant à n’importe quel autre type de point flottant avec le [casting explicite](../operators/type-testing-and-cast.md#cast-operator-). Pour plus d’informations, voir [conversions numériques intégrées](numeric-conversions.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Types virgule flottante](~/_csharplang/spec/types.md#floating-point-types)
- [Le type décimal](~/_csharplang/spec/types.md#the-decimal-type)
- [De vrais littérals](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Types de valeur](value-types.md)
- [Types intégraux](integral-numeric-types.md)
- [Chaînes de format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md)
- [Valeurs numériques dans .NET](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>

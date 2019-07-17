---
title: Types numériques à virgule flottante - Référence C#
description: Vue d’ensemble des types virgule flottante C# intégrés
ms.date: 06/30/2019
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
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664189"
---
# <a name="floating-point-numeric-types-c-reference"></a>Types numériques à virgule flottante (Référence C#)

Les **types numériques à virgule flottante** sont un sous-ensemble des **types simples** et peuvent être initialisés avec des [*littéraux*](#floating-point-literals). Tous les types virgule flottante sont également des types valeur. Tous les types numériques à virgule flottante prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md) et les opérateurs de [comparaison et d’égalité](../operators/equality-operators.md).

Le tableau suivant indique la plage de valeurs approximative et la précision pour les types virgule flottante :
  
|Type|Plage approximative|Précision|  
|----------|-----------------------|---------------|  
|`float`|±1,5 x 10<sup>−45</sup> à ±3,4 x 10<sup>38</sup>|~6-9 chiffres|  
|`double`|De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup>|~15-17 chiffres|  
|`decimal`|±1,0 x 10<sup>-28</sup> to ±7,9228 x 10<sup>28</sup>|28 à 29 chiffres|  

La valeur par défaut pour tous les types virgule flottante est `0`. Chaque type virgule flottante a des constantes nommées `MinValue` et `MaxValue` correspondant à la valeur minimale et à la valeur maximale. Les types `float` et `double` ont des constantes supplémentaires pour `PositiveInfinity`, `NegativeInfinity` et `NaN` (pour « Pas un nombre »). Le type `decimal` contient des constantes pour `Zero`, `One` et `MinusOne`.

Le type `decimal` fournit une plus grande précision et une plage de valeurs plus petite que `float` et `double`, ce qui le rend particulièrement approprié aux calculs financiers et monétaires.

Vous pouvez combiner des types intégraux et des types virgule flottante dans une expression. Dans ce cas, les types intégraux sont convertis en types virgule flottante. L’évaluation de l’expression est exécutée d’après les règles suivantes :

- Si l’un des types virgule flottante est `double`, l’expression prend la valeur `double` ou [bool](../keywords/bool.md) dans les comparaisons relationnelles ou les comparaisons d’égalité.
- S’il n’y a aucun type `double` dans l’expression, celle-ci prend la valeur `float` ou [bool](../keywords/bool.md) dans les comparaisons relationnelles ou les comparaisons d’égalité.

Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :

- Zéro positif et négatif
- Infini positif et négatif
- Valeur NaN (N’est pas un nombre)
- L’ensemble fini de valeurs différentes de zéro

Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de [l’IEEE](https://www.ieee.org).

Vous pouvez utiliser des [chaînes au format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md) ou des [chaînes au format numérique personnalisées](../../../standard/base-types/custom-numeric-format-strings.md) pour mettre en forme une valeur à virgule flottante.

## <a name="floating-point-literals"></a>Littéraux à virgule flottante

Par défaut, un littéral numérique à virgule flottante sur le côté droit de l’opérateur d’assignation est traité comme `double`. Vous pouvez utiliser des suffixes pour convertir un littéral à virgule flottante ou intégral en un type spécifique :

- Le suffixe `d` ou `D` convertit un littéral en `double`.
- Le suffixe `f` ou `F` convertit un littéral en `float`.
- Le suffixe `m` ou `M` convertit un littéral en `decimal`.

Les exemples suivants montrent chaque suffixe :

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>Conversions

Il existe une conversion implicite (appelée *conversion étendue*) de `float` en `double` parce que la plage de valeurs `float` est un sous-ensemble de `double` et qu’aucune perte de précision ne se produit de `float` en `double`. 

Vous devez utiliser un cast explicite pour convertir un type virgule flottante en un autre type virgule flottante, lorsqu’une conversion implicite n’est pas définie entre le type source et le type de destination. C’est ce qu’on appelle une *conversion restrictive*. Un scénario explicite est nécessaire, car la conversion peut entraîner une perte de données. Il n’existe aucune conversion implicite entre les autres types virgule flottante et le type `decimal` parce que le type `decimal` a une plus grande précision que celle de `float` ou `double`.

Pour plus d’informations sur les conversions numériques implicites, consultez [Tableau des conversions numériques implicites](../keywords/implicit-numeric-conversions-table.md).

Pour plus d’informations sur les conversions numériques explicites, consultez [Tableau des conversions numériques explicites](../keywords/explicit-numeric-conversions-table.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Types intégraux](integral-numeric-types.md)
- [Tableau des valeurs par défaut](../keywords/default-values-table.md)
- [Tableau des formats des résultats numériques](../keywords/formatting-numeric-results-table.md)
- [Tableaux des types intégrés](../keywords/built-in-types-table.md)
- [Valeurs numériques dans .NET](../../../standard/numerics.md)
- [Cast et conversions de types](../../programming-guide/types/casting-and-type-conversions.md)
- [Tableau des conversions numériques implicites](../keywords/implicit-numeric-conversions-table.md)
- [Tableau des conversions numériques explicites](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md)

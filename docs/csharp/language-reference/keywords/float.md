---
title: float, mot clé - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: db0139f2000c1bc2c5a13a3a542164201e73f0fb
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424207"
---
# <a name="float-c-reference"></a>float (référence C#)

Le mot clé `float` désigne un type simple qui stocke des valeurs à virgule flottante de 32 bits. Le tableau suivant montre la précision et la plage approximative pour le type `float`.

|Type|Plage approximative|Précision|Type .NET|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|±1,5 x 10<sup>−45</sup> à ±3,4 x 10<sup>38</sup>|~6-9 chiffres|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a>Littéraux

Par défaut, un littéral numérique réel sur le côté droit de l’opérateur d’assignation est traité comme un [double](double.md). Par conséquent, pour initialiser une variable de type float, utilisez le suffixe `f` ou `F`, comme dans l’exemple suivant :

```csharp
float x = 3.5F;
```

Si vous n’utilisez pas de suffixe dans la déclaration précédente, vous obtiendrez une erreur de compilation, puisque vous essayez de stocker une valeur [double](double.md) dans une variable `float`.

## <a name="conversions"></a>Conversions

Vous pouvez combiner des types numériques intégraux et des types virgule flottante dans une expression. Dans ce cas, les types intégraux sont convertis en types virgule flottante. L’évaluation de l’expression est exécutée d’après les règles suivantes :

- Si l’un des types virgule flottante est [double](double.md), l’expression prend la valeur [double](double.md), ou [bool](bool.md) dans les comparaisons relationnelles ou les comparaisons d’égalité.

- S’il n’y a aucun type [double](double.md) dans l’expression, elle prend la valeur `float`, ou [bool](bool.md) dans les comparaisons relationnelles ou les comparaisons d’égalité.

Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :

- Zéro positif et négatif

- Infini positif et négatif

- Valeur NaN (N’est pas un nombre)

- L’ensemble fini de valeurs différentes de zéro

Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de [l’IEEE](https://www.ieee.org).

## <a name="example"></a>Exemples

Dans l’exemple suivant, un [int](../builtin-types/integral-numeric-types.md), un [short](../builtin-types/integral-numeric-types.md) et un `float` sont inclus dans une expression mathématique produisant un résultat `float`. (N’oubliez pas que `float` est un alias du type <xref:System.Single?displayProperty=nameWithType>.) Notez qu’il n’y a aucune valeur [double](double.md) dans l’expression.

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Single>
- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Cast et conversions de types](../../programming-guide/types/casting-and-type-conversions.md)
- [Mots clés C#](index.md)
- [Types intégraux](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [Tableau des types intégrés](built-in-types-table.md)
- [Tableau des conversions numériques implicites](implicit-numeric-conversions-table.md)
- [Tableau des conversions numériques explicites](explicit-numeric-conversions-table.md)

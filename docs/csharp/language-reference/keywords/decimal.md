---
title: decimal, mot clé - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 7ad01f9e4f5a8b1a153b1ef306e9d6168335eb3d
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424305"
---
# <a name="decimal-c-reference"></a>decimal (référence C#)

Le mot clé `decimal` indique un type de données 128 bits. Par rapport à d’autres types virgule flottante, le type `decimal` fournit une plus grande précision et une plage de valeurs plus réduite ; il est donc particulièrement approprié aux calculs financiers et monétaires. Le tableau suivant indique la plage de valeurs approximative et la précision fournies par le type `decimal`.

|Type|Plage approximative|Précision|Type .NET|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|±1,0 x 10<sup>-28</sup> to ±7,9228 x 10<sup>28</sup>|28-29 chiffres significatifs|<xref:System.Decimal?displayProperty=nameWithType>|

La valeur par défaut de `decimal` est 0m.

## <a name="literals"></a>Littéraux

Si vous souhaitez qu'un littéral numérique réel soit considéré comme une valeur de type `decimal`, utilisez le suffixe m ou M, comme indiqué ci-après :

```csharp
decimal myMoney = 300.5m;
```

Si le suffixe m n’est pas spécifié, le nombre est considéré comme une valeur de type [double](../../../csharp/language-reference/keywords/double.md) et génère une erreur du compilateur.

## <a name="conversions"></a>Conversions

Les types intégraux sont convertis implicitement en type `decimal` et ont pour résultat une valeur de type `decimal`. Par conséquent, vous pouvez initialiser une variable de type decimal avec un littéral d'entier, sans utiliser de suffixe, par exemple :

```csharp
decimal myMoney = 300;
```

Étant donné qu’il n’y a pas de conversion implicite entre les autres types virgule flottante et le type `decimal`, un cast doit être utilisé pour convertir ces types. Par exemple :

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

Vous pouvez aussi combiner, au sein d'une même expression, des types `decimal` et des types numériques intégraux. En revanche, si vous combinez le type `decimal` avec les autres types virgule flottante sans spécifier de cast, une erreur de compilation se produit.

Pour plus d’informations sur les conversions numériques implicites, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).

Pour plus d’informations sur les conversions numériques explicites, consultez [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).

## <a name="formatting-decimal-output"></a>Mise en forme d’une sortie décimale

Vous pouvez appliquer un format à un résultat à l'aide de la méthode `String.Format`, ou de la méthode <xref:System.Console.Write%2A?displayProperty=nameWithType>, qui appelle `String.Format()`. Le format monétaire est spécifié à l'aide du format de chaîne monétaire standard « C » ou « c », comme le montre le second exemple traité ultérieurement dans cet article. Pour plus d'informations sur la méthode `String.Format`, consultez <xref:System.String.Format%2A?displayProperty=nameWithType>.

## <a name="example"></a>Exemples

L’exemple suivant provoque une erreur du compilateur en essayant d’ajouter les variables [double](../../../csharp/language-reference/keywords/double.md) et `decimal`.

```csharp
decimal dec = 0m;
double dub = 9;
// The following line causes an error that reads "Operator '+' cannot be applied to
// operands of type 'double' and 'decimal'"
Console.WriteLine(dec + dub);

// You can fix the error by using explicit casting of either operand.
Console.WriteLine(dec + (decimal)dub);
Console.WriteLine((double)dec + dub);
```

Le résultat est l'erreur suivante :

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

Dans cet exemple, un `decimal` et un [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) sont combinés dans la même expression. Le résultat est de type `decimal`.

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a>Exemples

Dans cet exemple, le résultat est mis en forme à l'aide de la chaîne de format monétaire. Notez que la valeur `x` est arrondie, car le nombre de décimales excède 0,99 $. La variable `y`, représentant le nombre maximal exact de chiffres, est affichée dans le format correct.

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Decimal>
- [Référence C#](../../../csharp/language-reference/index.md)
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Mots clés C#](../../../csharp/language-reference/keywords/index.md)
- [Types intégraux](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md)

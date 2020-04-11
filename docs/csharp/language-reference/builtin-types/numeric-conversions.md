---
title: Conversions numériques intégrées - Référence C
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: b7d53e508e4d585c746a3cc61824cdace7707deb
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121451"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Conversions numériques intégrées (référence C)

Cmd fournit un ensemble de types [numériques intégrals](integral-numeric-types.md) et [flottants.](floating-point-numeric-types.md) Il existe une conversion entre deux types numériques, implicites ou explicites. Vous devez utiliser une [expression de fonte](../operators/type-testing-and-cast.md#cast-expression) pour effectuer une conversion explicite.

## <a name="implicit-numeric-conversions"></a>Conversions numériques implicites

Le tableau suivant montre les conversions implicites prédéfinies entre les types numériques intégrés :

|À partir|À|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double` ou `decimal`|
|[byte](integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|
|[short](integral-numeric-types.md)|`int`, `long`, `float`, `double` ou`decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|
|[int](integral-numeric-types.md)|`long`, `float`, `double` ou `decimal`|
|[uint](integral-numeric-types.md)|`long`, `ulong`, `float`, `double` ou`decimal`|
|[Long](integral-numeric-types.md)|`float`, `double` ou `decimal`|
|[Ulong](integral-numeric-types.md)|`float`, `double` ou `decimal`|
|[Flotteur](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> Les conversions `int`implicites `long`de `ulong` `float` , `uint`, `ulong` `double` ou à et à partir `long` ou à peut causer une perte de précision, mais jamais une perte d’un ordre de grandeur. Les autres conversions numériques implicites ne perdent jamais d’informations.

Notez également que

- Tout [type numérique intégral](integral-numeric-types.md) est implicitement convertible à n’importe quel type numérique à point [flottant.](floating-point-numeric-types.md)

- Il n’y a `byte` pas `sbyte` de conversions implicites aux types et aux types. Il n’existe aucune conversion implicite à partir des types `double` et `decimal`.

- Il n’existe aucune conversion implicite entre le type `decimal` et le type `float` ou `double`.

- Une valeur d’une `int` expression constante de type (par exemple, une valeur représentée par un `sbyte` `byte`littéral integer) peut être implicitement convertie en , , `short`, `ushort`, `uint`, ou `ulong`, si elle est dans la gamme du type de destination:

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Comme l’exemple précédent l’indique, si la valeur constante n’est pas dans la plage du type de destination, une erreur de compilateur [CS0031](../../misc/cs0031.md) se produit.

## <a name="explicit-numeric-conversions"></a>Conversions numériques explicites

Le tableau suivant montre les conversions explicites prédéfinies entre les types numériques intégrés pour lesquels il n’y a pas [de conversion implicite](#implicit-numeric-conversions):

|À partir|À|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`byte`, `ushort`, `uint` ou `ulong`|
|[byte](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint` ou`ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte` ou `short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort` ou`int`|
|[Long](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` ou `ulong`|
|[Ulong](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` ou `long`|
|[Flotteur](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong` ou `decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , , ,`decimal`|
|[Decimales](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , , ,`double`|

> [!NOTE]
> Une conversion numérique explicite peut entraîner une perte <xref:System.OverflowException>de données ou jeter une exception, généralement un .

Notez également que

- Quand vous convertissez une valeur d’un type intégral en un autre type intégral, le résultat varie selon le [contexte de vérification](../keywords/checked-and-unchecked.md) du dépassement. Dans un contexte vérifié, la conversion réussit si la valeur source se situe dans la plage du type de destination. Sinon, une exception <xref:System.OverflowException> est levée. Dans un contexte non vérifié, la conversion réussit toujours et procède comme suit :

  - Si le type source est plus grand que le type de destination, la valeur source est tronquée via l’abandon de ses bits « supplémentaires » les plus significatifs. Le résultat est ensuite traité en tant que valeur du type de destination.

  - Si le type source est plus petit que le type de destination, alors la valeur source est soit prorogée ou sans prolongation de sorte qu’elle est de la même taille que le type de destination. L’extension de signe est utilisée si le type source est signé. L’extension de zéro est utilisée si le type source est non signé. Le résultat est ensuite traité en tant que valeur du type de destination.

  - Si le type source a la même taille que le type de destination, la valeur source est traitée comme une valeur du type de destination.

- Quand vous convertissez une valeur de type `decimal` en type intégral, la valeur source est arrondie vers zéro à la valeur intégrale la plus proche. Si la valeur intégrale obtenue se trouve en dehors de la plage du type de destination, une exception <xref:System.OverflowException> est levée.

- Quand vous convertissez une valeur `double` ou `float` en type intégral, cette valeur est arrondie vers zéro, à la valeur intégrale la plus proche. Si la valeur intégrale résultante se situe en dehors de la plage du type de destination, le résultat varie selon le [contexte de vérification](../keywords/checked-and-unchecked.md) du dépassement. Dans un contexte vérifié, une exception <xref:System.OverflowException> est levée, alors que dans un contexte non vérifié, le résultat est une valeur non spécifiée du type de destination.

- Quand vous convertissez `double` en `float`, la valeur `double` est arrondie à la valeur `float` la plus proche. Si `double` la valeur est trop petite ou `float` trop grande pour s’intégrer dans le type, le résultat est nul ou infini.

- Dans le cas d’une conversion de `float` ou `double` en `decimal`, la valeur source est convertie en une représentation `decimal` et arrondie au nombre le plus proche après la 28ème décimale, si nécessaire. Selon la valeur de la valeur source, la conversion peut aboutir à l’un des résultats suivants :

  - Si la valeur source est trop petite pour être représentée en tant que `decimal`, le résultat est zéro.

  - Si la valeur source est une valeur non numérique (NaN), un nombre infini ou une valeur trop grande pour être représentée au format `decimal`, une exception <xref:System.OverflowException> est levée.

- Lorsque vous `decimal` `float` vous `double`convertissez à ou, `float` la `double` valeur source est arrondie au plus proche ou à la valeur, respectivement.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Conversions numériques implicites](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Conversions numériques explicites](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Casting et conversions de type](../../programming-guide/types/casting-and-type-conversions.md)

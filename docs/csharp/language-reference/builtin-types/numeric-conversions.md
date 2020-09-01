---
description: 'En savoir plus sur les conversions implicites et explicites entre les types numériques intégrés en C #'
title: Conversions numériques intégrées-référence C#
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: ee5def3b5e0e067919a8c8335db701dbb6dd4d88
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142243"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Conversions numériques intégrées (référence C#)

C# fournit un ensemble de types numériques [intégraux](integral-numeric-types.md) et [à virgule flottante](floating-point-numeric-types.md) . Il existe une conversion entre deux types numériques, implicite ou explicite. Vous devez utiliser une [expression de cast](../operators/type-testing-and-cast.md#cast-expression) pour effectuer une conversion explicite.

## <a name="implicit-numeric-conversions"></a>Conversions numériques implicites

Le tableau suivant montre les conversions implicites prédéfinies entre les types numériques intégrés :

|À partir|À|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double` ou `decimal`|
|[byte](integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|
|[short](integral-numeric-types.md)|`int`, `long`, `float`, `double` ou`decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|
|[int](integral-numeric-types.md)|`long`, `float`, `double` ou `decimal`|
|[uint](integral-numeric-types.md)|`long`, `ulong`, `float`, `double` ou`decimal`|
|[long](integral-numeric-types.md)|`float`, `double`ou `decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double`ou `decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> Les conversions implicites de `int` ,, `uint` `long` ou `ulong` vers `float` et à partir de `long` ou `ulong` en `double` peuvent entraîner une perte de précision, mais jamais une perte d’un ordre de grandeur. Les autres conversions numériques implicites ne perdent jamais d’informations.

Notez également que

- Tout [type numérique intégral](integral-numeric-types.md) est implicitement convertible en [type numérique à virgule flottante](floating-point-numeric-types.md).

- Il n’existe aucune conversion implicite des `byte` types et `sbyte` . Il n’existe aucune conversion implicite à partir des types `double` et `decimal`.

- Il n’existe aucune conversion implicite entre le type `decimal` et le type `float` ou `double`.

- La valeur d’une expression constante de type `int` (par exemple, une valeur représentée par un littéral entier) peut être implicitement convertie en `sbyte` , `byte` , `short` , `ushort` , `uint` ou `ulong` , si elle se trouve dans la plage du type de destination :

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Comme le montre l’exemple précédent, si la valeur de constante n’est pas comprise dans la plage du type de destination, une erreur de compilateur [CS0031](../../misc/cs0031.md) se produit.

## <a name="explicit-numeric-conversions"></a>Conversions numériques explicites

Le tableau suivant montre les conversions explicites prédéfinies entre les types numériques intégrés pour lesquels il n’existe pas de [conversion implicite](#implicit-numeric-conversions):

|À partir|À|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`byte`, `ushort`, `uint` ou `ulong`|
|[byte](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint` ou`ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte`ou `short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort` ou`int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` ou `ulong`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` ou `long`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong` ou `decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `float` ou `decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `float` ou `double`|

> [!NOTE]
> Une conversion numérique explicite peut entraîner une perte de données ou lever une exception, en général un <xref:System.OverflowException> .

Notez également que

- Quand vous convertissez une valeur d’un type intégral en un autre type intégral, le résultat varie selon le [contexte de vérification](../keywords/checked-and-unchecked.md) du dépassement. Dans un contexte vérifié, la conversion réussit si la valeur source se situe dans la plage du type de destination. Sinon, une exception <xref:System.OverflowException> est levée. Dans un contexte non vérifié, la conversion réussit toujours et procède comme suit :

  - Si le type source est plus grand que le type de destination, la valeur source est tronquée via l’abandon de ses bits « supplémentaires » les plus significatifs. Le résultat est ensuite traité en tant que valeur du type de destination.

  - Si le type de source est plus petit que le type de destination, la valeur source est un signe étendu ou étendu à zéro, afin qu’elle soit de la même taille que le type de destination. L’extension de signe est utilisée si le type source est signé. L’extension de zéro est utilisée si le type source est non signé. Le résultat est ensuite traité en tant que valeur du type de destination.

  - Si le type source a la même taille que le type de destination, la valeur source est traitée comme une valeur du type de destination.

- Quand vous convertissez une valeur de type `decimal` en type intégral, la valeur source est arrondie vers zéro à la valeur intégrale la plus proche. Si la valeur intégrale obtenue se trouve en dehors de la plage du type de destination, une exception <xref:System.OverflowException> est levée.

- Quand vous convertissez une valeur `double` ou `float` en type intégral, cette valeur est arrondie vers zéro, à la valeur intégrale la plus proche. Si la valeur intégrale résultante se situe en dehors de la plage du type de destination, le résultat varie selon le [contexte de vérification](../keywords/checked-and-unchecked.md) du dépassement. Dans un contexte vérifié, une exception <xref:System.OverflowException> est levée, alors que dans un contexte non vérifié, le résultat est une valeur non spécifiée du type de destination.

- Quand vous convertissez `double` en `float`, la valeur `double` est arrondie à la valeur `float` la plus proche. Si la `double` valeur est trop petite ou trop grande pour être contenue dans le `float` type, le résultat est zéro ou infini.

- Dans le cas d’une conversion de `float` ou `double` en `decimal`, la valeur source est convertie en une représentation `decimal` et arrondie au nombre le plus proche après la 28ème décimale, si nécessaire. Selon la valeur de la valeur source, la conversion peut aboutir à l’un des résultats suivants :

  - Si la valeur source est trop petite pour être représentée en tant que `decimal`, le résultat est zéro.

  - Si la valeur source est une valeur non numérique (NaN), un nombre infini ou une valeur trop grande pour être représentée au format `decimal`, une exception <xref:System.OverflowException> est levée.

- Lorsque vous convertissez `decimal` en `float` ou `double` , la valeur source est arrondie à la `float` valeur ou la plus proche `double` , respectivement.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Conversions numériques implicites](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Conversions numériques explicites](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Cast et conversions de types](../../programming-guide/types/casting-and-type-conversions.md)

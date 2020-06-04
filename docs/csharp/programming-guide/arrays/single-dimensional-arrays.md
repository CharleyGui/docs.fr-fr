---
title: Tableaux unidimensionnels - Guide de programmation C#
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: e189253eedc21fa2d51e16407f04b034610bb57b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410242"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tableaux unidimensionnels (Guide de programmation C#)

Vous créez un tableau unidimensionnel à l’aide de l’opérateur [New](../../language-reference/operators/new-operator.md) en spécifiant le type d’élément de tableau et le nombre d’éléments. L’exemple suivant déclare un tableau de cinq entiers :

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

Ce tableau contient les éléments de `array[0]` à `array[4]`. Les éléments du tableau sont initialisés à la valeur par défaut du type d’élément, `0` pour les entiers.

Les tableaux peuvent stocker tout type d’élément que vous spécifiez, comme dans l’exemple suivant, qui déclare un tableau de chaînes :

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a>Initialisation du tableau

Vous pouvez initialiser les éléments d’un tableau lorsque vous déclarez le tableau. Le spécificateur de longueur n’est pas nécessaire, car il est déduit par le nombre d’éléments dans la liste d’initialisation. Par exemple :

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

Le code suivant illustre une déclaration d’un tableau de chaînes où chaque élément de tableau est initialisé par un nom de jour :

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
Vous pouvez éviter l' `new` expression et le type de tableau lorsque vous initialisez un tableau lors de la déclaration, comme indiqué dans le code suivant. C’est ce qu’on appelle un [tableau implicitement typé](implicitly-typed-arrays.md):

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

Vous pouvez déclarer une variable tableau sans la créer, mais vous devez utiliser l' `new` opérateur quand vous assignez un nouveau tableau à cette variable. Par exemple :

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a>Tableaux de types valeur et de types référence

Considérons la déclaration de tableau suivante :  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

Le résultat de cette instruction varie selon que `SomeType` est un type valeur ou un type référence. S’il s’agit d’un type valeur, l’instruction crée un tableau de 10 éléments, chacun d’entre eux ayant le type `SomeType` . Si `SomeType` est un type référence, l’instruction crée un tableau de 10 éléments dont chacun est initialisé avec une référence null. Dans les deux instances, les éléments sont initialisés à la valeur par défaut pour le type d’élément. Pour plus d’informations sur les types valeur et les types référence, consultez types [valeur](../../language-reference/builtin-types/value-types.md) et [types référence](../../language-reference/keywords/reference-types.md).
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Array>
- [Tableaux](./index.md)
- [Tableaux multidimensionnels](./multidimensional-arrays.md)
- [Tableaux en escalier](./jagged-arrays.md)

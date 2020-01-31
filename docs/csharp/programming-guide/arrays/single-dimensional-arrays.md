---
title: Tableaux unidimensionnels - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 8f093d22da789c6df750475e47a3b4e4685c5651
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744209"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tableaux unidimensionnels (Guide de programmation C#)

Vous pouvez déclarer un tableau unidimensionnel de cinq entiers comme indiqué dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Ce tableau contient les éléments de `array[0]` à `array[4]`. L’opérateur [new](../../language-reference/operators/new-operator.md) est utilisé pour créer le tableau et initialiser ses éléments à leurs valeurs par défaut. Dans cet exemple, tous les éléments du tableau sont initialisés à zéro.  
  
 Un tableau qui stocke des éléments de type chaîne peut être déclaré de la même façon. Par exemple :  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Initialisation du tableau

 Il est possible d’initialiser un tableau lors de sa déclaration, auquel cas le spécificateur de longueur n’est pas nécessaire, car il est déjà fourni par le nombre d’éléments figurant dans la liste d’initialisation. Par exemple :  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Un tableau de chaînes peut être initialisé de la même manière. Voici une déclaration d’un tableau de chaînes où chaque élément du tableau est initialisé par un nom de jour de la semaine :  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 Quand vous initialisez un tableau lors de sa déclaration, vous pouvez utiliser les raccourcis suivants :  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Il est possible de déclarer une variable de tableau sans initialisation, mais vous devez alors utiliser l’opérateur `new` quand vous affectez un tableau à cette variable. Par exemple :  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C# 3.0 introduit les tableaux implicitement typés. Pour plus d’informations, consultez [Tableaux implicitement typés](./implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Tableaux de types valeur et de types référence

 Considérons la déclaration de tableau suivante :  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Le résultat de cette instruction varie selon que `SomeType` est un type valeur ou un type référence. S’il s’agit d’un type de valeur, l’instruction crée un tableau de 10 éléments, chacun ayant le type `SomeType`. Si `SomeType` est un type référence, l’instruction crée un tableau de 10 éléments dont chacun est initialisé avec une référence null.  
  
Pour plus d’informations sur les types valeur et les types référence, consultez types [valeur](../../language-reference/builtin-types/value-types.md) et [types référence](../../language-reference/keywords/reference-types.md).
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Array>
- [Guide de programmation C#](../index.md)
- [Tableaux](./index.md)
- [Tableaux multidimensionnels](./multidimensional-arrays.md)
- [Tableaux en escalier](./jagged-arrays.md)

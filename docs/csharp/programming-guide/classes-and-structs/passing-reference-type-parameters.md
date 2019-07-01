---
title: Passage de paramètres de type référence - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: 1b2aae49fbea138646b5f325919246238b2401ae
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398355"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Passage de paramètres de type référence (Guide de programmation C#)
Une variable d’un [type référence](../../../csharp/language-reference/keywords/reference-types.md) ne contient pas directement ses données ; il contient une référence à ses données. Quand vous passez un paramètre de type référence par valeur, il est possible de changer les données appartenant à l’objet référencé, comme la valeur d’un membre de classe. En revanche, vous ne pouvez pas changer la valeur de la référence elle-même ; par exemple, vous ne pouvez pas utiliser la même référence pour allouer de la mémoire à un nouvel objet et la faire persister en dehors de la méthode. Pour cela, passez le paramètre en utilisant le mot clé [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md). Pour des raisons de simplicité, les exemples suivants utilisent `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Passage de types référence par valeur  
 L’exemple suivant illustre le passage d’un paramètre de type référence (`arr`) par valeur, à une méthode (`Change`). Sachant que le paramètre est une référence à `arr`, il est possible de modifier les valeurs des éléments du tableau. Cependant, la tentative de réassignation du paramètre à un emplacement de mémoire différent n’aboutit qu’à l’intérieur de la méthode et n’affecte pas la variable d’origine, `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 Dans l’exemple précédent, le tableau `arr`, qui est un type référence, est passé à la méthode sans le paramètre `ref`. Dans ce cas, une copie de la référence, qui pointe vers `arr`, est passée à la méthode. La sortie montre que la méthode peut modifier le contenu d’un élément du tableau, dans ce cas de `1` à `888`. Cependant, si vous allouez une nouvelle portion de mémoire via l’opérateur [new](../../../csharp/language-reference/operators/new-operator.md) à l’intérieur de la méthode `Change`, la variable `pArray` fait référence à un nouveau tableau. Par conséquent, les modifications apportées à la suite de cette opération n’ont pas d’effet sur le tableau d’origine (`arr`), qui est créé à l’intérieur de `Main`. En fait, deux tableaux sont créés dans cet exemple : un à l’intérieur de `Main` et un autre à l’intérieur de la méthode `Change`.  
  
## <a name="passing-reference-types-by-reference"></a>Passage de types référence par référence  
 L’exemple suivant est identique au précédent, sauf que le mot clé `ref` est ajouté à l’en-tête et à l’appel de la méthode. Les modifications qui se produisent dans la méthode affectent la variable d’origine dans le programme appelant.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Les modifications qui se produisent à l’intérieur de la méthode affectent le tableau d’origine dans `Main`. En fait, le tableau d’origine est réalloué à l’aide de l’opérateur `new`. Par conséquent, après l’appel à la méthode `Change`, toute référence à `arr` pointe vers le tableau à cinq éléments, qui est créé dans la méthode `Change`.  
  
## <a name="swapping-two-strings"></a>Permutation de deux chaînes  
 La permutation de chaînes est un bon exemple de passage de paramètres de type référence par référence. Dans l’exemple, deux chaînes, `str1` et `str2`, sont initialisées dans `Main` et passées à la méthode `SwapStrings` en tant que paramètres modifiés par le mot clé `ref`. Les deux chaînes sont permutées à l’intérieur de la méthode mais aussi à l’intérieur de `Main`.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 Dans cet exemple, les paramètres doivent être passés par référence pour affecter les variables dans le programme appelant. Si vous supprimez le mot clé `ref` de l’en-tête et de l’appel de la méthode, aucune modification ne se produit dans le programme appelant.  
  
 Pour plus d’informations sur les chaînes, consultez [string](../../../csharp/language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Passage de paramètres](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
- [ref](../../../csharp/language-reference/keywords/ref.md)
- [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)
- [out](../../../csharp/language-reference/keywords/out.md)
- [Types référence](../../../csharp/language-reference/keywords/reference-types.md)

---
title: Passage de tableaux en tant qu’arguments - Guide de programmation C#
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705689"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Passage de tableaux en tant qu’arguments (Guide de programmation C#)

Les tableaux peuvent être passés en tant qu’arguments à des paramètres de méthode. Comme les tableaux sont des types référence, la méthode peut modifier la valeur des éléments.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Passage de tableaux unidimensionnels en tant qu’arguments

Vous pouvez passer un tableau unidimensionnel initialisé à une méthode. Par exemple, l’instruction suivante envoie un tableau à une méthode Print.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Le code suivant illustre une implémentation partielle de la méthode Print.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a> Exemple

Dans l’exemple suivant, un tableau de chaînes est initialisé et passé en tant qu’argument à une méthode `DisplayArray` pour des chaînes. La méthode affiche les éléments du tableau. Ensuite, la méthode `ChangeArray` inverse les éléments du tableau, puis la méthode `ChangeArrayElements` modifie les trois premiers éléments du tableau. Une fois que chaque méthode est retournée, la méthode `DisplayArray` montre que le passage d’un tableau par valeur n’empêche pas les modifications des éléments du tableau.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Passage de tableaux multidimensionnels en tant qu’arguments

Vous pouvez passer un tableau multidimensionnel initialisé à une méthode de la même manière que vous passez un tableau unidimensionnel.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Le code suivant illustre une déclaration partielle d’une méthode Print qui accepte un tableau à deux dimensions en tant qu’argument.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant :

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a> Exemple

Dans l’exemple suivant, un tableau à deux dimensions d’entiers est initialisé et passé à la méthode `Print2DArray`. La méthode affiche les éléments du tableau.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Tableaux](index.md)
- [Tableaux unidimensionnels](single-dimensional-arrays.md)
- [Tableaux multidimensionnels](multidimensional-arrays.md)
- [Arrays déchiquetés](jagged-arrays.md)

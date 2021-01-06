---
title: Tableaux en escalier - Guide de programmation C#
description: Un tableau en escalier en C# est un tableau dont les éléments sont des tableaux de tailles différentes. Découvrez comment déclarer, initialiser et accéder à des tableaux en escalier.
ms.date: 12/18/2020
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 6d4fb939fb6594c7644a80eb688ea852ddf8a5c5
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97737279"
---
# <a name="jagged-arrays-c-programming-guide"></a>Tableaux en escalier (Guide de programmation C#)

Un tableau en escalier est un tableau dont les éléments sont des tableaux, éventuellement de tailles différentes. Un tableau en escalier est parfois appelé « tableau de tableaux ». Les exemples suivants montrent comment déclarer, initialiser et accéder aux tableaux en escalier.

 Voici une déclaration d’un tableau unidimensionnel qui comporte trois éléments, chacun d’eux étant un tableau unidimensionnel d’entiers :

 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]

 Pour pouvoir utiliser `jaggedArray`, vous devez initialiser ses éléments. Pour ce faire, procédez comme suit :

 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]

 Chacun des éléments est un tableau unidimensionnel d’entiers. Le premier élément est un tableau de 5 entiers, le deuxième est un tableau de 4 entiers et le troisième est un tableau de 2 entiers.

 Il est aussi possible d’utiliser des initialiseurs pour remplir les éléments de tableau de valeurs, auquel cas vous n’avez pas besoin de la taille du tableau. Par exemple :

 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]

 Vous pouvez aussi initialiser le tableau au moment de la déclaration, comme ceci :

 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]

 Vous pouvez utiliser la forme abrégée suivante. Notez que vous ne pouvez pas omettre l’opérateur `new` dans l’initialisation des éléments, car il n’existe pas d’initialisation par défaut pour les éléments :

 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]

 Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.

 Vous pouvez accéder aux éléments de tableau individuels comme dans ces exemples :

 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]

 Il est possible de combiner des tableaux en escalier et des tableaux multidimensionnels. Vous trouverez ci-dessous une déclaration et une initialisation d’un tableau en escalier unidimensionnel composé de trois éléments de tableau à deux dimensions de tailles différentes. Pour plus d’informations, consultez [tableaux multidimensionnels](./multidimensional-arrays.md).

 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]

 Vous pouvez accéder aux différents éléments comme le montre cet exemple, qui présente la valeur de l’élément `[1,0]` du premier tableau (valeur `5`) :

 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]

 La méthode `Length` retourne le nombre de tableaux contenus dans le tableau en escalier. Par exemple, en supposant que vous avez déclaré le tableau précédent, cette ligne :

 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]

 retourne la valeur 3.

## <a name="example"></a>Exemple

 Cet exemple génère un tableau dont les éléments sont eux-mêmes des tableaux. Chacun des éléments de tableau ont une taille différente.

 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Array>
- [Guide de programmation C#](../index.md)
- [Tableaux](./index.md)
- [Tableaux unidimensionnels](./single-dimensional-arrays.md)
- [Tableaux multidimensionnels](./multidimensional-arrays.md)

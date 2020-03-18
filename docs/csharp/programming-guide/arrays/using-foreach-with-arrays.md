---
title: Utiliser foreach avec des tableaux - Guide de programmation C#
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705676"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Utiliser foreach avec des tableaux (Guide de programmation C#)

L’instruction [foreach](../../language-reference/keywords/foreach-in.md) offre une méthode simple et appropriée pour itérer au sein des éléments d’un tableau.

Pour les tableaux unidimensionnels, l’instruction `foreach` traite les éléments dans l’ordre croissant des index, en commençant par l’index 0 et en terminant par l’index `Length - 1` :

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

Pour les tableaux multidimensionnels, les éléments sont traités de sorte que les index de la dimension la plus à droite sont incrémentés en premier, puis la dimension immédiatement à gauche, et ainsi de suite vers la gauche :

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

Cependant, dans le cas de tableaux multidimensionnels, l’utilisation d’une boucle [for](../../language-reference/keywords/for.md) imbriquée vous permet de mieux contrôler l’ordre dans lequel les éléments du tableau sont traités.

## <a name="see-also"></a>Voir aussi

- <xref:System.Array>
- [Guide de programmation C#](../index.md)
- [Tableaux](index.md)
- [Tableaux unidimensionnels](single-dimensional-arrays.md)
- [Tableaux multidimensionnels](multidimensional-arrays.md)
- [Arrays déchiquetés](jagged-arrays.md)

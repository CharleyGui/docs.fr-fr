---
title: Utiliser foreach avec des tableaux - Guide de programmation C#
description: L’instruction foreach en C# itère au sein des éléments d’un tableau. Pour les tableaux unidimensionnels, foreach traite les éléments dans l’ordre d’index de plus en plus important.
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: d924a3ef3351cbb30b809a1542f35314ee721852
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474538"
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
- [Guide de programmation C#](../index.md)
- [Tableaux](index.md)
- [Tableaux unidimensionnels](single-dimensional-arrays.md)
- [Tableaux multidimensionnels](multidimensional-arrays.md)
- [Tableaux en escalier](jagged-arrays.md)

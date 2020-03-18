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
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="e2dfd-102">Utiliser foreach avec des tableaux (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="e2dfd-103">L’instruction [foreach](../../language-reference/keywords/foreach-in.md) offre une méthode simple et appropriée pour itérer au sein des éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="e2dfd-104">Pour les tableaux unidimensionnels, l’instruction `foreach` traite les éléments dans l’ordre croissant des index, en commençant par l’index 0 et en terminant par l’index `Length - 1` :</span><span class="sxs-lookup"><span data-stu-id="e2dfd-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="e2dfd-105">Pour les tableaux multidimensionnels, les éléments sont traités de sorte que les index de la dimension la plus à droite sont incrémentés en premier, puis la dimension immédiatement à gauche, et ainsi de suite vers la gauche :</span><span class="sxs-lookup"><span data-stu-id="e2dfd-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="e2dfd-106">Cependant, dans le cas de tableaux multidimensionnels, l’utilisation d’une boucle [for](../../language-reference/keywords/for.md) imbriquée vous permet de mieux contrôler l’ordre dans lequel les éléments du tableau sont traités.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2dfd-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2dfd-107">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="e2dfd-108">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e2dfd-108">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e2dfd-109">Tableaux</span><span class="sxs-lookup"><span data-stu-id="e2dfd-109">Arrays</span></span>](index.md)
- [<span data-ttu-id="e2dfd-110">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="e2dfd-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="e2dfd-111">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="e2dfd-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="e2dfd-112">Arrays déchiquetés</span><span class="sxs-lookup"><span data-stu-id="e2dfd-112">Jagged Arrays</span></span>](jagged-arrays.md)

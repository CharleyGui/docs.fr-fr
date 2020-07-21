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
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="5fba5-104">Utiliser foreach avec des tableaux (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="5fba5-104">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5fba5-105">L’instruction [foreach](../../language-reference/keywords/foreach-in.md) offre une méthode simple et appropriée pour itérer au sein des éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="5fba5-105">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="5fba5-106">Pour les tableaux unidimensionnels, l’instruction `foreach` traite les éléments dans l’ordre croissant des index, en commençant par l’index 0 et en terminant par l’index `Length - 1` :</span><span class="sxs-lookup"><span data-stu-id="5fba5-106">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="5fba5-107">Pour les tableaux multidimensionnels, les éléments sont traités de sorte que les index de la dimension la plus à droite sont incrémentés en premier, puis la dimension immédiatement à gauche, et ainsi de suite vers la gauche :</span><span class="sxs-lookup"><span data-stu-id="5fba5-107">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="5fba5-108">Cependant, dans le cas de tableaux multidimensionnels, l’utilisation d’une boucle [for](../../language-reference/keywords/for.md) imbriquée vous permet de mieux contrôler l’ordre dans lequel les éléments du tableau sont traités.</span><span class="sxs-lookup"><span data-stu-id="5fba5-108">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fba5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fba5-109">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="5fba5-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5fba5-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5fba5-111">Tableaux</span><span class="sxs-lookup"><span data-stu-id="5fba5-111">Arrays</span></span>](index.md)
- [<span data-ttu-id="5fba5-112">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="5fba5-112">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="5fba5-113">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="5fba5-113">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="5fba5-114">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="5fba5-114">Jagged Arrays</span></span>](jagged-arrays.md)

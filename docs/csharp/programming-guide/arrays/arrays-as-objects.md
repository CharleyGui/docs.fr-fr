---
title: Tableaux en tant qu'objets - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 9905168662496c46d20f191c04f21d8630d02fa2
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772111"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="4b613-102">Tableaux en tant qu'objets (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="4b613-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="4b613-103">En C#, les tableaux sont en fait des objets, et pas simplement des zones adressables de mémoire contiguë comme en C et C++.</span><span class="sxs-lookup"><span data-stu-id="4b613-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="4b613-104"><xref:System.Array> est le type de base abstrait de tous les types de tableau.</span><span class="sxs-lookup"><span data-stu-id="4b613-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="4b613-105">Vous pouvez utiliser les propriétés et d’autres membres de classe que <xref:System.Array> possède.</span><span class="sxs-lookup"><span data-stu-id="4b613-105">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="4b613-106">Par exemple, l’utilisation de la propriété <xref:System.Array.Length%2A> pour récupérer la longueur d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4b613-106">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="4b613-107">Le code suivant affecte la longueur du tableau `numbers`, c’est-à-dire la valeur `5`, à une variable appelée `lengthOfNumbers` :</span><span class="sxs-lookup"><span data-stu-id="4b613-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="4b613-108">La classe <xref:System.Array> fournit beaucoup d’autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux.</span><span class="sxs-lookup"><span data-stu-id="4b613-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="4b613-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b613-109">Example</span></span>

<span data-ttu-id="4b613-110">L’exemple suivant utilise la propriété <xref:System.Array.Rank%2A> pour afficher le nombre de dimensions d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4b613-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="4b613-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b613-111">See also</span></span>

- [<span data-ttu-id="4b613-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4b613-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4b613-113">Tableaux</span><span class="sxs-lookup"><span data-stu-id="4b613-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="4b613-114">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="4b613-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="4b613-115">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="4b613-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="4b613-116">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="4b613-116">Jagged Arrays</span></span>](./jagged-arrays.md)

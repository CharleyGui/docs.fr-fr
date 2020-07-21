---
title: Tableaux en tant qu'objets - Guide de programmation C#
description: Les tableaux en C# sont des objets du tableau de types de base abstraits. Vous pouvez utiliser les propriétés et d’autres membres de classe de Array, tels que la propriété Length.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474720"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="361b8-104">Tableaux en tant qu'objets (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="361b8-104">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="361b8-105">En C#, les tableaux sont en fait des objets, et pas simplement des zones adressables de mémoire contiguë comme en C et C++.</span><span class="sxs-lookup"><span data-stu-id="361b8-105">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="361b8-106"><xref:System.Array> est le type de base abstrait de tous les types de tableau.</span><span class="sxs-lookup"><span data-stu-id="361b8-106"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="361b8-107">Vous pouvez utiliser les propriétés et d’autres membres de classe qui <xref:System.Array> possèdent.</span><span class="sxs-lookup"><span data-stu-id="361b8-107">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="361b8-108">Par exemple, l’utilisation de la <xref:System.Array.Length%2A> propriété pour récupérer la longueur d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="361b8-108">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="361b8-109">Le code suivant affecte la longueur du tableau `numbers`, c’est-à-dire la valeur `5`, à une variable appelée `lengthOfNumbers` :</span><span class="sxs-lookup"><span data-stu-id="361b8-109">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="361b8-110">La classe <xref:System.Array> fournit beaucoup d’autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux.</span><span class="sxs-lookup"><span data-stu-id="361b8-110">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="361b8-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="361b8-111">Example</span></span>

<span data-ttu-id="361b8-112">L’exemple suivant utilise la propriété <xref:System.Array.Rank%2A> pour afficher le nombre de dimensions d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="361b8-112">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="361b8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="361b8-113">See also</span></span>

- [<span data-ttu-id="361b8-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="361b8-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="361b8-115">Tableaux</span><span class="sxs-lookup"><span data-stu-id="361b8-115">Arrays</span></span>](./index.md)
- [<span data-ttu-id="361b8-116">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="361b8-116">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="361b8-117">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="361b8-117">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="361b8-118">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="361b8-118">Jagged Arrays</span></span>](./jagged-arrays.md)

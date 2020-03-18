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
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="07083-102">Passage de tableaux en tant qu’arguments (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="07083-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="07083-103">Les tableaux peuvent être passés en tant qu’arguments à des paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="07083-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="07083-104">Comme les tableaux sont des types référence, la méthode peut modifier la valeur des éléments.</span><span class="sxs-lookup"><span data-stu-id="07083-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="07083-105">Passage de tableaux unidimensionnels en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="07083-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="07083-106">Vous pouvez passer un tableau unidimensionnel initialisé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="07083-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="07083-107">Par exemple, l’instruction suivante envoie un tableau à une méthode Print.</span><span class="sxs-lookup"><span data-stu-id="07083-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="07083-108">Le code suivant illustre une implémentation partielle de la méthode Print.</span><span class="sxs-lookup"><span data-stu-id="07083-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="07083-109">Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="07083-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="07083-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="07083-110">Example</span></span>

<span data-ttu-id="07083-111">Dans l’exemple suivant, un tableau de chaînes est initialisé et passé en tant qu’argument à une méthode `DisplayArray` pour des chaînes.</span><span class="sxs-lookup"><span data-stu-id="07083-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="07083-112">La méthode affiche les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="07083-112">The method displays the elements of the array.</span></span> <span data-ttu-id="07083-113">Ensuite, la méthode `ChangeArray` inverse les éléments du tableau, puis la méthode `ChangeArrayElements` modifie les trois premiers éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="07083-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="07083-114">Une fois que chaque méthode est retournée, la méthode `DisplayArray` montre que le passage d’un tableau par valeur n’empêche pas les modifications des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="07083-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="07083-115">Passage de tableaux multidimensionnels en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="07083-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="07083-116">Vous pouvez passer un tableau multidimensionnel initialisé à une méthode de la même manière que vous passez un tableau unidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="07083-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="07083-117">Le code suivant illustre une déclaration partielle d’une méthode Print qui accepte un tableau à deux dimensions en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="07083-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="07083-118">Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="07083-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="07083-119"> Exemple</span><span class="sxs-lookup"><span data-stu-id="07083-119">Example</span></span>

<span data-ttu-id="07083-120">Dans l’exemple suivant, un tableau à deux dimensions d’entiers est initialisé et passé à la méthode `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="07083-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="07083-121">La méthode affiche les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="07083-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="07083-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07083-122">See also</span></span>

- [<span data-ttu-id="07083-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="07083-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="07083-124">Tableaux</span><span class="sxs-lookup"><span data-stu-id="07083-124">Arrays</span></span>](index.md)
- [<span data-ttu-id="07083-125">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="07083-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="07083-126">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="07083-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="07083-127">Arrays déchiquetés</span><span class="sxs-lookup"><span data-stu-id="07083-127">Jagged Arrays</span></span>](jagged-arrays.md)
